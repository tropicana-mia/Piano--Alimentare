# Piano Alimentare

App web personale per gestire il piano alimentare settimanale: pasti, sostituzioni consentite per categoria (carne, pesce, formaggio, uova, tofu) con conteggio rispetto all'obiettivo settimanale, verdure abbinate, e lista della spesa generata automaticamente.

Basato sullo schema nutrizionale di Laura Santelia, adattato alle preferenze personali.

## Come funziona

- **Un solo file HTML** — nessuna build, nessuna dipendenza da installare. Basta aprirlo in un browser.
- I dati (piano modificato e lista spesa spuntata) si salvano automaticamente nel browser tramite `localStorage`. Restano privati e locali: nessun server coinvolto.
- Il pulsante ↺ in alto ripristina il piano ai valori di partenza.

## Sviluppo locale

Non serve nulla di speciale — apri `index.html` con doppio click, oppure con un piccolo server locale se preferisci:

```bash
python3 -m http.server 8000
# poi apri http://localhost:8000
```

## Deploy su GitHub Pages

1. Crea un nuovo repository su GitHub (es. `piano-alimentare`), pubblico o privato.
2. Nella cartella del progetto:
   ```bash
   git init
   git add .
   git commit -m "Prima versione del piano alimentare"
   git branch -M main
   git remote add origin https://github.com/<tuo-utente>/piano-alimentare.git
   git push -u origin main
   ```
3. Su GitHub: **Settings → Pages → Source** → scegli il branch `main` e la cartella `/ (root)`.
4. Dopo un minuto, l'app sarà online su:
   ```
   https://<tuo-utente>.github.io/piano-alimentare/
   ```

Se il repository è **privato**, GitHub Pages richiede un piano Pro (o l'uso di GitHub Pages con visibilità limitata via altri strumenti); se ti va bene un repository pubblico, funziona anche col piano gratuito.

## Personalizzare i dati

Tutti i dati del piano vivono in cima al file `index.html`, dentro il tag `<script>`:

- `CATS` — le categorie proteiche, le opzioni consentite per ciascuna, e l'obiettivo settimanale (es. carne 4 volte).
- `VEG_OPTIONS` — l'elenco delle verdure/abbinamenti disponibili nel menu a tendina.
- `plan` — il piano dei 7 giorni (colazione, merenda, pranzo, cena) usato come valore di partenza.
- `SHOP_CATALOG` / `VEG_CATALOG` — dizionari che mappano ogni proteina/verdura alla categoria del negozio (Pescheria, Macelleria, Latticini, Ortofrutta, Dispensa) e alla quantità standard, usati per generare la lista della spesa.

Per aggiungere un nuovo alimento, cercalo in questi oggetti e aggiungi una voce nello stesso formato.

## Prossimi passi possibili

- Salvataggio su più dispositivi (richiederebbe un piccolo backend o un servizio come Firebase/Supabase, dato che ora i dati sono solo nel browser locale)
- Storico dei pasti per evitare ripetizioni troppo ravvicinate nel tempo
- Editor visuale per aggiungere nuovi alimenti senza toccare il codice
- Esportazione della lista spesa come testo da condividere (es. su WhatsApp)

## Licenza

Uso personale.
