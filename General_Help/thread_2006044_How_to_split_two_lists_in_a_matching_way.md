---
title: "How to split two lists in a matching way?"
date: 2012-06-18
forum: General Help
---

### Post by pqn on 2012-06-18
There are two files, containing sentences of varied length, in different languages. Since they are translations of each other, the number of lines matches in the files. I want to split the two files in question in a random way (with a sentence getting with, for example, 90% chance to one output file, 10% to the other), but in such a way that the new, split files still have matched lines.

Visual representation (A1 etc. symbolises the respective lines in the original file):

```

[FONT=Courier New]A1A2A3A4A5          B1B2B3B4B5
    I                   I
    v                   v
A1A2A4              B1B2B4
A3A5                B3B5[/FONT]

```The files in question may contain more than hundred thousand lines each, and may or may not use Unicode horrorific characters.

How do I .sh or .pl this?

---

