---
title: "sharing packages on USB-flash (no internet)"
date: 2010-02-02
forum: General Help
---

### Post by julianb on 2010-02-02
I was just in Haiti, which is a challenging environment for any operating system.

People I work with were using Xubuntu thanks to some CDs that I brought. Xubuntu 9.10 was working fine but Remastersys was not working with it. It seems as though [that issue has been resolved]("http://geekconnection.org/remastersys/forums/index.php?topic=354.0").

But short of doing a remaster, do any of you have a good way of sharing packages? For instance, Jimmy downloads a program for organizing his photos and wants to give it to all his friends; they have limited access to the internet but they have USB flash drives. Is there an easy, user-friendly way for Jimmy to put "such-and-such program" on a USB flash drive in a way that allows his friends to install the program, and dependencies, from the flash drive? 

A related challenge is that we want to have a user-friendly operating system that works on a slow computer, and at the very least provides (offline) word processing capability and internet browsing capability. Anybody have experience with the new Lubuntu alpha, and how it compares to Ubuntu/Xubuntu for ease of use?

*I was in the country during the 1/12/10 earthquake; fortunately I wasn't badly hurt.

---

### Post by 2hot6ft2 on 2010-02-02
Well one way to get packages on a pc without Internet access is to go to
System>Administration>Synaptic Package Manager
select the packages you want and/or Mark All Upgrades then click on File>Generate package download script
Copy the script to a usb flash or regular drive and take it to the pc with Internet access and double click on it and select Run in Terminal

It will download all the packages to the folder where the script is.

Then take that back to the offline pc and start Synaptic and click on File>Add Downloaded Packages then point it to where the downloaded packages and script are and it will install them.

There is also another program to do it too but I don't remember the name off hand.

I have installed individual packages using the downloaded packages by double clicking the deb I wanted to install and if it needed something else (a dependency) it would be in the same folder just find it or them and install them first until all dependencies are satisfied.

Can't help with Lubuntu this is the first I've heard of it.

---

### Post by Leppie on 2010-02-02
if you download the .deb packages (or create them out of the source code on one of the machines) you can just copy them to a usb drive and install them using gdebi (just double click the packages) on the other machines.

---

### Post by 2hot6ft2 on 2010-02-02
> **Leppie said:**
> if you download the .deb packages (or create them out of the source code on one of the machines) you can just copy them to a usb drive and install them using gdebi (just double click the packages) on the other machines.
Forgot gdebi to install them.

Another option might be APTonCD it's in the repos

APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you&#8217;ve downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.

---

