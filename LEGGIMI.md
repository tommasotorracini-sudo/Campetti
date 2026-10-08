# Campetti: prototipo PWA della tesi

Web app che si apre dal telefono e si può aggiungere alla schermata Home (Progressive Web App).
"Campetti" è un nome provvisorio: si cambia in `js/config.js` e in `manifest.webmanifest`.

## Cosa è vero e cosa è simulato

| Funzione | Stato |
|---|---|
| Mappa | vera (OpenStreetMap) |
| Campi da basket e loro caratteristiche (pavimentazione, luci, canestri, accesso) | **veri**, letti da OpenStreetMap tramite Overpass |
| La tua posizione | vera, solo se la autorizzi; non viene inviata a nessuno |
| Presenze ("giocano ora", "stanno arrivando") | **simulate** |
| Partite spontanee (*raid*): creazione, iscrizione, soglia, scadenza | **simulate** nel telefono |
| Chat del campo | **simulata**; i messaggi restano sul telefono |
| Profilo (nickname, posizione, storico) | salvato solo sul telefono, senza livello né valutazioni |
| Allenamento (tiri liberi su 10) | salvato solo sul telefono |

Nella tesi va scritto così: il prototipo usa dati reali per i campi e dati simulati per le funzioni sociali.

## Struttura

```
index.html            struttura delle schermate
css/style.css         stile neutro da prototipo (colori e caratteri in cima al file, nelle variabili :root)
js/config.js          zona iniziale della mappa, nome, durata delle segnalazioni
js/app.js             logica dell'app
manifest.webmanifest  nome, icone e colori dell'app installata
sw.js                 service worker (fa aprire l'app anche con rete debole)
icons/                icone provvisorie, da sostituire con quelle del marchio
```

## Pubblicarla gratis su GitHub Pages

1. Crea un account su github.com.
2. Crea un nuovo repository pubblico, per esempio `campetti`.
3. Nel repository: **Add file → Upload files**, trascina tutto il contenuto della cartella (non la cartella stessa) e conferma con **Commit changes**.
4. Vai su **Settings → Pages**. In "Branch" scegli `main` e la cartella `/ (root)`, poi **Save**.
5. Dopo un paio di minuti l'app è online all'indirizzo `https://TUONOME.github.io/campetti/`.
6. Dal telefono apri l'indirizzo e scegli **Aggiungi a schermata Home** (iPhone: tasto Condividi in Safari; Android: menu di Chrome).

Ogni volta che carichi file nuovi, il sito si aggiorna da solo in un paio di minuti.

## Cambiare zona

In `js/config.js` modifica `center` con le coordinate della tua zona (le trovi su openstreetmap.org: tasto destro sul punto → "Mostra indirizzo"). Sulla mappa puoi comunque spostarti e premere "Cerca campi in quest'area".

## Cose da sapere

- **Dati OpenStreetMap.** Sono inseriti da volontari: alcuni campi mancano o hanno informazioni incomplete ("non indicato"). Il pulsante "Segnala una modifica" porta all'editor di OpenStreetMap. Nella tesi la fonte va citata come "© contributori di OpenStreetMap" (licenza ODbL).
- **Overpass** è un servizio gratuito con limiti d'uso: va bene per la tesi e per i test con poche persone, non per un'app con molti utenti.
- **La posizione** funziona solo su indirizzi https, quindi sì su GitHub Pages, no aprendo il file dal computer.
- Il pulsante "Azzera i dati della demo" nel profilo cancella partite, chat e sessioni salvate: utile prima di ogni test con un nuovo utente.

## Prossimi passi

1. Definire il design in Figma (wireframe → interfaccia).
2. Riportare colori, caratteri e icone del marchio in `css/style.css` e in `icons/`.
3. Usare il link o un QR code per il test con 5-8 persone (par. 6.9).
