---
title: "Copy &amp; Paste problem"
date: 2010-09-14
forum: General Help
---

### Post by jurco on 2010-09-14
Hi guys. I (Kubuntu10.04) have a problem with Copy&paste after closing source window.
I read some threads about this issue but none of them helped me.

I tried to run klipper, but that didnt help. There is one pro for klipper - it can store more values from which I can choose.

The problem is that I copy some text (from one window) which stores in klipper. Then I close the window and when I try to paste I get no result. The only way is to go to clipper and click the desired value from the list. But this is wasting of time (and nerves)...

anyone help please

---

### Post by ankspo71 on 2010-09-14
Hi,
Give "parcellite" a try.
It features this:
"Daemon mode; guard your clipboard contents when you close applications."
I used to use it with the Gnome Desktop and it worked great for me, and I'm almost positive it works just as well in KDE too.
Hope that helps.

---

### Post by jurco on 2010-09-14
Looks like parcellite gets no more development. This does not sound good to me.
If possible I would like to make klipper to work properly.

---

### Post by ianmillington on 2010-09-14
Yes, unfortunately Klipper does appear to have generally developed the behaviour to which you refer. So you have no option other than to select what you wish to paste.

At least that is my experience from programs like openoffice, firefox etc. Whether KDE applications such as konqueror/korganizer etc produce a different result I wouldn't know

---

### Post by jurco on 2010-09-14
Am I write when I say that all people using KDE experience difficulties with copy & paste or is it sth what I brought from Windows times (at least this way makes more sense to me)?

---

### Post by ianmillington on 2010-09-14
I can't say I've found it a problem myself - the ability to paste something I had copied earlier outweighs it for me. So much so that in windows I have installed ditto as I find the Windows XP clipboard woefully inadequate.

You might find help here

[http://gadgethubs.com/make-use-of-the-kde-4-5-clipboard/](http://gadgethubs.com/make-use-of-the-kde-4-5-clipboard/)

In particular have you tried the "unix way" i.e highlight and middle mouse click or enabling the actions function as a possible solution?

---

### Post by jurco on 2010-09-16
OK, I found the solution. I just needed to check option "Do not allow emtpy clipboard"
And add klipper to startup script :)
...but it took days...uff

---

