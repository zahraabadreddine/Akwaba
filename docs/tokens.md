# Tokens d'Akwaba

Un token est le plus petit « mot » du langage reconnu par le lexer.

## Familles

| Famille | Contenu | Token produit |
|---|---|---|
| Mots-clés (11) | entier booleen si sinon tantque afficher vrai faux et ou non | le mot-clé lui-même |
| Identificateurs | une lettre, puis des lettres, des chiffres ou des tirets bas (la casse compte) | IDENT |
| Nombres | entiers positifs écrits en chiffres : 0, 42, 2026 | NOMBRE |
| Opérateurs | + - * / % = == != < <= > >= | l'opérateur lui-même |
| Ponctuation | ( ) { } ; | le symbole lui-même |

Règles importantes :

- Un mot-clé n'est jamais un identificateur : `si` ne peut pas être un nom de variable.
- La casse compte : `Entier` est un identificateur, `entier` est un mot-clé.
- Le lexer lit le plus long token possible : `<=` donne un seul token, pas `<` puis `=`.
- Tout caractère qui n'appartient à aucune famille (par exemple `#` ou `@`) est une erreur lexicale.

## Exercice 2.1 — Découpage d'une ligne

`tantque (i <= 10) { somme = somme + i; }` contient 14 tokens.

| N° | Token | Famille |
|---|---|---|
| 1 | tantque | Mot-clé |
| 2 | ( | Ponctuation |
| 3 | i | Identificateur |
| 4 | <= | Opérateur |
| 5 | 10 | Nombre |
| 6 | ) | Ponctuation |
| 7 | { | Ponctuation |
| 8 | somme | Identificateur |
| 9 | = | Opérateur |
| 10 | somme | Identificateur |
| 11 | + | Opérateur |
| 12 | i | Identificateur |
| 13 | ; | Ponctuation |
| 14 | } | Ponctuation |

## Exercice 2.2 — Mot-clé, identificateur, nombre ou erreur

| Mot | Catégorie | Justification |
|---|---|---|
| Entier | Identificateur | La casse compte, ce n'est donc pas le mot-clé « entier ». |
| note suivi d'un tiret bas et de 1 | Identificateur | Il commence par une lettre, suivie de lettres, chiffres ou tirets bas. |
| tantque | Mot-clé | Il fait partie des 11 mots-clés. |
| 2026 | Nombre | Entier positif écrit en chiffres. |
| total précédé d'un tiret bas | Erreur lexicale | Un identificateur doit commencer par une lettre. |
| 2x | Erreur lexicale | Ni un nombre (contient une lettre) ni un identificateur (commence par un chiffre). |
| afficher | Mot-clé | Il fait partie des 11 mots-clés. |
| vrai | Mot-clé | Valeur booléenne, fait partie des 11 mots-clés. |
