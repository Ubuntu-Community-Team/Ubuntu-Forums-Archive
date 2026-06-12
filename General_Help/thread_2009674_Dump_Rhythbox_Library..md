---
title: "Dump Rhythbox Library."
date: 2012-06-24
forum: General Help
---

### Post by uRock on 2012-06-24
I made the mistake of adding a network drive to Rhythmbox's library and now I have doubles of every song listed in Rhythmbox(at least this is the case with every song which is in my Home/Music and the network drive). What is the easiest way to dump the library and start over?

Edit: I tried removing via synaptic and using the complete removal selection, then I ran Bleachbit as user and root. The library was still there after installing again.

---

### Post by sgage on 2012-06-24
> **uRock said:**
> I made the mistake of adding a network drive to Rhythmbox's library and now I have doubles of every song listed in Rhythmbox(at least this is the case with every song which is in my Home/Music and the network drive). What is the easiest way to dump the library and start over?

Just select everything in the Music browser, and right-click/remove. Then you will start fresh.

Or you can go to ~/.local/share/rhythmbox and delete rhythmdb.xml.

---

### Post by uRock on 2012-06-24
Thanks. When I tried removing them via the right-click method, they were all imported from both locations again when I went to import from the primary location I wanted. 

I then tried deleting the xml and that worked like a charm. All of the songs from the network drive loaded whil the files in the Music folder were ignored.:guitar:

---

