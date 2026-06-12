---
title: "WINE and Win program slowdowns"
date: 2006-06-16
forum: General Help
---

### Post by Trance Gemini on 2006-06-16
hi!

Yesterday I installed WINE (acc. to ubuntu wiki guide) and tried to launch a programm, that I use under window to read books (programm called **Govorilka**). But I come to that ir runs veeery slow! This is a very simple programm, that looks like a wordpad, and it runs sooo slow, expecially it "think a lot" when i try to resize the window! Under win it runs as fast as light.
So why is that? I read that win programms emulates rather fast, and they runs almost as fast as they rund under win! Could it be some wine settings I shoud enable/disable?

P.S. i use F-Siemens laptop, 256 ram, centrino 1,7, ATI mobile video, ubuntu, gnome

By the way, maybe you can recomend some book-reading programs, so I don't need to run it via WINE? like [ICE Book Reader]("http://www.ice-graphics.com/ICEReader/ScreenR.html") under win would be super :) (also i tried to run ice book reader via wine - it's stops to respond after it's splash screen)

---

### Post by eqisow on 2006-06-16
> P.S. i use F-Siemens laptop, **256 ram**, centrino 1,7, ATI mobile video, ubuntu, gnome

That 256 MB of RAM is definitely the culprit. Wine has to load the entire Windows API, and therefore takes a bit of memory. GNOME already takes quite a bit, plus whatever else you're running, so Wine just doesn't have what it needs. That said, when Wine has enough RAM available, it does run pretty speedy.

Your two solutions are going to be either installing a lightweight window manager, such as XFCE or Fluxbox, or getting another 256 MB of RAM.

Edit: As far a Linux ebook readers, I know of Kniga and PyBook off-hand. It would help to know what kind of ebook formats you needs to read.

---

### Post by Trance Gemini on 2006-06-16
[QUOTE=eqisow]As far a Linux ebook readers, I know of Kniga and PyBook off-hand. It would help to know what kind of ebook formats you needs to read.[/QUOTE]

Basically it doesn't matter, because everything can be converted to .txt :) but anyway, they usualy come as .doc or .txt

---

