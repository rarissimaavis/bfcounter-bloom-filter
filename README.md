# 🌷 Analisi di BFCounter per il conteggio efficiente dei k-mer nel DNA tramite Bloom Filter
> Progetto realizzato da [rarissimaavis](https://github.com/rarissimaavis) per il corso di Strumenti Formali per la Bioinformatica 2024/25 sull'analisi del tool BFCounter, basato su Bloom Filter per il conteggio efficiente dei k-mer nelle sequenze di DNA! 🧬

# Abstract
Le tecnologie di sequenziamento di nuova generazione hanno rivoluzionato la genomica, generando dataset di grandi dimensioni che richiedono strumenti efficienti per la loro analisi, rendendo essenziale lo sviluppo di strumenti computazionali efficienti per la loro analisi.

Il conteggio dei k-mer, sottosequenze di lunghezza fissa, rappresenta un passaggio fondamentale in applicazioni come l'assemblaggio genomico, la metagenomica e l'identificazione di varianti genetiche. Tuttavia, il trattamento di dataset genomici su larga scala richiede soluzioni efficienti in termini di memoria e velocità di elaborazione.

Questo lavoro si concentra sull'uso dei Bloom Filter, strutture dati probabilistiche, come strumento per rappresentare in modo compatto i k-mer e ridurre significativamente il consumo di risorse computazionali. In particolare, viene analizzato BFCounter, un tool che integra i Bloom Filter per eliminare i k-mer unici e migliorare l'efficienza del conteggio, e viene effettuato un confronto con Jellyfish, una soluzione tradizionale basata su tabelle hash.

L'analisi comparativa, supportata da test sperimentali, evidenzia che BFCounter utilizza significativamente meno memoria, nonostante la tolleranza a una bassa percentuale di falsi positivi intrinseca ai Bloom Filter. Jellyfish, al contrario, si distingue per una maggiore velocità di calcolo e risultati deterministici, richiedendo però un dispendio più elevato di risorse computazionali.

Questo studio dimostra come i Bloom Filter possano rappresentare una soluzione efficace per migliorare l'efficienza delle analisi genomiche, offrendo spunti per future ottimizzazioni.

# ✨ Introduzione
Questa repository documenta l'analisi e il confronto di due strumenti per il conteggio dei k-mer:

- [BFCounter](https://github.com/pmelsted/BFCounter): un software che utilizza i Bloom Filter per ridurre il consumo di memoria;
- [Jellyfish](https://github.com/gmarcais/Jellyfish/tree/master): una soluzione basata su tabelle hash dinamiche, ottimizzata per velocità e parallelismo.

# 🔧 Setup

## Requisiti
🐧 Ambiente Linux per garantire la compatibilità degli strumenti;
💻 Ambiente C++ con compilatore GCC o equivalente;
🛠️ CMake per la configurazione del progetto.

## Installazione dei tool
Clonare e compilare le repository ufficiali.

BFCounter:
```bash
git clone https://github.com/pmelsted/BFCounter.git
cd BFCounter
make
```

Jellyfish:
```bash
git clone https://github.com/gmarcais/Jellyfish.git
cd Jellyfish
autoreconf -i
./configure
make
```

# 🚀 Guida all'uso

## BFCounter

Esempio di comando per il conteggio dei k-mer:
```bash
./BFCounter count -k 31 -n 1000 -o output.bf test.fasta
```

Per esportare i k-mer in un file di testo:
```bash
./BFCounter dump -k 31 -i output.bf -o kmers.txt
cat kmers.txt
```

## Jellyfish

Esempio di comando per il conteggio dei k-mer e la stampa delle statistiche:
```bash
/usr/bin/time -v jellyfish count -m 31 -s 100M -t 10 test.fasta -o output.jf
```

Per esportare i k-mer in un file di testo con frequenza associata:
```bash
./BFCounter dump -k 31 -i output.bf -o kmers.txt
cat kmers.txt
```

# 📊 Risultati Sperimentali

## BFCounter

- 🧠 Riduzione della memoria: Minor uso di memoria grazie ai Bloom Filter;
- 🔍 Precisione: Tolleranza a una bassa percentuale di falsi positivi.

## Jellyfish

- ⚡ Velocità di calcolo: Tempi di esecuzione più rapidi grazie all'uso di tabelle hash ottimizzate;
- 🎯 Accuratezza: Risultati deterministici senza falsi positivi.
