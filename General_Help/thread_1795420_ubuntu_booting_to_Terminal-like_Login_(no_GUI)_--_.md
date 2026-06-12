---
title: "ubuntu booting to Terminal-like Login (no GUI) -- Help with recovery mode"
date: 2011-07-02
forum: General Help
---

### Post by ester4 on 2011-07-02
Could someone explain how I might try using Recovery Mode to fix whatever is wrong?

When i'm booting, I no longer get the gui login prompt. Instead I get a Terminal-like login prompt. I can login and everything but I'm a noob and don't know what to do.

I booted to recovery mode and selected fix broken packages but this didn't fix the problem. is there anything else I can try?

---

### Post by wolfen69 on 2011-07-02
Once you login, do **startx** and tell us what happens.

---

### Post by ester4 on 2011-07-02
> **wolfen69 said:**
> Once you login, do **startx** and tell us what happens.

I already tried this before I posted here on forums. All that happened was that the characters turned all funny looking. It still said Login etc but they were like in block letters. Bottom line, it did nothing.

---

### Post by nrundy on 2011-07-02
ester

try this at the prompt: sudo apt-get install ubuntu-desktop

---

### Post by LastHylian on 2011-07-02
What kind of of video card do you have? 
     You can find out by typing "lspci | grep VGA" without the ""

Is this a fresh install, or was the GUI previously working?

Depending on which video card you have, your drivers might be missing. For me personally, whenever there is a kernel update, I have to re-install my NVIDIA drivers again.

---

### Post by ester4 on 2011-07-02
hey, thanks a lot for your help guys :)

installing the ubuntu-desktop thing worked.

---

