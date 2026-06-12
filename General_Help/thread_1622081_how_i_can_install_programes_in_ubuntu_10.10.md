---
title: "how i can install programes in ubuntu 10.10"
date: 2010-11-15
forum: General Help
---

### Post by astm on 2010-11-15
[SIZE=4]hello guys
i want to know how i can install programs in ubuntu 10.10 
i try to open ubuntu software center then search about the program i want  then press on install button but after that i can't know how i can find this program or how i can get it ?

help me please #-o[/SIZE]

---

### Post by Verbeck on 2010-11-15
the programs usually gets sorted in the applications menu if it has a gui. in 10.10, at the top of the installation page, there should be an indication on where its is located
[img]http://4.bp.blogspot.com/_JSR8IC77Ub4/THjCDVLQJ9I/AAAAAAAABBU/CwxEd9AclnI/s1600/4JULA.png[/img]

---

### Post by astm on 2010-11-24
is this step want me to have internet connection in my ubuntu pc ?

---

### Post by deserthowler on 2010-11-24
> **astm said:**
> is this step want me to have internet connection in my ubuntu pc ?

Yes, it gets them from the Ubuntu repositories.

Earl

---

### Post by astm on 2010-11-29
[SIZE=3]yes i relay installed some programs from ubuntu software center

but i want to install some programs like  dream weaver - wampserver - photoshop - flash

what i can do ?  all of these programs for windows ;)[/SIZE]

---

### Post by oliwek on 2010-11-29
The best thing to do is to find linux alternatives for those programs : use GIMP instead of Photoshop, etc

you'll find a list for some of the windows classics here : [https://help.ubuntu.com/8.04/switching/applications-equivalents.html](https://help.ubuntu.com/8.04/switching/applications-equivalents.html)


Another way is to install [wine]("https://help.ubuntu.com/community/Wine"), and then with the help of wine, (try to) install your windows programs

then if it doesn't work with wine, use [virtualbox]("https://help.ubuntu.com/community/VirtualBox"), install windows from within the virtualization software, and install your precious windows .exe (with this solution, you run windows from within linux, both at the same time, so you can install any program, but it will be slower than if you ran directly windows. A fast dual or quadcore CPU + plenty of RAM helps a lot)

of course you could also install windows in another partition and keep a multiboot PC(but then you can't run Ubuntu and a windows program simultaneously : you have to reboot each time)

ps : you should try to search a bit, all your questions are already answered in the documentationi section  ;)
start from there : [https://help.ubuntu.com/community]("https://help.ubuntu.com/community")
then if you enter "windows" in the search area, or "wine", you'll find already plenty of information

---

### Post by oldos2er on 2010-11-29
> **astm said:**
> [SIZE=3]what i can do ?  all of these programs for windows ;)[/SIZE]

If you need to use Windows programs, run Windows. As was mentioned, Wine may or may not work for you; check the app database at [http://appdb.winehq.org/](http://appdb.winehq.org/) beforehand to see if there's any point in trying to use the programs you mentioned.

There is a Linux version of flash; the package name is flashplugin-installer.

---

### Post by IronHide NSDQ on 2010-11-30
I have an interesting one here...Software Center won't open!!

When I went to attempt to uninstall it and then re-install it, the system said I would also uninstall "Ubuntu Netbook". 

Now, for obvious reasons, this gave me pause :D

Any ideas??

---

### Post by ivarn on 2010-12-01
> **IronHide NSDQ said:**
> I have an interesting one here...Software Center won't open!!

When I went to attempt to uninstall it and then re-install it, the system said I would also uninstall "Ubuntu Netbook". 

Now, for obvious reasons, this gave me pause :D

Any ideas??

And you're sure it's not running in the background, on another workspace or something?
Run the command "killall software-center" from the command line (ALT+F2).
Then try to start it again.
No luck? Run "sudo apt-get reinstall software-center" from the terminal (CTRL+ALT+T)

EDIT: Windows apps in Linux will never work 100% stable even with Wine installed.
Wine will let you run a few windows apps but most of them not that stable. It's more a solution for gamers and less important stuff like that.
Here: check out these links for good alternatives to your Windows apps:
[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.osalt.com/](http://www.osalt.com/)
[http://linuxappfinder.com/](http://linuxappfinder.com/)

Macromedia Dreamweaver MX 2004 and 8 and Macromedia Flash mx 2004 and 8 works great.

---

### Post by IronHide NSDQ on 2010-12-02
Ok, the Killall command does nothing.

When I click on Software Center, it looks like it trys to start, but fails after a few seconds.

Tried the command reinstall and got "E: Invalid Operation reinstall"

---

