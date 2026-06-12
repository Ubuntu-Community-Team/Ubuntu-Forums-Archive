---
title: "Extracting archives"
date: 2010-09-25
forum: General Help
---

### Post by OllieGab on 2010-09-25
So I've got this film, a collection of about 90 different rar-files. One called xxx.rar, all the others .r00....r89.
I've managed to extract before and get a "finsihed" product but seem completely stuck now.
Tried Archive Manager, and though it doesn't exactly gives me any error messages, I don't end up with a single file/film.
I can extract **one** rar file on its own and get a **one** xxx.img file.
When I've done this before (luck?) I've ended up with a single .avi-file.

Any suggestions?

---

### Post by Merthod on 2010-09-25
In your software manager or Synaptic Package Manager try to install either 7zip or RAR. Many of these problems come because we don't have the right handlers installed. I have 7zip (which can also handle RAR files) and now I can open through Archive Manager all kinds of archive files, including yours.

Hope this helps.

---

### Post by OllieGab on 2010-09-25
I have 7zip installed but I beleive it's not a graphical tool?
If I use the command line (with 7zip), what would be the 'command'?

---

### Post by OllieGab on 2010-09-26
It looks like I've managed to sort this out myself...perhaps it can be of help to someone else at some point!
After trying various things out, converting, using different archive programmes etc, I noticed that when using Archive Manager it said [read only] on the top border.
So I made myself root at the command line, typed 'nautilus', went to the relevant folder and just right-clicked on the first rar-file (r00). Clicked Extract, and hey presto...there it was! The avi file!
This hasn't happened to me before but somehow it obviously didn't like that I was just my normal me, ie the 'normal' user.

---

### Post by tagnu on 2010-09-27
Thank you. Got it working by installing **rar**.

```
sudo apt-get install rar
```

> **Merthod said:**
> In your software manager or Synaptic Package Manager try to install either 7zip or RAR. Many of these problems come because we don't have the right handlers installed. I have 7zip (which can also handle RAR files) and now I can open through Archive Manager all kinds of archive files, including yours.

Hope this helps.

---

### Post by Larsko on 2010-09-27
Hi all,

Just tried to open a 7zip archive.

After a apt-cache search 7zip into the sullution.
Just install p7zip-full and you can extract the archive.

Cheers!

Lars

---

