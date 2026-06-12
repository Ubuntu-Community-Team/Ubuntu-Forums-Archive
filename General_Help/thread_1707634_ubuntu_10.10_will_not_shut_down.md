---
title: "ubuntu 10.10 will not shut down"
date: 2011-03-15
forum: General Help
---

### Post by harlie on 2011-03-15
I have posted this before but still have no answer here it is again.
I am using ubuntu 10.10 dual booting with microsoft windows.
windows will shut down computer on command 
ubuntu will not shut down computer no matter what is tried.
I have a  HP Pavillion Elite HPE using GNOME 2.32.0 (ubuntu 2010-09-27
kernel is linux 2.6.35-25 generic-pae
platform is i686
cpu is AMD Phenom IIx6 1045

problem solved   trouble was a LAN setting in the setup or bios section when I set it to disabled the problem went away
thanks to the person who suggested this.

---

### Post by WlaadDyaab on 2011-03-15
> **harlie said:**
> I have posted this before but still have no answer here it is again.
I am using ubuntu 10.10 dual booting with microsoft windows.
windows will shut down computer on command 
ubuntu will not shut down computer no matter what is tried.
I have a  HP Pavillion Elite HPE using GNOME 2.32.0 (ubuntu 2010-09-27
kernel is linux 2.6.35-25 generic-pae
platform is i686
cpu is AMD Phenom IIx6 1045
 
Have you tried to use command line in Terminal to shut down your system?

Try this:

Open Terminal: Applications > Accessories > Terminal (short cut: ctrl + alt + T)

Copy/paste this code > sudo shutdown now -h

Then type your password (it wont show) then press "Enter" (or the "return" key)

---

### Post by harlie on 2011-03-15
yes I tried this and it will not shut down

PROBLEM  SOLVED

---

### Post by harlie on 2011-03-15
> **WlaadDyaab said:**
> Have you tried to use command line in Terminal to shut down your system?

Try this:

Open Terminal: Applications > Accessories > Terminal (short cut: ctrl + alt + T)

Copy/paste this code 

Then type your password (it wont show) then press "Enter" (or the "return" key)

yes I TRIED THIS AND IT DOES  NoT WORK IT ONLY REBOOTS

PROBLEM  SOLVED

---

### Post by WlaadDyaab on 2011-03-15
> **harlie said:**
> yes I tried this and it will not shut down

Do you run any program in order for Ubuntu not to shut down?

---

### Post by antaios256 on 2011-03-15
it almost sounds as if he has a BIOS setting to power on network traffic. does this sound familiar / do you use LAN as apposed to Wireless

---

### Post by harlie on 2011-03-15
> **antaios256 said:**
> it almost sounds as if he has a BIOS setting to power on network traffic. does this sound familiar / do you use LAN as apposed to Wireless


no I don't use a lan    btw I am a beginner and not on a network

PROBLEM  SOLVED

---

### Post by harlie on 2011-03-15
> **WlaadDyaab said:**
> Do you run any program in order for Ubuntu not to shut down?


no any thing I run makes no difference just ubuntu in general

PROBLEM  SOLVED

---

### Post by complience on 2011-03-17
I'm having the same problem and have done for a while.

I can restart without problem, but a full shutdown is impossible.

I think its somthing to do with communication between Ubuntu and the PSU.

any help troubleshooting this problem?

---

### Post by supershin on 2011-03-17
Did you update it recently? Could be an update broke something.

---

### Post by shane2peru on 2011-03-17
I had this problem before, I think it turned out there was a BIOS update that I had to do.  That finally fixed it.  I just hit the power button on the laptop when it started to boot back up.  It was a real annoyance, but after a while I got in the habit of hitting the powerbutton at the end of the powerdown cycle.  Possible a BIOS issue.  

Shane

---

### Post by complience on 2011-03-17
i updated my bios to the very latest version a few weeks ago..
no change.

---

### Post by shane2peru on 2011-03-17
I'm not sure if this will help you out, but try this:
```
sudo poweroff
```  and see if that works.  I don't remember some of the other stuff I tried, but it was a pain.  Hope that will help!

Shane

---

### Post by complience on 2011-03-17
Thanks I've tried both shutdown & poweroff -h now
neither work

On shutting down i get the error

* unmounting local filesystems 

/ is busy

System will now halt
(then it hangs)

Sorry I can't give you the exact error but I don't seem to have any logging of my shutdown process even tho ive activated it.

i've also tried deactivating my apci support as suggested in this blog post .. again it didn't work

[http://www.brighthub.com/computing/linux/articles/39504.aspx](http://www.brighthub.com/computing/linux/articles/39504.aspx)

---

### Post by harlie on 2011-03-18
> **supershin said:**
> Did you update it recently? Could be an update broke something.


thanks, no it has been unable to shut down ever since it was installed it reboots and nothing will make it shut down except to open windows 7 and shut down from there

---

### Post by harlie on 2011-03-18
> **shane2peru said:**
> I'm not sure if this will help you out, but try this:
```
sudo poweroff
```  and see if that works.  I don't remember some of the other stuff I tried, but it was a pain.  Hope that will help!

Shane


thanks I will try it

---

### Post by thenickrulz on 2011-03-18
I have the same problem help me on my thread...
[http://ubuntuforums.org/showthread.php?p=10575468#post10575](http://ubuntuforums.org/showthread.php?p=10575468#post10575) 
Cheers TNR:p:D
Ps Very annoying issue

---

### Post by harlie on 2011-03-19
> **harlie said:**
> thanks I will try it


tried it no luck

---

