---
title: "Grub2 hiddenmenu"
date: 2009-10-16
forum: General Help
---

### Post by JebusWankel on 2009-10-16
I have a dual boot, but I so seldom use the other OS (Debian actually) that I'd rather Grub just boot right away into Ubuntu and not show the menu. I couldn't figure out how to do this. I Googled around and found that what I wanted, the hiddenmenu option, has been taken out of Grub. Instead, you have to implement it yourself with an albeit short script.

I like the other things about Grub2: better looking, the update-grub function is probably a miracle if you've ever nuked grub by misconfiguring menu.lst. Adding backgrounds is nifty too, and, assuming you find a use for it, the scripting is probably cool. I just don't see how deprecating what I assume is a popular option is a good idea.

Btw, here's the script on [the Grub wiki]("http://grub.enbug.org/Hiddenmenu"). Google yields some others.

---

### Post by Rocket2DMn on 2009-10-16
I think the equivalent in Grub2 is GRUB_HIDDEN_TIMEOUT in /etc/default/grub which needs to be uncommented and set to 0 for there to not be a menu prompt.  There is more info here - [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

More user friendly documentation is in progress to go here (being written by our friend, drs305) - [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) (currently redirects to the wiki link above).  He also has some nice Grub2 tutorials here - 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

HTH

---

### Post by JebusWankel on 2009-10-17
Thanks for the tip, but it didn't work. The menu showed up for about 2 seconds, with the countdown starting at 4, even though there's no 4 in my config file.

---

### Post by Rocket2DMn on 2009-10-17
What about the GRUB_HIDDEN_MENU_QUIET property?  Is that set to true?

---

### Post by drs305 on 2009-10-17
It actually probably started at 5, but maybe the first number we see is 4. Check to see with:
```

cat /etc/default/grub | grep "GRUB_TIMEOUT"

```
If there is no number, it defaults. I've seen different default values in the past four months (I think), with different installs varying from 5-15 seconds. Chances are good it now defaults to 5 seconds if there is no value present.

If you don't want to see anything, you should be able to set the GRUB_TIMEOUT=0 and it should boot without delay. You should probably also remove any GRUB_HIDDEN_TIMEOUT value, and to cover all the bases, it should proably be GRUB_DEFAULT=saved for which option to boot.

```

gksu gedit /etc/default/grub

```

Don't forget to run "sudo update-grub" after you have made the changes.

There are a couple of Grub links in my signature line if you are interested.

---

### Post by Rocket2DMn on 2009-10-17
> **drs305 said:**
> It actually probably started at 5, but maybe the first number we see is 4. Check to see with:
```

cat /etc/default/grub | grep "GRUB_TIMEOUT"

```

If you don't want to see anything, you should be able to set the GRUB_TIMEOUT=0 and it should boot without delay. You should probably also remove any GRUB_HIDDEN_TIMEOUT value, and to cover all the bases, it should proably be DEFAULT=saved for which option to boot.

```

gksu gedit /etc/default/grub

```

There are a couple of Grub links in my signature line if you are interested.

Just the man I was looking for! I've already linked the OP to your posts :)
:guitar:

---

### Post by JebusWankel on 2009-10-17
Thanks! I took the slightly unscientific method and followed all your suggestions at once.

I ended up with this:
```
GRUB_DEFAULT=saved
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
```

And it did the job.

---

