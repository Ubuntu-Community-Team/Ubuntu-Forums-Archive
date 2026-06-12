---
title: "There is something horribly wrong"
date: 2006-02-07
forum: General Help
---

### Post by Baikonur on 2006-02-07
Today, I have tried to install Kubuntu 5.10 three times. First, i368 (kubuntu-5.10-install-i386.iso) from the Swedish mirror from [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php). The MD5 was fine. I burned it on a cd, then tried install it, and in the start it went all fine. But then when it was installing the base system, about halfway throught it gave me an error saying that it had no kernel to install. So, it wouldn't install, and i aborted the installation. 

I figured it must have been a flawed cd or something. I burned it again, on a different brand cd, and tried to install, and it did exactly the same. Well, i figured, most have been a flawed file or something, even thought the MD5 was like it's supposed to. So i downloaded it again, this time from the Korean mirror. Burned it, tried to install it, and it did once again exactly the same.

So, could someone tell me what on earth is going on?

(btw. Ubuntu 5.04 both installs and works just fine)

---

### Post by byen on 2006-02-07
which cd-burner are you using? If you are using Windows I would strongly suggest [Deepburner]("http://www.download.com/DeepBurner/3000-2646_4-10447242.html?tag=tab_pub") for burning ISO cds and try using a lower write speed.
hope it helps. Goodluck!

---

### Post by Baikonur on 2006-02-07
I used UltraIso with 52x, 32x and then 16x.

---

### Post by byen on 2006-02-07
Usually for the error " no kernel to install" I would have said that it is an incomplete or a corrupted installation. But since you say the integrity was checked and confirmed...it would have to be the cd-write issue.. why not try the burner that I suggested. I have used it..its free and safe.

---

### Post by Baikonur on 2006-02-07
Well, I tried once more with the UltraIso, this time with 4x, once more I got the same result. I decided to check the integrity again, and it was fine. I tried it with the DeepBurner at 4x, results were exactly like with the UltraIso.

---

### Post by moopere on 2006-02-07
[QUOTE=Baikonur]Today, I have tried to install Kubuntu 5.10 three times. First, i368 (kubuntu-5.10-install-i386.iso) from the Swedish mirror from [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php). The MD5 was fine. I burned it on a cd, then tried install it, and in the start it went all fine. But then when it was installing the base system, about halfway throught it gave me an error saying that it had no kernel to install. So, it wouldn't install, and i aborted the installation. 

I figured it must have been a flawed cd or something. I burned it again, on a different brand cd, and tried to install, and it did exactly the same. Well, i figured, most have been a flawed file or something, even thought the MD5 was like it's supposed to. So i downloaded it again, this time from the Korean mirror. Burned it, tried to install it, and it did once again exactly the same.

So, could someone tell me what on earth is going on?

(btw. Ubuntu 5.04 both installs and works just fine)[/QUOTE]

You won't believe it, because I certainly didn't, but its a bad burn - I got exactly this (no kernel thingy) after downloading the ISO (with good MD5) 3 times and burning to the same CD-RW disc a dozen times (verbatim 700MB 24X), after fiddling and fiddling and fiddling I eventually, for no well thought out reason swapped the Verbatim for a Mitsubishi 650MB 4x CD-RW and it worked right away (!!!).

Talk about frustrating.  I burned the verbatim first under gnome-baker then under Windows - Nero, no good either way.

I suspect in the end it wasn't the brand name but the speed at which it was burned.

Cheers,
Craig

---

### Post by Baikonur on 2006-02-08
Well, you're right there, I do find it hard to believe :)

I've burned it on 6 different CDs now, last 3 of which have been with 2 different isos (both having good MD5), 2 different burning software and 2 different brands of CDs, all burned 4x, and still, same result.

---

### Post by jackrabbit123 on 2006-02-08
I don't know if this will work, but if you can boot from a USB device try:
'dd if=/path/to/iso of=/dev/sdx1'
where x is whatever letter your usb stick turns up as.  Again I don't know if it'll work but it's worth a shot.  BTW this will destroy whatever filesystem you already have on your usb stick so make sure you back it up first.
Chris

---

### Post by newuser111 on 2006-02-08
your cds are probably fine, unplug any unnecessary USB peripherals and turn off your printer before starting the install

try "linux acpi=off" at the install prompt

---

### Post by Baikonur on 2006-02-08
I can safely say that the two that are in pieces aren't fine :)

Well, thanks for the help so far, I'll have to try those when I get home.

---

### Post by Baikonur on 2006-02-08
Nope. Didn't work. Tried with no other usb-stuff than mouse, and with 'linux acpi=off'.

Results you can guess.

But I don't think it's the CDs, my roommate burned me one too, and there was no difference.

---

### Post by shakin on 2006-02-08
[QUOTE=Baikonur]Nope. Didn't work. Tried with no other usb-stuff than mouse, and with 'linux acpi=off'.

Results you can guess.

But I don't think it's the CDs, my roommate burned me one too, and there was no difference.[/QUOTE]

Can you try the install on your roommate's computer? Maybe put your hard drive in his computer temporarily just to see if it works.

You might also want to try using the LiveCD's memcheck boot option to see if you have bad RAM. I've definitely seen a bad stick of RAM cause installation issues even though once installed the system works fine.

---

### Post by Baikonur on 2006-02-08
Nope, he has a laptop so i won't be getting my hard drive in it. But anyways, I tried to install Ubuntu 5.04, and it installed just fine and seems to be working ok too.

---

### Post by Baikonur on 2006-02-10
Mmm, can't get Kubuntu (or Ubuntu) Breezy to install, seems like I'll be changing  distro, even though Ubuntu is the only one I'm familiar with at all.

---

### Post by newuser111 on 2006-02-10
but file a bug with your hardware specs at least, since its weird that hoary installs but breezy didnt

[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by Baikonur on 2006-02-10
Can't file the bug, since the bug reporting tool doesn't seem to function, it gives me an "Oops" when I try to add the report :)

---

