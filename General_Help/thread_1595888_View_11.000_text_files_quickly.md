---
title: "View 11.000 text files quickly?"
date: 2010-10-13
forum: General Help
---

### Post by BarbozaG on 2010-10-13
Hi; I'm in a bit of a mess, I need to view 10.858 text files by this friday to see which ones I need (searching file contents is not a solution), I was wondering if anyone knew any way/program to quickly view them as if they were, for example, images? And, optionally, to be able to save them to a different location from there? It doesn't necessarily have to be for Ubuntu as I also have WinXP and Vista, but it would save me having to transfer those couple of gigabytes to another computer. :)

---

### Post by Barriehie on 2010-10-13
Are they all in the same directory?

Edit: My idea hinges on your ability to use vim, or any other editor that supports macros.

---

### Post by BarbozaG on 2010-10-13
not really, they're in about 100 or so subdirectories within a larger directory :P

Edit:  but, no, sorry, there's another folder with them all in one :)

---

### Post by Barriehie on 2010-10-13
Since you can't grep...
```
vim *parent_folder*/*
```

On my machine I can have up to 279,913 file descriptors so then it would be a memory thing...

---

