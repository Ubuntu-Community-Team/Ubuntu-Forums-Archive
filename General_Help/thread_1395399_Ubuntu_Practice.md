---
title: "Ubuntu Practice"
date: 2010-01-31
forum: General Help
---

### Post by tolinrome on 2010-01-31
Been fooling around with Ubuntu for a while and was wondering how I can get some practice with it.
Any free tutorials or exercises on using commands with the terminal and other basic stuff?

Also, what's the difference with Ubuntu and Ubuntu server?
How is Ubuntu different than Unix and Linux?

I was thinking of putting an Ubuntu server in my windows environment - can it be part of AD? What are the advantages?
Thanks!!!
New to Ubuntu and loving it.

---

### Post by rogue_0111 on 2010-01-31
> **tolinrome said:**
> Been fooling around with Ubuntu for a but and was wondering how I can get some practice with it.
Any free tutorials or exercises on using commands with the terminal and other basic stuff?

New to Ubuntu and loving it.

Check out:
[http://ubuntuclips.org/index.html](http://ubuntuclips.org/index.html)

--

---

### Post by t4thfavor on 2010-01-31
Ubuntu is Linux + apps, Linux is Unix-like. 

ubuntu server is the ubuntu OS without a bunch of gui and other needless apps, it comes with the bare essentials--

It also has a slightly different kernel that has different compile time options.

---

### Post by Robster2 on 2010-01-31
I'd start with the free PDF pocket guide

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

There is Rutebook in the synaptic Package manager 600 pages of Linux.

The Ubuntu server is for networking.  You have one computer (with the server installed) and several desktops connected to form a network. 

Unless you want to build a network - don't bother.

---

### Post by tolinrome on 2010-01-31
thanks for all the excellent answers. The pocket guide seems perfect for me. I did download through packet manager the rutebook but I dont know where it went too....

one last thing - I made so many updates and changes to this installation (9.10) - is there anyway I can save a 'config file' so if this laptop blows up I can just install Ubuntu again and reload all my extras without having to go through all that time again?

---

### Post by Robster2 on 2010-02-02
Rutebook information stolen shamelessly from a post by Mike Rechtman.


Click: System --> Administration --> Synaptic Package Manager
Enter your password
Wait for Synaptic to complete loading and enter "rutebook" (without the quotes) in the QuickSearch box.
One line should appear in the lower right-hand pane. (if more or less lines appear -- stop. This won't work)
Click on the box to the left of the rutebook package name, and select "Mark for Installation"
In the Synaptic toolbar, click on "Apply"
When asked "Apply following changes?" click on "Apply" again
Wait for Synaptic to complete loading and installing, then click File --> Quit to end the Package Manager

Step two:
To make it easier to find where the tutorial was installed:

Click System --> Preferences --> Main Menu
Select "System Tools" in the left-hand pane
Click on "+ New Item". A box should open.
Select type: "Application"
and enter Name: "Linux Tutorial" (No quotes)
and Command: "evince /usr/share/doc/rutebook/rute.pdf.gz" (without quotes)
Click "Close"
Click "Close" again.

To read the tutorial:
Click Applications --> System tools --> Linux tutorial

---

### Post by baddog144 on 2010-02-02
Linux is a kernel, the core of the operating system. Ubuntu is built around this core. Linux started as a clone of MINIX, which is a UNIX-*like* OS. I'm not really sure of the exact differences between them though.

The point here is that Ubuntu is not different to Linux, it is built around Linux ;)

---

