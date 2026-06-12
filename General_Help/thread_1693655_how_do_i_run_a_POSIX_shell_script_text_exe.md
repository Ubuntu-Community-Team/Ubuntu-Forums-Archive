---
title: "how do i run a POSIX shell script text exe"
date: 2011-02-23
forum: General Help
---

### Post by jezzyjez on 2011-02-23
I am trying to install the below file.

[email]jez@jez-Studio-1537:~/.gvfs/matu20Xa.iso[/email]$ file install
install: POSIX shell script text executable


Which command do I need to use to run it?

I have tried, run, open, % , install and none of them work

Bit of a n00b question I know but if anyone could help that would be great

:D

Jez

---

### Post by mciverza on 2011-02-23
> **jezzyjez said:**
> I am trying to install the below file.

[email]jez@jez-Studio-1537:~/.gvfs/matu20Xa.iso[/email]
Jez

Hi Jez

That looks like an .ISO file (ie a CD/DVD image). Those files can be 'mounted' (ie attached to your system) just as if they were real CDs.

The file you want to install is presumably on the "CD".

If you install package "fuseiso" (from System --> Administration -->Synaptic ....) then you should be able to double-click to "open" any ISO file.

What are you trying to install?  (am trying to pre-empt a possible 'wrong way' of doing things in ubuntu)

Safe computing

---

### Post by jezzyjez on 2011-02-23
ok before I mounted the iso using achivemounter.

But after your advice installed fuseiso then doubleclicked this just opened the file in xfburner.

It is a MATLAB iso I received from a colleague.

The readme.txt states to run the install file in the iso

Jez

---

### Post by jezzyjez on 2011-02-23
Ok problem solved, the problem was that I was mounting it as a drive and not as a disk. Fuseiso didnt work for me so I installed Gmount-iso

Once Mounting with this it was possible to run the install file as an executable

---

