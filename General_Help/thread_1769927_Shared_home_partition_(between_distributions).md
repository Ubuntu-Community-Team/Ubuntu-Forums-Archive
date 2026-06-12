---
title: "Shared home partition (between distributions)"
date: 2011-05-28
forum: General Help
---

### Post by Martin_sensei on 2011-05-28
Hello,

Just a general question:

If I have /home on a separate partition, is it possible to mount that /home partition on multiple distributions (Ubuntu, SuSE for example) on the same PC?

---

### Post by ram0042 on 2011-05-28
> **Martin_sensei said:**
> Hello,

Just a general question:

If I have /home on a separate partition, is it possible to mount that /home partition on multiple distributions (Ubuntu, SuSE for example) on the same PC?
Yes it is. I had it working with Arch and Ubuntu but after I upgraded Ubuntu to 11.04 manually, I guess I forgot to uncheck the format. So not sure if Ubuntu handles it with the "Upgrade ubuntu X to 11.042" option.

---

### Post by Martin_sensei on 2011-05-28
OK, great, I'll give it a go.  Just wanted to make sure there was no reason NOT to do it...

---

### Post by Morbius1 on 2011-05-28
You can mount it but it may not do you any good. It's been a while since I used a non-debian based system but as I recall both RedHat ( i.e., Fedora ) and SuSE start their uid's at 500. But Debian based systems start with 1000.

So if you have a user named: morbius in Fedora his uid = 500. The same user on Ubuntu has a uid = 1000. So morbius is not morbius and one may not be able to write to the others files.

---

### Post by srs5694 on 2011-05-28
The UID issue might or might not be a problem, and is easily overcome (I'll get to that in a moment). A bigger issue is that you want to ensure that you don't use the same user home directory within /home for two distributions. That is, if you're martin on Ubuntu, you've probably got a home directory of /home/martin. That means that when you install SUSE, you should be sure to use another home directory -- perhaps /home/martins. The easiest way to do this is to use a different username in each distribution; however, you can use the usermod command to alter the username after installation without also modifying the home directory. This will let you have the same username but a different user home directory. Some distributions also let you set a custom home directory on installation, but I don't happen to recall if SUSE is one of them. (Fedora is, FWIW.)

If you want to access all the same user files in both distributions, you can set up symbolic links between the two home directories. (The problem with sharing is with configuration files.)

The UID issue might not be a problem if you don't expect to share files with yourself between distributions, or if you rely on something else (like an SMB/CIFS network server or an NTFS or FAT partition) that doesn't understand Linux UID numbers for cross-distribution file sharing. IIRC, SUSE starts numbering its UIDs from 1000, as does Ubuntu, so you may have matching UID numbers from the start. If not, the problem can be overcome using the same usermod command that can change the username.

Type "man usermod" at a shell prompt to learn about it. I recommend practicing on a test account. Note that modifying an account while it's in use is tricky. This is a drawback of Ubuntu's reliance on sudo; you can't modify your own account in this way -- or if you do, strange things can happen. Thus, I recommend modifying SUSE's accounts, since with SUSE you can log out of your account and do a direct root login. Alternatively, you could activate root in Ubuntu or create a second account with administrative access and use it to modify your main account.

---

### Post by Martin_sensei on 2011-06-03
Thanks for the reply!

I was under the impression that a separate /home partition was the way to go if you wanted multiple distributions on the same machine, however this sounds like it may cause problems.

I have one more question though, I have ubuntu installed on one PC, and I was thinking of installing Kubuntu instead.

Can I keep the /home partition as is?

Cheers

---

### Post by vhradice on 2011-06-03
I am currently running Fedora 14 and I am thinking of switching to Ubuntu. I would like to run it for a while and get familar with it. I have some space to create a partition and install it.  I would like to use the same /home/me directory for both distros.  I can't tell from reading this if
(1) Is it possible to do this?
(2) Is it safe to do this?
(3) what may/will get screwed up if I do this?

I am familiar enough with grub to fix the config file.  Which leads to the question - which version of grub does Ubuntu use - legacy or Grub2?

Thanks now for your help.

p.s. What brought this on was I downloaded FC15, installed it, and I don't like what they did to the user interface.

---

### Post by srs5694 on 2011-06-04
> **vhradice said:**
> I am currently running Fedora 14 and I am thinking of switching to Ubuntu. I would like to run it for a while and get familar with it. I have some space to create a partition and install it.  I would like to use the same /home/me directory for both distros.  I can't tell from reading this if
(1) Is it possible to do this?

Yes.

> (2) Is it safe to do this?

No.

> (3) what may/will get screwed up if I do this?

In a "stock" configuration, ownership of files will become a problem because Ubuntu and Fedora assign different UID values to their users. If you solve this problem (as described in my previous post), you could have specific applications behave strangely in one or both distributions because their configuration files might not work properly with two different versions of the program. Another related issue is that icons and other support files might be stored in different locations, so icons are likely to change when you reboot.

Using a separate user home directory is *not* difficult. Do it that way and you'll have no problems.

> I am familiar enough with grub to fix the config file.  Which leads to the question - which version of grub does Ubuntu use - legacy or Grub2?

GRUB 2.

> p.s. What brought this on was I downloaded FC15, installed it, and I don't like what they did to the user interface.

Many Ubuntu users dislike the recent Ubuntu change to Unity. It's got some similarities to Fedora's change to GNOME 3, so it's possible you won't like Unity any more than you like GNOME 3. There may be a way to force Fedora 15 to log in using its "legacy" mode, which it normally uses on computers with older graphics hardware or graphics hardware with weaker acceleration support. (The equivalent is certainly possible with Ubuntu.) You could also try switching desktop environments entirely -- KDE, Xfce, and LXDE are three possibilities.

---

### Post by vhradice on 2011-06-05
Thank you for the reply.  My reason for asking (1) was that I didn't want things to get lost like mail and any documents I change.  It sound like if I put things like documents and mail files separate from the rest of home, I can test and see if I want to switch.  The other option is to load a separate machine with ubuntu and test that and switch my real pc over if I like what I see.

---

