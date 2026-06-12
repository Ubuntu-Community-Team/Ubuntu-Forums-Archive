---
title: "Login Troubles."
date: 2010-08-19
forum: General Help
---

### Post by John Peschken on 2010-08-19
I'm still new to Linux and Ubuntu.  I installed it with no serious trouble a couple weeks ago, love it, but now I have hit a snag that I can not seem to get around.

I can't log in anymore.  I enter my password, click to proceed, some text flashes by too fast to read, and I end up back at the log in dialogue.  This happens whether I try to use my account or the no-password-yet account I set up for my wife.

I may have unwittingly done something by attempting to remove Evolution from the computer, but I thought that I was being pretty careful to only remove things that were part of Evolution.

How do I recover from this?

I am now reduced to using the Windows computer to post this message.  I feel so unclean somehow.

Thank you for your support of this clueless noob!

---

### Post by dcollier on 2010-08-19
How did you remove evolution?  Have you tried logging in at the command prompt? "crtl + alt + f1"

---

### Post by silbak04 on 2010-08-19
Try booting from LiveCD and chrooting...and mount all your drives, install Evolution...

This link will tell you how to chroot:

[http://superuser.com/questions/111152](http://superuser.com/questions/111152)

---

### Post by varunendra on 2010-08-19
Before trying what silbak04 suggested, try booting into 'Recovery Mode' (press & hold 'shift' key while booting) and select dpkg there. Sometimes, a broken system can be recovered this way.

---

### Post by John Peschken on 2010-08-19
> **dcollier said:**
> How did you remove evolution?  Have you tried logging in at the command prompt? "crtl + alt + f1"
Nope, didn't know the "crtl + alt + f1" trick.  I ran into that earlier today, but didn;t pay much attention because I thought it was just to get you to terminal mode, and I didn't see how that would help me.  I'll see what happens tonight when I get back to my ex-Linux box.

---

### Post by John Peschken on 2010-08-19
> **John Peschken said:**
> Nope, didn't know the "crtl + alt + f1" trick.  I ran into that earlier today, but didn;t pay much attention because I thought it was just to get you to terminal mode, and I didn't see how that would help me.  I'll see what happens tonight when I get back to my ex-Linux box.
I _tried_ to get rid of Evolution by removing all the things that appeared to be part of it in the software center.  I don't care for it, and I'm sort of compulsive about uninstalling software I don't use.  I have no idea if that's how I blew it up.

---

### Post by John Peschken on 2010-08-19
> **dcollier said:**
> How did you remove evolution?  Have you tried logging in at the command prompt? "crtl + alt + f1"
I just now tried Ctl-Alt-F1, and that did get me to the command prompt.  I have no idea how to proceed from there, but I do get a command prompt.   Maybe it is a hint that my problem happens when Gnome tries to load on top of that, but what do I know?  I am the newbie here!

---

### Post by John Peschken on 2010-08-19
> **varunendra said:**
> Before trying what silbak04 suggested, try booting into 'Recovery Mode' (press & hold 'shift' key while booting) and select dpkg there. Sometimes, a broken system can be recovered this way.
Booting into recovery mode doesn't seem to have fixed much of anything.  I choose recovery mode from the text mode menu that comes up, but I get the same result as before.  There were two different recovery mode options offered which seemed identical.  I tried them both with the same result.

Thanks for the information, though.  I did not know how to get to recovery mode.  That could prove useful later.

---

### Post by spibou on 2010-08-19
Login to console and do```
sudo apt-get install gnome
```

---

### Post by John Peschken on 2010-08-19
> **varunendra said:**
> Before trying what silbak04 suggested, try booting into 'Recovery Mode' (press & hold 'shift' key while booting) and select dpkg there. Sometimes, a broken system can be recovered this way.
I missed the "select dpkg there" portion of your message on the first reading.   Sorry about that.  I tried again. dpkg did do a lot of work, but the problem remains.

---

### Post by John Peschken on 2010-08-19
> **silbak04 said:**
> Try booting from LiveCD and chrooting...and mount all your drives, install Evolution...

This link will tell you how to chroot:

[http://superuser.com/questions/111152](http://superuser.com/questions/111152)
Thanks for the link, but there's an awful lot I don't understand there.  I think I will have to give the sudo apt-get install gnome solution a try before I try to decipher the chroot solution.

---

### Post by John Peschken on 2010-08-19
> **spibou said:**
> Login to console and do```
sudo apt-get install gnome
```
That results in complaints from Ubuntu.

[B]... unmet dependencies
Gnome: Depends: swfdec-mozilla but it is not going to be installed.[/B]

---

### Post by John Peschken on 2010-08-19
I wonder if Ubuntu gives me reinstall options if I just boot off the live CD.  I think I will see if that gets me anywhere.  I don't have that much invested in my configuration that I can't recreate easily enough.   Documents are backed up, I just want to salvage all the MP3's I ripped onto the hard drive.

---

### Post by John Peschken on 2010-08-19
Ladies and/or Gentlemen;

It seemed like the effort to revive my system was taking more time and trouble than starting over with a fresh install, so I went for the fresh install.  All I really lost was some MP 3's ripped from CD's.  I haven't tried yet, but the documents should all be retrievable (Please oh please!) since I had simple backup/restore working behind the scenes on those.  Thanks for all your efforts.

---

