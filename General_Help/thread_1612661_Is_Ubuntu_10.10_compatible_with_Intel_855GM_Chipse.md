---
title: "Is Ubuntu 10.10 compatible with Intel 855GM Chipsets?"
date: 2010-11-03
forum: General Help
---

### Post by CharlesWelsh on 2010-11-03
Hello, I have a Toshiba Satellite A15- S1292 Laptop with the latest Ubuntu installed :D! Problems still persist as the naked eye can see.. however I am curious as to if any experienced users would be able to help me enable the drivers WITHOUT negatively affecting my system. I am not the most intelligent of users.. That's why I am posting this in the user friendly Ubuntu Forums. ANY help would be greatly appreciated just PLEASE do not send me down the wrong path. I have had this laptop for quite some time and i was happy to see that this Release of Ubuntu installed flawlessly. However graphically due to the drivers being disabled I am dissapointed as usual. Thanks in advance.

~CJ

---

### Post by CharlesWelsh on 2010-11-03
Bump ^^

---

### Post by janpol on 2010-11-03
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1464239]("http://ubuntuforums.org/showthread.php?t=1464239")

Hope it helps!

---

### Post by CharlesWelsh on 2010-11-03
Seems promising.. :( However that is for Lucid.. would it make a difference on 10.10? I just dont want to get my computer to where i cannot fix it. I'm illiterate when it comes to Ubuntu.

---

### Post by Rubi1200 on 2010-11-03
The 855GM works out-of-the-box so to speak on 10.10

However, some caveats:

1. Compiz does not work

2. there are persistent CPU spikes that affect usability

Now, wait for it:
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

The fix on 10.10 is basically the same as for 10.04!

I have only just started testing this, so I am not willing to give you a definitive answer as to whether it is really a decent workaround.

I will post with more information as I continue my own tests.

In any event, it might be worth trying it for yourself.

---

### Post by CharlesWelsh on 2010-11-03
Okay.. So forgive the seemingly pointless questions.. First off.. i ran these commands.. because i was told to..

```
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update && sudo apt-get upgrade

```

Then..
```
sudo gedit /etc/X11/xorg.conf
```
and paste ```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Than i do this? ->
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"


in /etc/default/grub 

Then I reboot and im done? Im just checking before i do all of this to be SURE. Thank you.

---

### Post by Rubi1200 on 2010-11-03
If you are talking about in 10.10, then the answer is no.

First enable the Intel driver:
> To enable the Intel driver you need to create a file called /etc/X11/xorg.conf containing the following: 
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Then run the following commands:
```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade
sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms
```
There is no need to edit the /etc/default/grub file on 10.10 for this to work.

Also, further testing has revealed that although Compiz now supposedly works with this fix, in fact it causes all kinds of weird freezes and other unusual and undesirable effects (menus blanked out, right-click not working etc).

My advice is to not use Compiz at all on 10.10 with the 855GM chipset.

However, the CPU spikes that I mentioned before *seem* to have disappeared. I need to test this more to give you a better answer though.

---

### Post by CharlesWelsh on 2010-11-03
Well :] Good news ladies and Gents.. My Fn keys now work flawlessly.. faster boot believe it or not.. No CPU spikes YET. However i try to enable graphics.. and it searches for drivers. It seems to go through however i cannot see any of my windows. thus eventually reverting to "None"
Any help would be appreciated.

---

### Post by CharlesWelsh on 2010-11-03
That works for me. Thank you for all of your help. It seems Canonical has come a long way integrating these chipsets into their software compatibility. This is a huge and much appreciated step. Thank you again.

---

### Post by Rubi1200 on 2010-11-03
You are more than welcome :)

Enjoy!

---

### Post by javiermorale on 2010-12-14
I am afraid to inform you that 3d and visual effects, compiz, etc. won't be able to be fully functional in old chip-sets such as Intel 855gm graphic card. I've one myself in a X40 IBM device and after installed previous Ubuntu releases and patches, creating xorg.conf files and change from distros. Nothing, I mean nothing works, apart from 8.04 or older version of Ubuntu. It's a bug reported and not fixed yet!! Suse 11.3 has the same problem although I've not tried Fedora 14 It seems the same! Sorry to be so realistic but it is disappointing..

---

