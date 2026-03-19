# ML--Grupp-6
Marketplace Safety – prioritera misstänkta annonser och meddelanden

### Tabeller (exporterade)
- `data\historical_data.csv`
- `data\Kravkort7.pdf` (Kravkort)
- `data\new_data.csv`

## Roller, Ansvar & Deltagare:

- Data & EDA - Katja Marjaana Christine Drugg
- Pipeline & preprocessing - Wendy Mermet
- Modelljämförelse - Elza Capar
- Optimering - Kevin Christofer Johansson
- Threshold/prioritering - Dariel Riera Carrillo
- Pitch & risker - Tim Elias Alexander Rydén


## Vår strategi

* Målet är en modell som generaliserar väl till ny data, därför används **ROC-AUC** som robust utvärderingsmått.
* Modeller utvärderas med **5-fold cross-validation** för att säkerställa stabil prestanda.
* **Logistic Regression** valdes som slutmodell då den gav högst genomsnittlig ROC-AUC.
* En enklare modell prioriteras eftersom den ofta är mer stabil över tid när beteenden förändras.
* **GridSearchCV** användes för hyperparameteroptimering med ROC-AUC som mål.
* Bästa parametrar: *C = 0.1, l1_ratio = 1, solver = saga* (ROC-AUC ≈ 0.741), marginellt bättre än alternativ.
* Förbättringen från tuning var liten → modellen var redan nära sitt prestandatak.
* Istället för threshold används **Top-X prioritering** för att rangordna misstänkta transaktioner.
* **Top-50** valdes som en stabil och realistisk daglig arbetsmängd för analytikern.
* Resultat: 42% träffsäkerhet (21/50), vilket är ca 4× bättre än slumpen och ger stabil arbetsbelastning.


## Miljö
- **Python:** 3.11.9
- **Paket:** `Pandas`, `matplotlib`, `numpy`, `seaborn`, `sklearn` (se `requirements.txt`)

## Kom igång och installera

```bash
# klona projetet
git clone https://github.com/wendymermet-lgtm/ML--Grupp-6.git

# Skapa och aktivera virtuell miljö
python -m venv .venv
# Windows PowerShell
.venv\Scripts\Activate
# macOS/Linux
# source .venv/bin/activate

# installera beroenden
python -m pip install -r requirements.txt

