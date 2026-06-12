---
title: "install problems"
date: 2009-10-20
forum: General Help
---

### Post by TCollins on 2009-10-20
Hello all ... i have a problem with my package manager, it tells me i will need to run "sudo dpkg-configure-a to correct this problem but i am new to ubuntu and i dont know how to do this can any one tell me.. thanks

---

### Post by VastOne on 2009-10-20
> **TCollins said:**
> Hello all ... i have a problem with my package manager, it tells me i will need to run "sudo dpkg-configure-a to correct this problem but i am new to ubuntu and i dont know how to do this can any one tell me.. thanks

Open a terminal and type in sudo dpkg-configure-a

It will ask yo for your password

Type it in and hit enter and follow any instructions.

It s OK if yo do not see anything as you type in your password, that is normal

---

### Post by P4man on 2009-10-20
probably an install or update that got aborted before it finished. Open a terminal (applications > accessoiries > terminal)

copy/Paste this command:

```
sudo dpkg --configure -a 
```
(paste using mouse middle click or shift+control+v)

Type your password and let it work. You may have to reboot after it finishes.

---

### Post by P4man on 2009-10-20
> **VastOne said:**
> Open a terminal and type in sudo dpkg-configure-a


Careful you copy pasted his typo. Its 
```
sudo dpkg --configure -a
```

mind the spaces and double --

---

### Post by John Bean on 2009-10-20
Surely you mean:
```
sudo dpkg --configure -a
```Open a terminal (Applications menu : Accessories : Terminal) and just type it in.

---

### Post by P4man on 2009-10-20
> **John Bean said:**
> Surely you mean:
```
sudo dpkg --configure -a
```Open a terminal (Applications menu : Accessories : Terminal) and just type it in.

Yes he meant
```

sudo dpkg --configure -a
```

So the OP has to type or copy paste

```
sudo dpkg --configure -a
```

and not the other command which looks like but is not

```
sudo dpkg --configure -a
```

Did we mention he needs to open a terminal before typing

```
sudo dpkg --configure -a
```

?

:D

---

### Post by VastOne on 2009-10-20
My bad! Thanks for pointing out what was NOT so obvious to me....

---

### Post by VastOne on 2009-10-20
> **P4man said:**
> Yes he meant
```

dpkg --configure -a
```

So the OP has to type or copy paste

```
dpkg --configure -a
```

and not the other command which looks like but is not

```
dpkg --configure -a
```

Did we mention he needs to open a terminal before typing

```
dpkg --configure -a
```

?

:D

Yes, we are all so very clear on it now!!!!
:confused:   :P

---

### Post by P4man on 2009-10-20
oops.. edit, ignore this

---

### Post by John Bean on 2009-10-20
> **P4man said:**
> Yes he meant
```

sudo dpkg --configure -a
```So the OP has to type or copy paste

```
sudo dpkg --configure -a
```and not the other command which looks like but is not

```
sudo dpkg --configure -a
```Did we mention he needs to open a terminal before typing

```
sudo dpkg --configure -a
```?

:D

Thanks for the sarcasm. Did it occur to you that your post hadn't appeared at the time I posted mine?

Never mind, not everyone is perfect.

---

### Post by P4man on 2009-10-20
> **John Bean said:**
> Thanks for the sarcasm. Did it occur to you that your post hadn't appeared at the time I posted mine?

Never mind, not everyone is perfect.

Yes of course, but it was still funny looking at the thread :D

---

### Post by John Bean on 2009-10-20
> **P4man said:**
> Yes of course, but it was still funny looking at the thread :D

True. The almost identical responses must be down to the "Great minds..." (etc) thing. The humour is unfortunately a result of my pathetically slow typing :-(

---

### Post by daboochmeister on 2009-11-02
I'll risk a serious follow-on q. - I had to do the above, because of an aborted install (not complaining -- my setup is pretty customized, I installed Ubuntu, but have switched to kde-desktop and am using KWin for login instead of gdm, etc. etc. -- lotsa small things that are off the beaten test path) ...

I had 3.1GB free in / before upgrade, and only 1.0GB free after.  I suspect there's things leftover that I should be cleaning, but a "sudo aptitude clean" didn't free much.  What else should I do to cleanup from an aborted/manually resumed install?

I have /home and /boot on their own partitions, btw, and there doesn't appear to be any jaunty cruft there.

tia!

---

### Post by P4man on 2009-11-03
> **daboochmeister said:**
> I'll risk a serious follow-on q. - I had to do the above, because of an aborted install (not complaining -- my setup is pretty customized, I installed Ubuntu, but have switched to kde-desktop and am using KWin for login instead of gdm, etc. etc. -- lotsa small things that are off the beaten test path) ...

I had 3.1GB free in / before upgrade, and only 1.0GB free after.  I suspect there's things leftover that I should be cleaning, but a "sudo aptitude clean" didn't free much.  What else should I do to cleanup from an aborted/manually resumed install?

I have /home and /boot on their own partitions, btw, and there doesn't appear to be any jaunty cruft there.

tia!

Run Disk usage analyser (apps > accessories)  to see where your space has gone. 2 GB sounds like a lot for an upgrade, but never having done it, I wouldnt know. If you want to expand your / this might help:
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

