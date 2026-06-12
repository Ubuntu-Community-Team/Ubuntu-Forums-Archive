---
title: "Format CDs with Nautilus GUI"
date: 2009-07-29
forum: General Help
---

### Post by DGeeez on 2009-07-29
I believe I should be able to do this somehow, to add mkfs or something like it to the right-click menu in Nautilus. When you're recycling rewritable CD/DVDs, and your CD software doesn't know how to do an over-write (aka brilliant Brasero), it could save a royal pain in the @ss! Can anyone do this?

---

### Post by philinux on 2009-07-29
Think this is a wishlist item in Karmic.
[http://ubuntuforums.org/showthread.php?t=1223139](http://ubuntuforums.org/showthread.php?t=1223139)

Install either K3b or gnomebaker. I prefer k3b myself.

---

### Post by coffeecat on 2009-07-29
> **DGeeez said:**
> When you're recycling rewritable CD/DVDs, and your CD software doesn't know how to do an over-write (aka brilliant Brasero)

I don't know about your Brasero, but my Brasero copes just fine. I often use it to write to a used DVD-RW or CD-RW. Brasero detects this, asks whether I want to erase it, and then goes on to a successful burn.

Or you can Tools > Erase in the main Brasero window.

---

### Post by DGeeez on 2009-07-29
Linux engineers should not decide whether I should have this convenience (it sure ISN'T Windows), and the difference is essential when you are recycling much rewriteable media. If it's not installed default, then I should be able to add it to the Nautilus right-click menu - anyone know how this can be done?

Thanks.

---

### Post by jocampo on 2009-07-29
> **DGeeez said:**
> Linux engineers should not decide whether I should have this convenience (it sure ISN'T Windows), and the difference is essential when you are recycling much rewriteable media. If it's not installed default, then I should be able to add it to the Nautilus right-click menu - anyone know how this can be done?

Thanks.

Did you try BRASERO?... also, I think you can use this from command line as well:

```
cdrecord dev=cdburnerdevice blank=all
```

---

### Post by DGeeez on 2009-07-29
[QUOTE=jocampo]Did you try BRASERO?...[/QUOTE]
That's the first thing which caused me annoyance, Brasero being so testy as it is - the only option it gives me is to insert a blank "writeable" CD! I then need to either open a Terminal session and then navigate to my CD before looking up the proper command syntax, or just take the CD to my Windows machine. Of course, it would be a lot better if I didn't have to do either - that's probably why Windows engineers included the format option on right-click menu of their file browser, and ya know, just because Microsoft did it doesn't make it a bad idea.

Anyway, I can't be at my GNOME machine for awhile, but what is that cdrecord command supposed to do?

---

### Post by DGeeez on 2009-07-29
> **philinux said:**
> Think this is a wishlist item in Karmic.
[http://ubuntuforums.org/showthread.php?t=1223139](http://ubuntuforums.org/showthread.php?t=1223139)

Install either K3b or gnomebaker. I prefer k3b myself.

I'll have to try K3b, since Gnomebaker crashes every time I try to use it.

---

### Post by DGeeez on 2009-07-29
> **coffeecat said:**
> I don't know about your Brasero, but my Brasero copes just fine. I often use it to write to a used DVD-RW or CD-RW. Brasero detects this, asks whether I want to erase it, and then goes on to a successful burn.

Or you can Tools > Erase in the main Brasero window.

I sure wish Brasero would ask me if I wish to erase my CD, but I just get "please insert writeable media" as if it had never been formatted. Could something misconfigured be causing that, without a litany of others as well?

---

### Post by coffeecat on 2009-07-29
> **DGeeez said:**
> Could something misconfigured be causing that, without a litany of others as well?

I wish I knew. I've noticed in other threads that there are people who can't get Brasero to work properly, and others who find it 100% reliable. I'm fortunate that I'm in the latter group. Unfortunately, there's no 'preferences' choice in the Brasero menus for you to see if anything is awry. There's a ~/.gconf/apps/brasero folder with a load of configuration stuff in it. You could try backing that up by renaming it and then opening Brasero again. It *should* create a new ~/.gconf/apps/brasero folder with default configurations. That might get it to prompt for erasing.

Whatever - if Brasero doesn't work for you, k3b is an excellent app with many more options to it. I used it regularly until Brasero came along. I still do occasionally.

---

