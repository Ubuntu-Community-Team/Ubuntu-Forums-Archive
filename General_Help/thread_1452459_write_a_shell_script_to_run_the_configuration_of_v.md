---
title: "write a shell script to run the configuration of vim editor?"
date: 2010-04-12
forum: General Help
---

### Post by ZaraCastle on 2010-04-12
Hi All
I have a question, tried to search on the Internet but it is hopeless. I want to write a shell script(bashShell) that will run commands of configuration for vim editor. For example: in the script, it will run ":let", ":set", ":highlight" to configure for vim editor. In addition to, when I searched a pattern and wrote it to file, I called vi to open it automatically. But, I couldn't highlight a word(that is the pattern I'm searching) in vim automatically. Anybody can help me solve this problem. Any help will be appreciated cordially. Thanks very much...

---

### Post by hawthornso23 on 2010-04-12
I believe you can do this via your .vimrc file.

---

### Post by ZaraCastle on 2010-04-12
> **hawthornso23 said:**
> I believe you can do this via your .vimrc file.

Hi hawthornso23,

The main purpose that I want is after searching a pattern and writing to a file, I need to highlight the pattern in this file when open it by vim editor. I want to do it automatically by writing a script with any patterns when I use "grep pattern > filename" more than do it manually by editing in .vimrc. Would you get my point? Thanks

---

### Post by ZaraCastle on 2010-04-12
> **ZaraCastle said:**
> Hi hawthornso23,

The main purpose that I want is after searching a pattern and writing to a file, I need to highlight the pattern in this file when open it by vim editor. I want to do it automatically by writing a script with any patterns when I use "grep pattern > filename" more than do it manually by editing in .vimrc. Would you get my point? Thanks

Pump

---

