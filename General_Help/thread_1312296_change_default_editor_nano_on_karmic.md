---
title: "change default editor nano on karmic"
date: 2009-11-03
forum: General Help
---

### Post by joenieburg on 2009-11-03
When I want to change my default editor on Ubuntu 9.10 (karmic)
So in a command line I do

sudo update-alternatives –config editor

```

There are 3 choices for the alternative editor (providing /usr/bin/editor).

  Selection    Pad                Prioriteit Status
------------------------------------------------------------
  0            /bin/nano           40        auto mode
* 1            /bin/ed            -100       manual mode
  2            /bin/nano           40        manual mode
  3            /usr/bin/vim.tiny   10        manual mode

Druk op enter om de huidige keuze[*] te behouden, of typ het keuzenummer: 

```

There I selected ed (hai ed) But ed is in manual mode and everytime a have to select ed again.

Is it possible to get ed started in auto mode? Just like nano?

---

