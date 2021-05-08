flashcards
==========

A UNIX style, plaintext flashcard system.

Files
-----

Deck files store the actual flashcards. Cards are identified by an id.
There are different types of cards:

- **Question / Answer Cards** have a question and an answer.
  You see the question first and "flip" the card to reveal the answer.
  
  ```
  <id>:
    qstn: <question>
    answ: <answer>
  ```
- **Cloze Cards** contain text where some parts are initially blanked out.
  When reviewing you can incrementally uncover the gaps.
  ```
  <id>:
    cloze:
      Some text with {{1:blanks}}.
      Blanks are marked with {{2:double curly braces}}.
      The first first two letters inside the {{2:curly braces}} specify {{3:the increment}}.
      The text after the colon is the {{4:content}}.
      This example would be uncovered in {{5:five}} steps.
  ```

Session files store a reviewal session, referencing the cards from a deck

```
<id>:
  last: <unix time of last review>
  dlay: <review delay in seconds>
```

These are seperated, so decks can be easily shared and reused.

Programs
--------

``` sh
flash <deckfile>
```
