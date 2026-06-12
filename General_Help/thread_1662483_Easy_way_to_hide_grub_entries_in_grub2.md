---
title: "Easy way to hide grub entries in grub2?"
date: 2011-01-08
forum: General Help
---

### Post by Bucky Ball on 2011-01-08
Hi all,

I have been fooling around with some of the new kernels and have ended up with a lot of options in my grub at boot. I have been checking this page:

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

... and it appears hiding the entries in grub2 is not as easy as hashing them out (#) which was the convention in grub.

My problem: I have installed kernel 2.6.36 and 2.6.37 just to fool around. Neither works in anything but low-graphics as it seems the ATI graphics driver is not working in either yet. They both also kill my wireless (don't recognise the card). BUT I don't want to completely uninstall them as I'd like to keep playing around as time goes on and they develop. I'd like to just hide them from the menu.

Is there some easy way of doing this? The link I provide only gives options to make the kernel non-executable (overly complicated process) or remove the kernel completely, neither of which I want to do.

This used to be simple in grub, open a file and add or remove a #, and - although overall I prefer grub2 - IMHO this 'improvement'  seems a little like a backward step. Sure a million people will disagree, but ...

Any ideas? Tnx in advance ... :D

---

### Post by TeoBigusGeekus on 2011-01-08
The only way I've found is to manually edit the grub.cfg file and comment out the entries you don't want to appear.
Of course, you have to do this after every kernel update (after everytime update-grub is run in general), so I don't know how much this "solution" will suit you.

Personally I don't use grub2; I'm still on grub legacy, as grub2 made my ttys disappear. I might try it again after a year or so, but until then grub legacy is perfect for me.

---

### Post by Bucky Ball on 2011-01-08
Thanks for that TeoBigusGeekus. So you can 'downgrade' to grub legacy? Think I'll just remove 'em for now, anyhow. I have .debs to install so easy to do that a little down the track. ;)

---

### Post by DeFrancoj on 2011-01-08
update-grub generates the grub.cfg file based on the contents of /etc/default/grub and /etc/grub.d. It ignores the files in /etc/grub.d/ that are not executable, so in your case I would probably chmod a-x the 10_linux and 30_os_prober entries and then write the 40_custom file to your liking (can probably even copy/paste the entries from your current grub.cfg). That's pretty close to editing the menu.lst file in legacy grub. 

Overall I think grub2 is an improvement, does a lot of things automatically and makes it less likely that a typo will leave you with an unbootable system that you have to go running for a live disk to fix. May as well learn it. 

You can also check out grub-set-default.

---

### Post by TeoBigusGeekus on 2011-01-08
> **Bucky Ball said:**
> Thanks for that TeoBigusGeekus. So you can 'downgrade' to grub legacy? Think I'll just remove 'em for now, anyhow. I have .debs to install so easy to do that a little down the track. ;)

I don't know if you can downgrade on ubuntu; I use arch.

---

### Post by stinkeye on 2011-01-08
grub-customizer allows you to hide entries in grub2 easily.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html[/COLOR]_**]("http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html")

---

### Post by Bucky Ball on 2011-01-08
> **stinkeye said:**
> grub-customizer allows you to hide entries in grub2 easily.
[**_[COLOR=DarkRed]http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html[/COLOR]_**]("http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html")

That is absolutely ROCKIN'!!! Fits the job perfectly. Now I have a neat menu without my 'testing' kernels which I can add when I want with a couple of clicks! Sure glad I didn't uninstall any kernels before I tried this. It is easy enough to add them back but this is even easier. 

Thanks a heap, stinkeye. Well spotted. ;)

PS: Should be in the repos, IMHO, although I realise that may not be possible for whatever reason.

---

### Post by stinkeye on 2011-01-08
Yeah it's a much needed progam.
Works with burg too.
I subscribe to the webupd8 and OMG!UBUNTU! RSS feeds for these little gems.

---

### Post by capn.hector on 2011-01-09
thanks for the program tip.  if grub2 had menu.lst that would be great this is second best

---

### Post by Bucky Ball on 2011-01-09
I passed this on to another user with instructions for adding the software source, etc. They couldn't get the instructions to work for some reason so they tried Ubuntu Software Centre and there it was!

I tried Synaptics and there it wasn't so I tried Software Centre and sure enough, it was there. 

In other words, another way to install is Ubuntu Software Centre and search for 'Grub Customizer' (talking 10.04 LTS and later). :)

---

### Post by stinkeye on 2011-01-09
Pretty sure it's not in the repos without adding the 
danielrichter2007 ppa.

---

