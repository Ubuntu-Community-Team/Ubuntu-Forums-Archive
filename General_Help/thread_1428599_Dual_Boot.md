---
title: "Dual Boot"
date: 2010-03-13
forum: General Help
---

### Post by SaRaveok on 2010-03-13
Hi there, i just installed Ubuntu on my Vista Machine in order to get to use it more and more, but at the same time i want to keep using Vista as it has the games that i play on there.

Ubuntu installed correctly without any problems, and after a while in using it i wanted to go play some games on vista, restarted the computer, it came up to the dual boot part and when i went to vista it came up Loading Grub then when back to dual boot, so now i can only access Ubuntu

Please Help

---

### Post by krapp on 2010-03-13
Newbie here as well: GRUB is how you get into not only Ubuntu, but all of your OSes. I am dual-booting Windows 7 & Ubuntu, and I get some 6 options in GRUB at startup. This may sound too obvious, but based on your wording I must ask: are you sure Vista or some sort of Windows isn't there further down the list?

---

### Post by SaRaveok on 2010-03-13
The only option for windows is vista and its at the bottom of the list

---

### Post by wilee-nilee on 2010-03-13
> **krapp said:**
> Newbie here as well: GRUB is how you get into not only Ubuntu, but all of your OSes. I am dual-booting Windows 7 & Ubuntu, and I get some 6 options in GRUB at startup. This may sound too obvious, but based on your wording I must ask: are you sure Vista or some sort of Windows isn't there further down the list?

I would be careful with that advice, some Ubuntu installs  have the recovery and main OS show up for Windows in grub. Hitting the recovery by accident has caused people to mess up the MBR and other problems.


So how did you resize the vista partition, and is this a actual dualboot?

---

### Post by krapp on 2010-03-13
> **SaRaveok said:**
> The only option for windows is vista and its at the bottom of the list

Read what it says to us.

---

### Post by SaRaveok on 2010-03-13
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sdb1)

That is everything that i see.

and after i did the sudo update-grub i tried to access vista again, and now it comes up with Mount of filesystem failed
A maintenance shell will now be started

:|

---

### Post by SaRaveok on 2010-03-13
> **wilee-nilee said:**
> I would be careful with that advice, some Ubuntu installs  have the recovery and main OS show up for Windows in grub. Hitting the recovery by accident has caused people to mess up the MBR and other problems.


So how did you resize the vista partition, and is this a actual dualboot?


I resized the vista partition through vista itself

---

### Post by krapp on 2010-03-13
> **SaRaveok said:**
> Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sdb1)

That is everything that i see.

and after i did the sudo update-grub i tried to access vista again, and now it comes up with Mount of filesystem failed
A maintenance shell will now be started

:|

So yes, it seems you're missing an option. I'm of no further help at this point. Sorry, and good luck!

---

### Post by wilee-nilee on 2010-03-13
Download this script to your desktop.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Then run in the terminal,
sudo bash ~/Desktop/boot_info_script*.sh
This will deposit a result text for you to post so the people who can help you will get a look.

---

### Post by Mark Phelps on 2010-03-13
> **SaRaveok said:**
> I resized the vista partition through vista itself

OK, so you did that right.  

Did you then boot back into Vista a couple of times after the resize to ensure that it still worked?

Or did you first discover that it no longer booted when you tried to boot into it from GRUB?

If the second is true, do you have a Vista installation DVD?

---

