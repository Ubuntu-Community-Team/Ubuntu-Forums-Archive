---
title: "What is this?  Is this repository important????"
date: 2012-07-07
forum: General Help
---

### Post by Petro Dawg on 2012-07-07
My desktop was kept getting an error about not being able to download some packages during update.  I was able to "fix" it by editing /etc/apt/sources.list

I disabled the following line by adding # before it...

```
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

I use Ubuntu 12.04, so I'm not sure why "breezy" updates were in the sources list.  Does anyone know what uses this update repository?

---

### Post by msammels on 2012-07-07
That repository looks like updates for restricted codecs and programs for  Breezy. If you are on 12.04 you can remove that, no problem.

---

### Post by MG&amp;TL on 2012-07-07
[https://wiki.ubuntu.com/BreezyBadger](https://wiki.ubuntu.com/BreezyBadger)

Nothing should use that repository, it went EOL some time ago. 

Intriguing how it got there though....:)

---

### Post by msammels on 2012-07-07
Perhaps he updated from Breezy, amazingly never had to fresh install, and it was never removed. :P You should keep it, for the vintage feel :D

I mean, come on... Ubuntu 5.10... you have repositories from 2005 :D

---

### Post by Petro Dawg on 2012-07-07
Thanks for the quick replies, I didn't think the repository was critical to 12.04, but since I'm rather new to Ubuntu, I wanted a couple more opinions before permanently disabling it.

---

### Post by Petro Dawg on 2012-07-07
> **msammels said:**
> Perhaps he updated from Breezy, amazingly never had to fresh install, and it was never removed. :P You should keep it, for the vintage feel :D

I mean, come on... Ubuntu 5.10... you have repositories from 2005 :D
Nope, this was a fresh complete install with 12.04, never ever saw any Ubuntu version prior to precise.

---

### Post by msammels on 2012-07-07
Holy bajingo... how did you manage to get 5.10 updates? :P Did you install some really old software or something? :P

---

### Post by Petro Dawg on 2012-07-07
> **msammels said:**
> Holy bajingo... how did you manage to get 5.10 updates? :P Did you install some really old software or something? :P

Like I said, I'm new to Ubuntu, so its quite possible in the first couple days in trying to figure out the system I installed something weird... But, this error did not show up until quite recently, and I haven't installed anything new lately, so I haven't the foggiest idea on how it happened.

Perhaps a rare Ubuntu Virus is lurking (mostly joking, but still some hint of concern).

---

### Post by msammels on 2012-07-07
I have yet to see a Linux-based virus... relax.

---

### Post by Petro Dawg on 2012-07-07
> **msammels said:**
> I have yet to see a Linux-based virus... relax.


Some sarcasm was intended, I'm not actually worried, I don't see a reason anyone would want to write a virus that wants to update breezy , aside from just wanting to be incredibly annoying? 

I'm sure I was messing around in terminal at some point and copied some old text from an old fix for some other problem I was trying to fix, and just didn't notice the problem it caused until today.  

Come to think of it, I was trying to get my old 3.5 floppy drive to work, and I bet it had something to with that fix.  Yes, I still have floppies lying around :p; for that "vintage feel."

---

### Post by msammels on 2012-07-07
Haha, I still use floppies today :P

---

### Post by Petro Dawg on 2012-07-07
> **msammels said:**
> Haha, I still use floppies today :P

Do you use 12.04?  If so, are you able to mount the floppy drive aside from using the terminal, did you have to apply some fix?  

I cannot read floppies unless I manually mount the internal drive from the terminal.  Its kind of annoying, but its not something I use often so its no big issue.

---

### Post by msammels on 2012-07-07
I say I use floppies. I do use 12.04, but I do not use floppies on my Linux machines, sorry.

---

### Post by Petro Dawg on 2012-07-07
> **msammels said:**
> I say I use floppies. I do use 12.04, but I do not use floppies on my Linux machines, sorry.

Ok, thanks anyways.  Floppy support on Ubuntu seems to be rather lacking.  I also have a tape drive around somewhere that would interesting to use, but I rather doubt that would be well supported.  

Guess I'll just be forced into the USB flash drive era and give up trying to get my archaic media to work correctly.

---

### Post by Old_Grey_Wolf on 2012-07-07
> **Petro Dawg said:**
> Guess I'll just be forced into the USB flash drive era and give up trying to get my archaic media to work correctly.

I have a floppy drive for playing some old DOS games using DOSBox. My external USB floppy drive mounts as soon as I plug it in. It may be different for in internal floppy drive. The USB interface may make it function differently.

---

