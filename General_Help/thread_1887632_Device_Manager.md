---
title: "Device Manager"
date: 2011-11-27
forum: General Help
---

### Post by biggjerryc on 2011-11-27
My teacher for school has asked us to install a Device Manager in Ubuntu 11.10. It has to be similar to the one in windows and it is NOT the storage device manager. Does anyone have a clue as to what I should be looking for. I have been searching and trying random things for over three hours now and cannot figure it out.

From my research, it has been removed from the synaptic package manager.

the screen should look like this...
[IMG]http://i10.photobucket.com/albums/a104/BiggJerryC/IMAG0123.jpg[/IMG]

---

### Post by Corporation on 2011-11-27
I think that can be installed from terminal:

sudo apt-get install gnome-device-manager

---

### Post by biggjerryc on 2011-11-27
tried that,it doesnt work. I think that worked on previous versions of Ubuntu

---

### Post by oldtimer7777 on 2011-11-27
> **biggjerryc said:**
> tried that,it doesnt work. I think that worked on previous versions of Ubuntu

I would try installing a previous version of Ubuntu where it works for now.

---

### Post by linuxnoob47 on 2011-11-27
I think our teacher is wasting our time to tell you the truth

---

### Post by linuxnoob47 on 2011-11-27
> **Corporation said:**
> I think that can be installed from terminal:

sudo apt-get install gnome-device-manager


this is what you get when trying to install in terminal

larry@larry-System-Product-Name:~$ sudo apt-get install gnome-device-manager
[sudo] password for larry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-device-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-device-manager' has no installation candidate
larry@larry-System-Product-Name:~$

---

### Post by oldtimer7777 on 2011-11-27
Why doesn't the instructor just use the previous version of Ubuntu where this can be achieved successfully??

That instructor must really not like you guys for some reason. I wonder why.. lol

> **linuxnoob47 said:**
> this is what you get when trying to install in terminal

larry@larry-System-Product-Name:~$ sudo apt-get install gnome-device-manager
[sudo] password for larry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-device-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-device-manager' has no installation candidate
larry@larry-System-Product-Name:~$

---

### Post by biggjerryc on 2011-11-27
He probably said don't get frustrated thinking that we were going to beat ourselves up about it all weekend and NEVER figure it out because it is impossible. Well.. I quit.

---

### Post by oldtimer7777 on 2011-11-27
> **biggjerryc said:**
> He probably said don't get frustrated thinking that we were going to beat ourselves up about it all weekend and NEVER figure it out because it is impossible. Well.. I quit.

The ability of a student to be able to talk to their instructor is a clear example of someone who is willing to teach or not. And besides they get paid tenure, we don't.

Sometimes the question is just wrong. :)  Goodluck.

---

### Post by nowifi on 2012-02-19
well ... for resourcefulness to solve a problem plagiarism may or may not be acceptable  ... in any case **[COLOR=Blue]gnome-device-manager[/COLOR]** does not run in isolation but is dependent on **[COLOR=Blue]hal[/COLOR]** (Hardware Abstraction Layer) - 

This is a very blatant hint that the resolution to this problem is not just click'n'pick.

There have been many postings referring to this difficulty w/o any published solutions.

While **[COLOR=Blue]gnome-device-manager[/COLOR]** automatically resolves and loads [COLOR=Blue]**libgnome-device-manager0**[/COLOR] there are other bindings that it is dependent on.

Specifically from a raw 10.04 lucid install it will be necessary to update some of:
```
[COLOR=Blue][B]
/hal/hal_0.5.14-0ubuntu6_i386.deb
/hal-info/hal-info_20091130-1_all.deb
/hal/libhal-storage1_0.5.14-0ubuntu6_i386.deb
/hal/libhal1_0.5.14-0ubuntu6_i386.deb[/B][/COLOR]

```(ie. **[COLOR=Blue]hal[/COLOR]**, **[COLOR=Blue]hal-info[/COLOR]**, **[COLOR=Blue]libhal-storage1[/COLOR]**, **[COLOR=Blue]libhal1[/COLOR]**)
and easily done in Synaptic Package Manager by searching for "hardware abstraction" and updating the packages above as required.

An alternative package, **[COLOR=Blue]hardinfo[/COLOR]**, is not based on HAL and can be useful too.

---

