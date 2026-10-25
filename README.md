# Opacte — têtes publiées / published heads

*Signé, prouvé, jamais lu — Signed, proven, never read* · <https://opacte.eu>

## Français

Ce dépôt reçoit chaque jour, à 06:00 UTC, un commit qui publie les **têtes** des trois chaînes publiques d'Opacte :

| Tête | Ce qu'elle désigne | Où la recouper |
|---|---|---|
| `trousseau` | H_fc du corps `said:trousseau-chaine` de la dernière version du trousseau des clés | <https://opacte.eu/.well-known/said-keys.json> |
| `journal` | H_fc de la dernière entrée `said:journal` du journal public (`hash_tete`) | <https://opacte.eu/log/head>, <https://opacte.eu/log> |
| `registre` | H_fc du corps `said:registre` de la dernière version du registre des algorithmes | <https://opacte.eu/.well-known/said-registry.json> |

`tetes.json` contient la dernière publication ; `AAAA/AAAA-MM-JJ.json`, celle de chaque jour. Les valeurs sont en
base64url (SHA3-512 de la forme canonique fc-v1).

**Pourquoi.** Opacte publie lui-même son trousseau, son journal et son registre. Ce dépôt, hébergé par un tiers, sert
à vérifier qu'Opacte montre **les mêmes chaînes à tout le monde** : une version réécrite, ou deux versions
différentes servies à deux personnes, deviendraient visibles en comparant ce que le site renvoie avec ce qui a été
publié ici. L'historique Git est lui-même une chaîne en ajout seul : **forkez ce dépôt** pour en garder une copie
indépendante ; une réécriture de l'historique serait alors constatable.

**Recouper.** `GET https://opacte.eu/log/head` renvoie la tête courante du journal et, dans `tetes_publiees`, la
dernière publication faite ici : elle doit être identique au contenu de `tetes.json`. Une tête publiée doit toujours
se retrouver plus tard dans la chaîne servie par le site (le journal ne fait que s'allonger).

## English

Every day at 06:00 UTC this repository receives one commit publishing the **heads** of Opacte's three public chains:

| Head | What it identifies | Where to cross-check it |
|---|---|---|
| `trousseau` | H_fc of the `said:trousseau-chaine` body of the latest version of the key set | <https://opacte.eu/.well-known/said-keys.json> |
| `journal` | H_fc of the latest `said:journal` entry of the public log (`hash_tete`) | <https://opacte.eu/log/head>, <https://opacte.eu/log> |
| `registre` | H_fc of the `said:registre` body of the latest version of the algorithm registry | <https://opacte.eu/.well-known/said-registry.json> |

`tetes.json` holds the latest publication; `YYYY/YYYY-MM-DD.json`, one per day. Values are base64url (SHA3-512 of the
fc-v1 canonical form).

**Why.** Opacte publishes its key set, log and registry itself. This repository, hosted by a third party, lets anyone
check that Opacte shows **the same chains to everyone**: a rewritten version, or two different versions served to
two people, would become visible by comparing what the site returns with what was published here. The Git history is
itself an append-only chain: **fork this repository** to keep an independent copy; a rewrite of the history would
then be detectable.

**Cross-check.** `GET https://opacte.eu/log/head` returns the current log head and, in `tetes_publiees`, the latest
publication made here: it must match the content of `tetes.json`. A published head must always be found later in the
chain served by the site (the log only grows).
