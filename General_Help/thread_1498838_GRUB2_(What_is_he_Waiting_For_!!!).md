---
title: "GRUB2 (What is he Waiting For ?!!!)"
date: 2010-06-01
forum: General Help
---

### Post by tlbuntu on 2010-06-01
Hello
I recently updated my ubuntu 10.4 with a couple of recommended updates then shutdown and surprised by the next boot with a blinking dash that infinitely blinked without sending error messages or even making beeps so I Googled a bit to find the most reasonable solution which is to reinstall grub2 so I booted the Live CD opened a terminal and typed 
```
sudo grub-install /dev/sda3
``` and got only an error complains about not auto detecting file system modules blah blah googled it and got other 4 error that im crossing whatever it is and it doesn't use UUIDs googled and got nothing so i hope somebody here will actually help to restore the whole grub2 thing without reformatting the whole Ehdd again,I've been troubleshooting for a day and I can't spend more time on this so if I can't restore it for some reason then how I can boot my system again and replacing it with another boot-loader you know guys HELLLP!!
---------------------------------------------------------------------------------------------------------
Thanks For The Open Source Community Who Gave Us Our Freedom

---

### Post by dino99 on 2010-06-01
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by tlbuntu on 2010-06-01
Reinstalling Ubuntu is Not A Possibility for Me anyway thx

---

### Post by stinkeye on 2010-06-01
> **tlbuntu said:**
> Hello
I recently updated my ubuntu 10.4 with a couple of recommended updates then shutdown and surprised by the next boot with a blinking dash that infinitely blinked without sending error messages or even making beeps so I Googled a bit to find the most reasonable solution which is to reinstall grub2 so I booted the Live CD opened a terminal and typed 
```
sudo grub-install /dev/sda3
``` and got only an error complains about not auto detecting file system modules blah blah googled it and got other 4 error that im crossing whatever it is and it doesn't use UUIDs googled and got nothing so i hope somebody here will actually help to restore the whole grub2 thing without reformatting the whole Ehdd again,I've been troubleshooting for a day and I can't spend more time on this so if I can't restore it for some reason then how I can boot my system again and replacing it with another boot-loader you know guys HELLLP!!
---------------------------------------------------------------------------------------------------------
Thanks For The Open Source Community Who Gave Us Our Freedom

[**_[COLOR="DarkRed"]The Grub 2 Guide[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=7505203&postcount=1")

---

### Post by tlbuntu on 2010-06-01
Well The Problem is Now Solved I Restored Grub What I had to do is 
```
sudo umount --a
```
```
sudo mount /dev/sda3 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda 
```
And Now Back Online Thanks For You And All Open Source Developers

---

