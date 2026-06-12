---
title: "Why is it so hard to install applications off the web?"
date: 2012-06-21
forum: General Help
---

### Post by flunkyou2 on 2012-06-21
Hello, I installed the new Ubuntu today  and having trouble installing apps :(  

I downloaded Vuze and wish to install it but how?  I have been using windows for years and thought i would give linux ago but i think i might go back to windows as it dont seem user friendly :(   Why can't i just click on a file and it installs like .exe's in windows? lol

Cheers
Chris

---

### Post by oldos2er on 2012-06-21
Linux isn't Windows; downloading random apps from their websites is the last resort to getting/installing a program, not the first. Use the Software Center instead.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by flemur13013 on 2012-06-21
Installing Vuze is actually easier with ubuntu than a windows install.

Type the stuff after the $:

$ sudo synaptic
(From a terminal, or you can start it from a menu - "System/Admin" something like that -> "(Synaptic)" Package manager).

That should start the "Package manager"

Type "vuze" in the "Quick Filter" at the top. 

I see 4 packages listed, "Vuze" being the first.  

Rt-click on it and select "Install". 
Then click the "Apply button".  

It'll do some stuff and vuze should be installed when it's done.

**Or, instead of all that, you could just type (the stuff after the $)**

$ sudo apt-get install vuze

**And you're all done. **

You need "sudo" for administrative privileges, to install system software; you'll have to enter your "root" password.

Edit: close the "synaptic" program before doing the command-line "apt-get" because they need exclusive use of the package database.

Command-line or synaptic will both show you dependencies you might need to install, too.

Synaptic is often nicer than the command line because it shows other packages that are associated with the one you want; also it can tell you the proper package name from a search in the "quick filter"; something like the "vuze" package might have an official name like "vuze-gtk", etc., rather than just "vuze" (although that's the real name).  I've never used the "Software Center", so maybe it's better...

---

### Post by d.atanasov on 2012-06-21
Hello, 

Why do you think it is hard to install package under Ubuntu? You have so many different things that you can use for example Software Centre, Synaptic Package Manager or even if you have your .deb files you can run Terminal and enter a command dpkg which is the basis of the previously mentioned software. So you have to learn as you did in Windows how the things are working :)

---

### Post by VE6EFR on 2012-06-21
Hi, Chris.

It's not that Ubuntu isn't user friendly. It's just different than what you are used to when you were running Windows. There is a learning curve but once you get the hang of how things work it's pretty easy to get things done.

Good luck and welcome to Ubuntu.

---

### Post by ubuntu27 on 2012-06-21
Here is a guide:

[Installing Software in Ubuntu]("www.psychocats.net/ubuntu/installingsoftware")

---

### Post by haqking on 2012-06-21
> **flemur13013 said:**
> 
Type the stuff after the $:

$ **sudo synaptic**



**You need "sudo" for administrative privileges, to install system software; you'll have to enter your "root" password.**


.

when using graphical apps such as synaptic then you should use **gksudo** and not **sudo.**

and when using sudo, you do not enter your root password, you enter your user account password which is a sudoer, root is locked by default in Ubuntu and has no password, even if its been set it is not the password used for **sudo **or **gksudo.**


This would only change if the admin has changed the way things work on the system such as assigning a password to **root** and changing the config of **sudo** to ask for the **root password**.  If the admin knew how to do this they wouldnt be asking here how to install software ;-)

Cheers

---

### Post by |{urse on 2012-06-21
Plus when you stick to installing through repositories you don't need to worry whether the installation file is rogue or not or for the wrong arch or whether it depends on another software to function etc etc etc.

---

### Post by QIII on 2012-06-21
Another thing to bear in mind when asking "Why doesn't Linux do X like Windows?":

Windows supports only Microsoft products.  Although it seems that Windows supports X, the opposite is true.  The makers of X go to great lengths to make sure X works with Windows.  They make a very wise business decision in doing so:  cost/revenue.

Since there is relatively little revenue to be gained catering to 5% of the market and the cost of catering to it is relatively the same, it would be a losing proposition for X Corporation to do that.  Thus, they don't spend the effort and resources to create a nice installer for many things tor Linux, even though many things (not .exes) might run on Linux.  They can't be blamed for decisions that keep them from going out of business, can they?

Furthermore, there are so many flavors of Linux that there could not be a "one size fits all" installer.

---

### Post by coldraven on 2012-06-21
If you do download an application that has been packaged as a .deb for your version of Ubuntu then you can just double click to install it.
For example see here:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by gordintoronto on 2012-06-21
> **flemur13013 said:**
> Installing Vuze is actually easier with ubuntu than a windows install.

Type the stuff after the $:

$ sudo synaptic
...


Flemur: good advice, except Synaptic is not installed by default in "the latest Ubuntu."

---

### Post by gordintoronto on 2012-06-21
> **flunkyou2 said:**
> Hello, I installed the new Ubuntu today  and having trouble installing apps :(  

I downloaded Vuze and wish to install it but how?  I have been using windows for years and thought i would give linux ago but i think i might go back to windows as it dont seem user friendly :(   Why can't i just click on a file and it installs like .exe's in windows? lol

Cheers
Chris

One more thing: when you installed Ubuntu, it included a bit torrent client which is perfectly servicable. If you double-click on a torrent, it will start right up.

---

### Post by markbl on 2012-06-22
New inexperienced users should stick with the default tool for searching and installing new packages, i.e. Ubuntu Software Center. It's as easy as using the app store on an iphone. Heaps of stuff and you can't go wrong.

I've been using Linux for many many years and I almost never install software from source and rarely download a deb. Stick to the standard packages (and maybe use ppa's when you get experienced) and your system will work consistently and upgrade automatically.

---

