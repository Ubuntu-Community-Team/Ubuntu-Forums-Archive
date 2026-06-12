---
title: "Crashes with evince and firefox"
date: 2006-02-17
forum: General Help
---

### Post by deavik on 2006-02-17
Hi,

Ubuntu is running great, but I have very frequent crashes with two applications that I use regularly. Evince (after loading moderately large pdfs) freezes the whole system (numlock doesn't work, mouse pointer doesn't move, etc) and I have to power off. This happens when I, say, scroll to a new page; almost everytime I use evince.

Firefox also freezes the system like evince sometimes, other times (very frequently) just quits to desktop.

Is there anything I can do to help this? Thanks,

My system: PIII 1 GHz, 256mb RAM, nVidia Geforce 4 MX 440 64mb assembled desktop

---

### Post by nanotube on 2006-02-17
hmm, that sounds a bit strange.. evince has never crashed on me like that (although it has failed to display certain pdfs)... you could try installing xpdf or gpdf, both of these are nice alternatives to evince.

as to firefox, i suppose you could try upgrading to the newest version, but somehow i suspect that it is probably one of the extensions you have installed. when firefox crashes, it is usually the fault of the extensions...

---

### Post by deavik on 2006-02-17
Hi nanotube, thanks for the reply.

I had upgraded firefox to 1.5 using the wiki page. At that time it used to crash even more frequently, so I removed that and moved back to firefox 1.0. I don't have any extensions installed at all!

I've tried xpdf, but evince (when it works) seems much better (for me). I'll look at gpdf, but right now both synaptic and apt-get from terminal are segfaulting when I run them. Keep in mind that the pdf I usually view (opengl spec) is ~400 pages, is this a problem with it running out of memory?

---

### Post by erice on 2006-02-17
You might try to use kpdf. It's a KDE program but works perfec in gnome. It's by far, the best pdf's reader I know in the linux world.

Anyway, i also never had any problems with evince. But this program doesn't have a function I like; the hability to reprint pdf with two pages by sheet of paper; that's really necessary to  save ink and paper :-).

---

### Post by deavik on 2006-02-17
erice, thanks for the advice. Before reading your post I just downloaded gpdf, and so far it's working very good. Plus it has some features better than evince (or possibly I didn't notice them in evince) like going back and forward in history. If this doesn't work for me, I'll try kpdf.

Thanks! :)

/edit: gpdf doesn't seem to have a find function. But that's still OK as the glspec has a good index at the back

---

