---
title: "Win7 and Ubuntu 11.10 Dual Boot Question"
date: 2011-10-20
forum: General Help
---

### Post by EwOkIE on 2011-10-20
Hi all....

I have Win7 64Bit on my Sata HDD
Installed a 40Gb IDE Drive which I installed Ubuntu (unplugged sata before doing do so)

Now on plugging all drives back in it boots to Ubuntu all the time how do I get it to give me an option to wither I want Win7 or Ubuntu....

Also I get Signal Over Range on my monitor????

Any help would be appreciated..
Thanks :KS

---

### Post by /bin/sh on 2011-10-20
You should install ubuntu with wubi: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by tartalo on 2011-10-20
Since you installed Ubuntu with the Windows HD unplugged, when Grub was installed in the MBR it didn't detect any other OS but Ubuntu.

In a terminal try this:
```
sudo update-grub
```

And reboot

---

### Post by shadytv on 2011-10-20
install grub, sudo apt-get install grub-pc most likely its pre-installed so when booting up your computer try holding either shift or esc this should bring up a grub menu
hope this helps :)

---

### Post by techvish81 on 2011-10-20
u unplugged sata while installing ubuntu, so it is natural,
now if you can install ubuntu again with sata plugged in and selecting desired ide partitiion while installion and giving it mountpoint "/" it will automatically add win7 in grub entry and u will have to select which os to boot .

---

### Post by EwOkIE on 2011-10-21
Thanks guys spot on it was the MBR that was the issue.

Now another question...  if you could help

In the chat with that jabber.org thingy I get an network error but chat still works, any ideas.
Just using chat for for my 2 sons in the house on each laptop..i know if only they could walk;)

---

