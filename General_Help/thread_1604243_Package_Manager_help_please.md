---
title: "Package Manager help please"
date: 2010-10-23
forum: General Help
---

### Post by jfbooth on 2010-10-23
Xubuntu 10.10

I installed a particular package known as ORIGAMI.  Found it in Package Manager.  All went well, .. until I realized it needs to be installed via command line in order to customize it.  So .. I UNinstalled it (complete removal) in PM and tried it again but this time 'download package files only' with the idea that I could then install it in Terminal and pass the install parameters I needed.

Problem:  I don't know what downloaded or where it is.  Doing a search on ORIGAMI with CATFISH, I find 38 hits.  Hmmmm, thought I uninstalled it ... COMPLETE REMOVAL?  Seems like a lot of 'left behind'things.  Anyway, ONE of the files found is:

origami_0.7.4-Oubuntu2_all.deb  21 kB   /var/cache/apt/archives

but it is so small, I doubt this is the item I am looking for.  Maybe I have the wrong perspective on this.  I need to install ORIGAMI with parameters and thought this is what I needed to do.

Now, first I would like to clean up all this origami-related leftovers and then get it installed.

Attached is a PARTIAL screen shot of the CATFISH search (if it works .. never attached a pic here before) and a SECOND attachment showing the ones that would not fit in the first shot.

I am pretty new to Linux and would appreciate any help.

---

### Post by Jose Catre-Vandis on 2010-10-23
OK, this should be fairly straight forward, do the following:

1. Open a terminal
2. Type the following:
```
sudo apt-get purge origami
```

[This]("http://ubuntuforums.org/showpost.php?p=5896262&postcount=9") post may also help with clearing out origami bits and pieces

3. then install it again
```
sudo apt-get install origami
```
(Add your required / preferred install parameters to the code above) although I would guess that you need to add the parameters when you run origami, not when you install it??

Depending on what you are doing, you may need to install from source, and compile the program with a specific config? If so you need to download the source, untar it, run the configure script, add your required parameters and then compile, and then install...

---

### Post by jfbooth on 2010-10-23
> **Jose Catre-Vandis said:**
> OK, this should be fairly straight forward, do the following:

1. Open a terminal
2. Type the following:
```
sudo apt-get purge origami
```

[This]("http://ubuntuforums.org/showpost.php?p=5896262&postcount=9") post may also help with clearing out origami bits and pieces

3. then install it again
```
sudo apt-get install origami
```
(Add your required / preferred install parameters to the code above) although I would guess that you need to add the parameters when you run origami, not when you install it??

Depending on what you are doing, you may need to install from source, and compile the program with a specific config? If so you need to download the source, untar it, run the configure script, add your required parameters and then compile, and then install...

Thank you for your reply.  There is SOME kind of problem .. I am getting install info from their website:

[http://origami.zelut.org/documentation.php](http://origami.zelut.org/documentation.php)

THEY SAY "Download Ubuntu

```
sudo aptitude install origami
```

Xubuntu does not have 'aptitude' which is why I used PACKAGE MANAGER.

Can I use apt-get origami??  I don't think so.

Then they say SOME parameters are passed during install which implies I have to GET IT FIRST and then install it:

```
sudo origami install -u USERNAME -t TEAMNUMBER -k PASSKEY
```

Using your suggestion, I get:

```
sudo apt-get install origami -u USERNAME -t TEAMNUMBER -k PASSKEY
```
**E: Command line option 'k' [from -k] is not known.**

apt-get install has some problem with -k.  This won't pass to apt-get.

thanks again for your time.  Further comments are appreciated.

Maybe I need to get 'aptitude'.

---

### Post by oldos2er on 2010-10-23
apt-get will work, also you can use it to install aptitude if you like. ```
sudo apt-get install origami && sudo origami install
```

---

### Post by jfbooth on 2010-10-23
> **oldos2er said:**
> apt-get will work, also you can use it to install aptitude if you like. ```
sudo apt-get install origami && sudo origami install
```

This looks REALLY promising.  Thank you.  Here is the latest problem.  Went to Package Manager.  It showed ORIGAMI as installed.  Marked it for COMPLETE REMOVAL and it uninstalled .. I GUESS.

Here is output from: ```
sudo apt-get install origami && sudo origami install
```where *'s are parameters.

jb@john-xubuntu:~/Desktop$ sudo apt-get install origami && sudo origami install -u ********* -k ******************** -t *****
[sudo] password for jb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  origami
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.5kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Selecting previously deselected package origami.
(Reading database ... 120819 files and directories currently installed.)
Unpacking origami (from .../origami_0.7.4-0ubuntu2_all.deb) ...
Processing triggers for man-db ...
Setting up origami (0.7.4-0ubuntu2) ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

ERROR: ORIGAMI APPEARS TO ALREADY BE INSTALLED. ABORTING!

so I tried:

sudo apt-get purge origami

and then repeated:

sudo apt-get install origami && sudo origami install -u ********* -k ******************** -t *****

and I still get 

ERROR: ORIGAMI APPEARS TO ALREADY BE INSTALLED. ABORTING!

Now, my OS thinks it is installed.

HELP, .. please.

---

### Post by oldos2er on 2010-10-23
Since it's installed, you only need the "sudo origami install" command.

You're more likely to get help on the folding forum: [http://foldingforum.org/](http://foldingforum.org/)

---

### Post by jfbooth on 2010-10-23
> **oldos2er said:**
> Since it's installed, you only need the "sudo origami install" command.

You're more likely to get help on the folding forum: [http://foldingforum.org/](http://foldingforum.org/)

I think I am getting closer.  I followed some instructions at:

[http://ubuntuforums.org/showpost.php?p=5896262&postcount=9](http://ubuntuforums.org/showpost.php?p=5896262&postcount=9)

for removing Origami.  It did not go perfectly, but most of it removed a lot of stuff... lending me to believe it was effectively removed.

So I tried your advice again with different results:

sudo apt-get install origami && sudo origami install -u ******** -k ************************************ -t *****
Reading package lists... Done
Building dependency tree       
Reading state information... Done
origami is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo: origami: command not found

which leads me to believe OS still thinks it is installed AND it does not like your suggestion (?) .. unless I made a typo .. or something.

I will go to them and see if I can get this straightened out.  Thank you all for your time and courtesy.

I have no idea what I did, .. but it appears to be installed (fully and correctly).  I rebooted machine.  I did the following:

sudo origami install -u ******* -t ****** -k *********************************
INSTALLING... PLEASE BE PATIENT
INSTALLATION SUCCESSFUL

and it appears to be running right.  Thank you all again.

---

