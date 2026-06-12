---
title: "Neato 4 CD/DVD Label Maker?"
date: 2009-08-27
forum: General Help
---

### Post by Gael33 on 2009-08-27
Neato 4 CD/DVD Label Maker is probably the easiest and best label maker on the market ... the problem is is that it doesn't work with Linux Ubuntu etc. I have tried installing it using Wine, again the installation failed.
Has anybody found a way to get Neato 4 to work on Ubuntu, or is there another program out there that would do the job, either a substitute for Neato 4, or a program that will allow Neato 4 to run / work on the Ubuntu platform?
Any suggestions will be helpful, thanks.

gael.

---

### Post by TeoBigusGeekus on 2009-08-27
I use KoverArtist.

---

### Post by Gael33 on 2009-08-27
> **TeoBigusGeekus said:**
> I use KoverArtist.

Thank you :)

gael

---

### Post by Gael33 on 2009-08-28
> **Gael33 said:**
> Thank you :)

gael

As a relative newbie I need some advice ... how do I get Koverartist to show in Applications once it's been installed?

gael

---

### Post by TeoBigusGeekus on 2009-08-29
Right click on menus->Edit menus
Go to graphics and choose new item.
Type: application, command: koverartist, comment: whatever you want

---

### Post by Gael33 on 2009-08-31
> **TeoBigusGeekus said:**
> Right click on menus->Edit menus
Go to graphics and choose new item.
Type: application, command: koverartist, comment: whatever you want

Thanks again.
I eventually found the program in the Debian folder in Applications. However, it doesn't create the round CD/DVD labels, it only creates the labels for the plastic covers.
Back to the drawing board unless someone else has any ideas?

gael.

---

### Post by P4man on 2009-08-31
You can use glabels

```
sudo apt-get install glables
```

It has templates for all possible labels, including CD labels. Its not the most powerful or versatile drawing program, but it might do.

If not, you can use inkscape (vector graphics) or gimp (bitmaps) to make the art, then print it with glabels. If you want to use gimp, have a look at this:

[http://www.shallowsky.com/software/gimplabels/](http://www.shallowsky.com/software/gimplabels/)

---

### Post by oboedad55 on 2009-08-31
> **Gael33 said:**
> Thanks again.
I eventually found the program in the Debian folder in Applications. However, it doesn't create the round CD/DVD labels, it only creates the labels for the plastic covers.
Back to the drawing board unless someone else has any ideas?

gael.

I spent three weeks in Glasgow on business in 2006. What a great country! I know what you're looking for and I used to have something but I can't recall it. I'll check in another forum and see what they have to say.

--Jon

Hey, I found something. It's called DiscWrapper and you can download a .deb file to install in Ubuntu. Here you go: [http://www.getdeb.net/app/DiscWrapper](http://www.getdeb.net/app/DiscWrapper)

Jon

---

