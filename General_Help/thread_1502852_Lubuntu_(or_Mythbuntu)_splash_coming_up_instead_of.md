---
title: "Lubuntu (or Mythbuntu) splash coming up instead of Ubuntu - plymouth error"
date: 2010-06-06
forum: General Help
---

### Post by NUboon2Age on 2010-06-06
Just wanted to post this fix so that others might find it more easily.  I've got 10.04 which i souped up by manually upgrading to Studio, and along the way i started getting Lubuntu splash instead of my Ubuntu splash.  I got this help from the #ubuntu and #ubuntu-beginners irc channels (acerimmer & ActionParsnip thanks!)
```
sudo update-alternatives --config default.plymouth
```
and afterwards I guess sometimes (not sure why/when) this is needed:
```
sudo update-initramfs -u
```
and was able to get the logout splash get back to Ubuntu, but boot up was still Lubuntu.

With a huge amount of googling and experimenting I finally found 
[http://ubuntuforums.org/showthread.php?t=1441464](http://ubuntuforums.org/showthread.php?t=1441464)

It turns out there's a bug
[https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237](https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237)

Here's the workaround:
```
***For anyone hit by this bug you will need to manually install the package:
plymouth-theme-ubuntu-text

And then remove these packages:
lubuntu-plymouth-theme
mythbuntu-default-settings

***If you are stuck with a black desktop after boot:
Switch over to a terminal via CTRL+ALT+F2

Login and run the commands:
sudo aptitude remove mythbuntu-default-settings
sudo aptitude install plymouth-theme-ubuntu-text
(above command will also auto-remove several xfce-related packages)

and finally reboot.
``` 

Now my Ubuntu is all happy again.:popcorn:

---

