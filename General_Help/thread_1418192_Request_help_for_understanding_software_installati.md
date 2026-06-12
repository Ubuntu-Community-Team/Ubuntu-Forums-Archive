---
title: "Request help for understanding software installations"
date: 2010-02-28
forum: General Help
---

### Post by eeprom on 2010-02-28
Hello,
I would like to understand how to install new software in ubuntu.  I have installed several programs, but I don't understand how they get installed.  Please note, I am not looking for a solution in how to download; I am trying to understand what linux is doing.  I imagine someone is going to tell me to type:
"sudo apt-get update"
"sudo apt-get install oregano"
But I would like to know what's going on.  Can someone point me to some documentation?

Example:  I have just downloaded Oregano using my Archive Manager.  I used "locate" to figure out where it went.  It is clearly on my system, in /usr/share/app-install/desktop$ oregano.desktop.  Archive Manager obviously put it there.  Now, using terminal commands, what do I need to install it?  Or is it already installed?

---

### Post by Swagman on 2010-02-28
Me again

It's already installed

I installed Oregano from Software Centre (Add/Remove in Feisty) and the launcher is in Applications/Science.

Or you can press left alt + f2 and type oregano to launch it

---

### Post by drpjkurian on 2010-02-28
Hi
1.To install new programmes, Please go to
'Ubuntu software centre' and select the programmes you wish and click for install

2. Some programmes you wish may not be listed in 'Ubuntu software centre' for eg Skype.
In this cases you may have to download the .deb versions of those programmes and click for Install.
Hereby I am giving the URL address of Skype .deb Package.
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

3. If .deb file are not available,the programme has to be installed through terminal by commands.

These are the the methods to install programmes in Linux.
Each programmes consist of several packages which conducts the smooth functioning of programme. Therefore synaptic package manager may not help you to install programmes

---

### Post by Swagman on 2010-03-01
So...

Howd this pan out then eeprom ?

---

### Post by eeprom on 2010-03-01
Swagman,
Thanks for asking.  I am up to speed in that I can pretty much install whatever I want.  The software center is a good resource.  However, I wish I understood more how a package gets installed, as I know how this works in windows, and in windows I can do this from a command line (run).  Synaptics seems to be the most similar method on the computer, and it is pretty easy to use.  But I am still way into the linux learning curve, and I guess I am confused between the archive manager, synaptics, tar balls, and command line installations.  They appear to all be methods of doing the same thing.  I prefer to understand things from the command line point of view.  I will try downloading a few tar files and then unzipping and installing them.  

EE

---

### Post by JKyleOKC on 2010-03-01
> **eeprom said:**
> I guess I am confused between the archive manager, synaptics, tar balls, and command line installations.  They appear to all be methods of doing the same thing.That's pretty much true, but a few differences do exist.

Synaptic, aptitude, and apt-get all do about the same thing, which is to access an "official" repository (and possibly others, if you have added them to your sources.list file), download a package file and any additional files it requires, then run the install scripts from that package. The install scripts from official repositories put the program files in "standard" locations such as /usr/bin, and usually add launcher lines to the system menu. Scripts from other sources may or may not do the same thing.

Using the archive manager won't, in itself, do any special placement of the files. This can make it more difficult to sort out the results unless you're quite familiar with the "standard locations" (which may vary from one distribution to another; Red Hat and Mandriva do things quite differently from Debian and Ubuntu, for example).

The tarball approach used to be the standard way, and is still the way most distribution maintainers get the programs in the first place before building the simplified packages (.deb or .rpm files). However it still runs some risk of putting things in non-standard locations. The great advantage of the tarball is that since you are actually compiling the programs from source there's less chance of errors and more opportunities to make custom changes. These advantages are, at the same time, disadvantages in that there's more opportunity for things to go wrong and less chance for you to get help when that happens!

While you're in the learning curve it's probably best to stick with the Synaptic-aptitude-apt-get approach, but use "locate" and "man" to learn more about just where the standard locations are for the distro you are using. You can add PPAs to your sources.list file (Synaptic makes it easy to do) for those few things such as VirtualBox's uncrippled edition that are not in the repositories...

Hope this helps some!

---

### Post by Alexandre Putt on 2010-03-01
> **eeprom said:**
> I wish I understood more how a package gets installed, as I know how this works in windows, and in windows I can do this from a command line (run).

Well, the archive is unpacked and the files are simply placed as prescribed into directories like /usr/bin, /usr/share/doc etc. 

There is no "installation" as such. There are two notes, however. 
[LIST]
[*]The package manager stores the information about each installed package so that to honour the dependencies and provide other services. This is necessary in order to avoid conflicts and missing/wrong libraries.
[*]More complex packages need to be configured in some way. E.g. Gnome menu may need to be altered.
[/LIST]

---

