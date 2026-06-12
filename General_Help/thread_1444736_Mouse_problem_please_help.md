---
title: "Mouse problem please help"
date: 2010-04-01
forum: General Help
---

### Post by aaronlopez9210 on 2010-04-01
when i go to use kubuntu on use without making changes or install, my mouse doesnt work, basically whenever i have to use my mouse or keyboard(other than main screen when you select install) it does not work....PLEASE HELP!!

---

### Post by colorlessprism on 2010-04-01
i know when i first upgraded to ubuntu 9.10 i could not use ANY usb components when the webcam was on, but i am on a netbook so ymmv. i had to disable my webcam, install, reboot, run update, enable webcam, run update again. unfortunately this is my only suggestion. good luck

---

### Post by aaronlopez9210 on 2010-04-01
i have a laptop, i cant not use my mouse

---

### Post by colorlessprism on 2010-04-01
is the mouse usb or your touchpad? the keyboard does not work either?i know the things were working when you were using a LiveCD so it makes me wonder why after install nothing works. i would check the known release notes page (im guessing your using 9.10) to see if there are any known issues:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

you might also check and see if there is a "hardware support" page. i found one some time ago for my MSI Wind:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

you might post what kind of laptop you have along with the version of kubuntu you're installing and what method (i.e. usb flash drive, CD, etc).

---

### Post by aaronlopez9210 on 2010-04-02
> **colorlessprism said:**
> is the mouse usb or your touchpad? the keyboard does not work either?i know the things were working when you were using a LiveCD so it makes me wonder why after install nothing works. i would check the known release notes page (im guessing your using 9.10) to see if there are any known issues:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

you might also check and see if there is a "hardware support" page. i found one some time ago for my MSI Wind:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

you might post what kind of laptop you have along with the version of kubuntu you're installing and what method (i.e. usb flash drive, CD, etc).


i never got to install it, for example....i would click use without making changes to your computer, and after it would finish loading and go to the desktop i cant move the mouse or use the keyboard. 
same scenario for when I would click install, when it loaded to the screen where i had to press NEXT i couldnt move the mouse or use the keyboard....
(for both scenarios the lights on my keyboard dont even turn on; numlock;capslock)

i have a
Toshiba Satellite Laptop
AMD 
Windows 7
Trying to install Kubuntu 9.10

THIS PROBLEM IS NOT YET SOLVED PLEASE HELP

---

### Post by colorlessprism on 2010-04-02
i am sorry you are still having problems, its really hard to make a switch when simple things dont work.  it looks like this is a known bug ([#89113]("https://bugs.launchpad.net/ubuntu/+source/laptop-detect/+bug/89113") / [#40503]("https://bugs.launchpad.net/ubuntu/+source/laptop-detect/+bug/40503")) so you are not alone. it seems a number of people have been able to run "dpkg-reconfigure xserver-xorg" from the terminal and their touchpad starts working again. you may need to get a usb mouse and keyboard...good luck

---

