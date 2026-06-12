---
title: "Empty Desktop..."
date: 2009-09-19
forum: General Help
---

### Post by kampe on 2009-09-19
Hi everybody,
 I've been using EasyPeasy1.0 for 5 months without any problem then yesterday (](*,)) I decided to remove Evolution mail (I don't use it at all) and all the related packages: after that I didn't notice anything strange on my laptop.
This morning when I switched it on (first time after removing those packages) I got a blue desktop with the mouse pointer in the middle and nothing else...no files on desktop, no task bars or icons....
I've tried several times to run apt-get update from the recovery mode but  I get this message:
"Unable to fetch some archives maybe run apt-get update or try with --fix-missing?"

Any ideas!?!?
Thanks in advance!

---

### Post by marcopolo1981 on 2009-09-19
Try 

apt-get update --fix-missing

If that doesn't work, I recommend re-installing evolution and checking what it wants to automatically remove the next time you want to uninstall it.

---

### Post by wojox on 2009-09-19
You need to reinstall evolution-data-server and evolution-data-server-common
 as gnome uses these packages else where.

---

### Post by kampe on 2009-09-19
> **marcopolo1981 said:**
> Try 

apt-get update --fix-missing

If that doesn't work, I recommend re-installing evolution and checking what it wants to automatically remove the next time you want to uninstall it.

When i run apt-get update --fix-missing it says:

g could not resolve "ca.archive.ubuntu.com"
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/intrepid-updates/release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/intrepid-updates/release.gpg) Could not resolve "ca.archive.ubuntu.com"
W: Failed to....
W: Failed to....
.
.
.
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

I also tried to reinstall evolution with:

apt-get install evolution

I get

After this operation 122MB of additional disk space will be used.
Do you want to continue? (Y/n)

I say Y but then again:

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I'm so hopeless......:(

---

### Post by kampe on 2009-09-19
> **wojox said:**
> You need to reinstall evolution-data-server and evolution-data-server-common
 as gnome uses these packages else where.

I tried both, but I always get the same result:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.24.3-Oubuntu1-i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.24.3-Oubuntu1-i386.deb) Could not resolve "ca.archive.ubuntu.com"
Failed to fetch.....
Failed to fetch...
.
.
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by marcopolo1981 on 2009-09-20
It seems like there might be repo's missing from your apt-get update.

Run

sudo gedit /etc/apt/sources.list

And check that important repos aren't commented out (start of line has #).
If they are commented out, remove the #, save and close the file.
When back at the prompt, run

sudo apt-get update

again to see if you have fixed it.

If gedtit fails, it may be because important files were removed when you uninstalled evolution. In that case, substitute the word gedit with nano.

I am assuming you are running 9.04, so I will install that version and tell you what it *should* say by default. I will post back with my output this afternoon sometime.

Regards

Mark

---

### Post by 3rdalbum on 2009-09-20
Connect your computer to a network via Ethernet cable and run those commands again. From the sounds of it, Network Manager is not running.

---

### Post by kampe on 2009-09-21
Hey guys! Finally I managed to fix it!! 

So, first of all I connected the notebook to the network via cable....I realized that when I was trying to run update or install commands evolution it was not connected!! :oops:

Then I run apt-get update and I also reinstalled evolution but nothig seemed to work, the problem was still there!

Finally I found somewhere on internet a guy with my same problem, saying it was due the absence of the Ubuntu-desktop package...
I run install ubuntu-desktop.....and that's it, now it's working again! :P

I'm still thinking about how the package disappeared from my laptop (is it somehow related to evolution!?!)...but I can't find a likely unswer! :lolflag:
Thanks everybody for your help, I appreciate it!!

---

### Post by j7%&lt;RmUg on 2009-09-21
When you uninstall evolution it also removes ubuntu-desktop(dont ask me why), when you go to reinstall evolution it does not need ubuntu-desktop and so doesnt reinstall it, thus you have to reinstall uubuntu-desktop manually.

---

### Post by marcopolo1981 on 2009-09-25
Sorry I didn't get back to you with the default repos - glad they weren't needed! After installing 9.04, I had some issues - one of which was the internet. Not the laptop, the ISP.

Ubuntu-dektop is only a meta package. Reinstalling this will install all packages associated with it, so you don't have to manually install each individial package. 
I'm pretty sure that gnome-panel was the culprit. It is automatically uninstalled with some evolution files, and reinstalled with the ubuntu-desktop meta package.
If you are now happy that this problem is resolved, please mark it as so. Thanks.

Mark

---

### Post by Robert.Zapata on 2009-10-09
> **kampe said:**
> Hey guys! Finally I managed to fix it!! 

So, first of all I connected the notebook to the network via cable....I realized that when I was trying to run update or install commands evolution it was not connected!! :oops:

Then I run apt-get update and I also reinstalled evolution but nothig seemed to work, the problem was still there!

Finally I found somewhere on internet a guy with my same problem, saying it was due the absence of the Ubuntu-desktop package...
I run **install ubuntu-desktop.....**and that's it, now it's working again! :P

I'm still thinking about how the package disappeared from my laptop (is it somehow related to evolution!?!)...but I can't find a likely unswer! :lolflag:
Thanks everybody for your help, I appreciate it!!

Hello Team:

I just made the same mistake..!!! Remove Evolution and check for removal a lot of options in Synaptic. After reading this thread my question is what do I need to put for the **"SOURCE DESTINATION"**


Thank you very much.

---

### Post by Robert.Zapata on 2009-10-10
UPDATE:


After running **"sudo apt-get install ubuntu-desktop"**

Seems to fixed the issue but after re-booting goes to the same. Re-installing right now from scratch

---

