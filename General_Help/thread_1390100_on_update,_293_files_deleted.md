---
title: "on update, 293 files deleted"
date: 2010-01-25
forum: General Help
---

### Post by swright007 on 2010-01-25
I did an update on one of my main computers last night.  while in the update it reported "293 files to be REMOVED and 1 to be added".... it cranked away for some time and now all I get is a text login to my desktop. There is no graphics anymore. just a command line.

Is there any way to make it boot the way it used to or will I have to reinstall without formatting my hard drive (if so, how do I do this?)?  I have checked and all my personal data is in tact.   I was running Hardy Heron with 5.4 gigs of an 80 Gig HD free and 2 Gigs of RAM with an AMD 5000+ processor.    Thank you in advance !

                                 Scott

---

### Post by mikewhatever on 2010-01-25
Boot the recovery mode, select the networking option, login and install ubuntu-desktop.

sudo apt-get install ubuntu-desktop

---

### Post by howefield on 2010-01-25
Sounds like maybe you removed ubuntu-desktop package.

Try typing at the command line, after login

```
sudo apt-get install ubuntu-desktop
```

What does that give you ? (Does it want to install it ?)

---

### Post by swright007 on 2010-01-25
When I booted it took me straight to TTY mode.  I tried to download it but it said there were unmet dependencies.  it said I should do a "sudo apt-get -f install" to correct broken packages.  In doing so, it wanted to delete 193 more files and fix 1

---

### Post by howefield on 2010-01-25
You could spend some time fixing it, to have a clue on how to help you'd need to explain exactly what you were doing.

But I think I'd simply reinstall without formatting, being the quickest fix. Backup your data if required and reinstall into the same partitions without marking them for format.

---

### Post by Marvin666 on 2010-01-25
I have a jaunty partiton that's messed up (no network manager, and it resists attempts to install one). Would reisntall without partition keep the programs and settings I have (but add the ones I unistalled), or would it be like a fresh install afterwards?

---

### Post by howefield on 2010-01-25
> **Marvin666 said:**
> I have a jaunty partiton that's messed up (no network manager, and it resists attempts to install one). Would reisntall without partition keep the programs and settings I have (but add the ones I unistalled), or would it be like a fresh install afterwards?

Your second sentence makes no sense whatsoever, try rephrasing it in a new thread/topic.

---

### Post by swright007 on 2010-01-25
if that is the case, having to reinstall.   How can I get the notes off TomBoy notes and should I do that before or after I reinstall ?

---

### Post by howefield on 2010-01-25
Backing up all your data before you start is only insurance against anything nasty happening, installing over the existing partitions without marking them for formatting should keep your data intact.

Your tomboy notes, I think, are stored in ~/.tomboy as .note files.

---

### Post by Vaphell on 2010-01-25
i think you can't avoid formatting / partition, that's why having separate /home partition is so convenient - it can be left untouched during fresh install so user data is still there.

---

### Post by swright007 on 2010-01-30
Ok, thank you.  Is there any way during initial install to request the /home directory to be set up on another drive or partition?   I don't recall that even being an option but would be greatly helpful if it were.   I am currently running off a Karmic live-CD.

---

### Post by oldos2er on 2010-01-30
You'd need to select manual installation to create or delete or resize partitions.

---

### Post by howefield on 2010-01-30
There is a partitioning video on screencasts.ubuntu.com that might be helpful. It is about 10 minutes long.

[http://screencasts.ubuntu.com/2009/09/11/Screencasting_on_Ubuntu_-_Part_1_of_3](http://screencasts.ubuntu.com/2009/09/11/Screencasting_on_Ubuntu_-_Part_1_of_3)

---

