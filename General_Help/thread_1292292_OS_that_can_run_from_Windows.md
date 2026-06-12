---
title: "OS that can run from Windows"
date: 2009-10-15
forum: General Help
---

### Post by Solarium on 2009-10-15
Hi guys,

I got some free time on my hands, and i wanted to try some operating systems that i can run directly from windows.

I dont want the hustle of partitioning and going thru the install nor do i want to use virtual machines, so if any one has any sugestions  i would love to hear .

---

### Post by SuperSonic4 on 2009-10-15
ubuntu works fine in wubi

don't know how exactly - try inserting the disc and seeing what happens

---

### Post by Niko Johnson on 2009-10-15
yeah you can always try out live CD's... i think that is the best way to try out new operating systems.. just download the iso burn it to a CD and boot off it. thats a pretty easy hassle free way to test out new O.S's

---

### Post by andymorton on 2009-10-15
You can install Ubuntu as a windows programme. You don't need to burn a CD. Just download the file and then install. 

[http://wubi-installer.org/](http://wubi-installer.org/)


andy 
:)

---

### Post by bodhi.zazen on 2009-10-15
wubi is dual booting still.

If you want to run Linux within Windows, use somethign like VirtualBox or VMWare.

---

### Post by CatKiller on 2009-10-15
> **Solarium said:**
>  I dont want the hustle of partitioning and going thru the install nor do i want to use virtual machines.

You've not really left yourself much of an option there, have you? Operating Systems aren't just applications, you know. The options boil down exactly to running one OS at a time (dual boot) or running one OS inside another (virtualisation). That's it. You're going to have to get your hands dirty at some point, or just ditch the idea completely.

There is no option that will let you run another OS inside Windows without virtualisation. By definition. So that's out.

The only way to run an OS without installing it is from a live environment - live CD or live USB. Neither of these are "directly from Windows." The live environment is the exclusive environment, and your Windows environment isn't touched at all. That's more-or-less the point.

Or you can install with Wubi, which is a standard install except that it installs to a virtual filesystem inside files on your existing Windows partition and the install process runs within the Windows environment. You're still dual-booting, as bodhi.zazen says, meaning that you'll be running a Linux environment instead of Windows whenever you boot into Ubuntu. You can uninstall Ubuntu as if it were a Windows application, which should remove the files you've created and restore the bootloader to its previous state.

---

### Post by karimruan on 2009-10-18
I think what he is looking for is a linux based OS that is as easy to dual boot as ubuntu is, with the wubi installer. TO answer the question, i believe that might be linux mint, which is based off of ubuntu. I also know that linspire and freespire are now based off of ubuntu, but do not know if they offer the same level of ease as ubuntu when setting up a windows/ubuntu dual boot. I am curious too, what other *nix OS allow you to install as a dual boot like ubuntu does with the wubi installer?

---

### Post by brett- on 2009-10-18
I think you should stick with Windows.

---

### Post by SlickRick on 2009-10-18
I think you should try [unetbootin]("http://unetbootin.sourceforge.net/"). It can install any linux iso onto a usb flash drive to use as a live cd. You can use this if you don't feel like wasting loads of CDs.

> **brett- said:**
> I think you should stick with Windows.

I don't think that would accomplish spending your free time testing out linux.

---

### Post by mechro on 2009-10-18
Some of these should work...

[http://www.worldofspectrum.org/emulators.html](http://www.worldofspectrum.org/emulators.html)

---

### Post by brett- on 2009-10-19
> **SlickRick said:**
> I think you should try [unetbootin]("http://unetbootin.sourceforge.net/"). It can install any linux iso onto a usb flash drive to use as a live cd. You can use this if you don't feel like wasting loads of CDs.



I don't think that would accomplish spending your free time testing out linux.


I was drunk, sorry.:guitar:

---

### Post by karimruan on 2009-10-19
> **brett- said:**
> I think you should stick with Windows.

But he said he wants to prove that a quality rap album can be produced on linux, and it can! You just have to do your research! And maybe buy a commercial linux DAW.

Besides, Reasons and Pro Tools are $250 +, and not everybody can swing that without the help of a label or a third job.

If you are a good producer, you can work with anything. I used to make electronica and my first and second album (both on amazon.com) did fairly well for my lack of marketing.

I know that linux still has a ways to go to contend with her closed source, proprietary OS competitors, but she has alot to offer.

---

