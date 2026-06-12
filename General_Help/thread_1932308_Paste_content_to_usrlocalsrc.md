---
title: "Paste content to /usr/local/src"
date: 2012-02-27
forum: General Help
---

### Post by viktorjano on 2012-02-27
Hi!

I am trying to copy-paste a tarball (or any folder) from desktop to the folder /usr/local
and after I make copy (right click --> copy) and try to paste it in some of the system folders (like the one mentioned) the paste option is inactive. 

Please help!!!

---

### Post by howefield on 2012-02-27
You need elevated rights to do that, ie use sudo.

Open a terminal and type something like

sudo mv source destination

where source is the path to the file on the desktop and destination is where you want to put it, in this case /usr/local/

---

### Post by forrestcupp on 2012-02-27
Or if you want to use Nautilus, open a terminal and type ```
gksudo nautilus
```and you will have super user privileges in Nautilus to paste the files. Just be careful.

---

### Post by viktorjano on 2012-02-27
Ok! Thanks...
 
You now my real problem is that I can NOT install any application on my Linux Ubuntu Feisty Fawn. I tried firefox (version 10.0.2), I tried skype (newest version), I tried some other packages and nothing happens. I go the standard way (by the way I am reading the steps from a book), [B]
sudo apt-get install packageName

[/B]I do this step by step:
1. copy the tarball  into the folder  /usr/local/src 
2. untar the tarball
    [B]sudo tar -xjvf skype_static-2.2.0.35.tar.bz2
[/B]3. **cd skype_static-2.2.0.35** (that is the name of the newly created folder)
4. so prompt looks like this **profesor@profesor-linux:/usr/local/src/skype_static-2.2.0.35$**
5. and here I type **sudo apt-get install skype**

and here is what I get:

[B]profesor@profesor-linux:/usr/local/src/skype_static-2.2.0.35$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
profesor@profesor-linux:/usr/local/src/skype_static-2.2.0.35$ 
[/B]

---

### Post by howefield on 2012-02-27
Feisty Fawn has been end of life for quite some time. I'd recommend using a currently supported version of Ubuntu if possible.

Then stick to the repositories for installing software.

You are confusing 2 different methods of installing packages. Compiling from source is different to installing from the repository.

---

### Post by viktorjano on 2012-02-27
When I try with dpkg utility:

sudo dpkg --install skype-ubuntu-intrepid_2.1.0.81-1_i386.deb

[B]profesor@profesor-linux:/usr/local/src$ sudo dpkg --install skype-ubuntu-intrepid_2.1.0.81-1_i386.deb

Selecting previously deselected package skype.
(Reading database ... 88002 files and directories currently installed.)
Unpacking skype (from skype-ubuntu-intrepid_2.1.0.81-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libasound2 (>> 1.0.17); however:
  Version of libasound2 on system is 1.0.13-1ubuntu5.
 skype depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 skype depends on libgcc1 (>= 1:4.3); however:
  Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
 skype depends on libqt4-dbus (>= 4.4.3); however:
  Package libqt4-dbus is not installed.
 skype depends on libqt4-network (>= 4.4.3); however:
  Package libqt4-network is not installed.
 skype depends on libqtcore4 (>= 4.4.3); however:
  Package libqtcore4 is not installed.
 skype depends on libqtgui4 (>= 4.4.3); however:
  Package libqtgui4 is not installed.
 skype depends on libstdc++6 (>= 4.3); however:
  Version of libstdc++6 on system is 4.1.2-0ubuntu4.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
profesor@profesor-linux:/usr/local/src$[/B]

---

### Post by SeijiSensei on 2012-02-27
Did you notice where it says "skype-ubuntu-**intrepid**"?  The stock version of Skype was compiled for Intrepid and expects to find libraries no older than the ones shipped with that version of Ubuntu.

You need to upgrade your system to something that is currently supported.  If you don't want to update very often, choose a "long-term-support" version like 10.04.  The upcoming 12.04 releases in April will also have LTS, but they'll also be running the Unity desktop.  You might prefer 10.04 which will look pretty much like Feisty.

---

### Post by viktorjano on 2012-02-28
OK thanks!
So the solution to my problem is most probably upgrading to newer version of Ubuntu!

---

