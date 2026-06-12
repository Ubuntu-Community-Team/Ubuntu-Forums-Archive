---
title: "Windows OS files are showing up within Ubuntu?"
date: 2011-03-12
forum: General Help
---

### Post by miltonberle on 2011-03-12
Having been interested in Ubuntu for several years, tonight I finally dual-booted Ubuntu and Vista using EasyBCD. I didn't know what to search for, so I thought I would ask: All of my windows OS files are showing as a "media volume" within Ubuntu. Is this normal? 

I have a plain vanilla dual boot install of Vista Business and Ubuntu 10.10 using an Ubuntu install disk. I pretty much used all the default settings in the GUI Ubuntu install. (Previously in Wubi, I was able to access windows files in a particular "hosts" directory, but right now I am really confused by the fact that ALL of my windows files are accessible within Ubuntu.) If anyone could enlighten me in this regard, I would greatly appreciate it!

The picture below demonstrates that all of the contents of my Windows OS C: location are accessible from within Ubuntu (is this normal for Ubuntu?):

[IMG]http://i721.photobucket.com/albums/ww217/diamondback2222/d55a424f.png[/IMG]

---

### Post by WorMzy on 2011-03-12
That "media volume" is your Windows partition, and Ubuntu has the necessary utilities to mount it. Be warned that if you attempt to delete a file on the Windows partition which Windows needs to boot/operate correctly, Ubuntu will not make any attempt to stop you. As far as Ubuntu knows, all the files on the Windows partition are up for relocation/deletion/modification, so it's up to you to know what not to touch.

If in doubt, just leave everything alone.

---

### Post by miltonberle on 2011-03-12
Okay, so it's  normal for Ubuntu to automatically mount the hard drive and Windows partition when it starts up? Thanks for the info! 

My confusion came from the fact that (a while ago) it seemed that the prevailing wisdom was that the Linux/Windows partitions were arbitrarily separate and mutually inaccessible...

---

### Post by bcbc on 2011-03-12
It's not normal for Ubuntu to mount the OS partition. In your case, your windows host is on a different partition - that is normally mounted as /host (it has to be for the wubi virtual disk to be mounted)- but unless you 
a) click on "OS" under the places menu, or 
b) have it in your fstab,
it remains unmounted. 

In previous versions you had to enter your password to mount a partition, but with the latest versions the default is to mount it (when you click on for the first time).

---

