---
title: "Deleting multiple boot entries"
date: 2011-02-02
forum: General Help
---

### Post by columbus2012 on 2011-02-02
Hi! can somebody help clean up my boot screen?

It seems each time I select 'restart later' after downloading updates I get extra lines on my boot screen. The top line works correctly to get me into Ubuntu & the bottom Win.

How do I delete the unnecessary lines?

---

### Post by mac4rfree on 2011-02-02
Check out dis link,,,

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

This should help you.. hope dis s wat u r expecting.

---

### Post by plucky on 2011-02-02
> **mac4rfree said:**
> Check out dis link,,,

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

This should help you.. hope dis s wat u r expecting.

That will not work with Grub2 as that howto is editing menu.list.

@OP

Open **Synaptic Package Manager** and search for [/b]linux-image[/b] and mark the kernels you want to remove for "complete removal".
Also do the same for **linux-headers**.Do not remove the current kernel.

This will run "update-grub" after it is done and remove them from the boot list.

It is a good practice to leave at least one older kernel just in case you have problems with the most recent kernel.


Good Luck

---

### Post by drewsus on 2011-02-02
Better yet, install Ubunu Tweak:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

And then open it, go to Package Cleaner -> Clean Kernels (and obviously "Unlock" then "Clean Up"):
[IMG]http://i.imgur.com/NjQKO.png[/IMG]

---

### Post by Frogs Hair on 2011-02-02
I use Ubuntu Tweak also if you don't want the PPA you can download the .deb package from here. [http://ubuntu-tweak.com](http://ubuntu-tweak.com)

---

### Post by drewsus on 2011-02-02
Im curious, why would you ever go static deb instead of updating PPA?

---

### Post by gwu777 on 2011-02-02
> **drewsus said:**
> Im curious, why would you ever go static deb instead of updating PPA?

Very good question I wish to know the answer!

Second ubuntu tweak, used to do things manually, but UT works a charm and has a lot of tools centralised for customising your ubuntu! Give it a try...

---

### Post by drewsus on 2011-02-02
> **gwu777 said:**
> Very good question I wish to know the answer!

I completely recommend getting the PPA instead of just downloading the standalone, none updating .deb.

---

### Post by columbus2012 on 2011-02-02
Thanks guys, instant resolution as always - easy when you know how!

The link posted by mac4rfree also linked to the new grub2 clean-up page [COLOR=RoyalBlue][U][HERE]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/")

[COLOR=Black]
[/COLOR][/U][COLOR=Black]Even easier with Ubuntu Tweak !! though - am learning every day -[/COLOR][/COLOR]

---

