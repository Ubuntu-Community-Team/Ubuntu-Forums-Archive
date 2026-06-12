---
title: "remastersys installing a ton of packages?"
date: 2009-07-17
forum: General Help
---

### Post by pythonscript on 2009-07-17
I'm making a custom live cd in a virtual machine, and I'd heard that remastersys is a good tool to do so. However, the vm I'm using is extremely lightweight, as in it doesn't use gnome... it only uses icewm. When I install remastersys, it's downloading a ton of packages that are all gnome based, and I'm wondering if this is going to mess up all my icewm configurations and if it'll take up a ton of space in the live cd, if it's even included. I'd like my custom "distro" to actually fit on just a cd, not a dvd, but I'm really worried that remastersys is filling my system up with junk. Thanks!

---

### Post by pythonscript on 2009-07-17
Never mind... a single pass of remastersys destroyed my entire icewm installation by overwriting *everything* with gnome. Wonderful. Simply wonderful.

---

### Post by aysiu on 2009-07-17
I made [an IceWM remix](http://ubuntuforums.org/showthread.php?p=7412240#post7412240) with Remastersys and didn't pull in Gnome.

By default, Jaunty installs all recommended packages. If you want to avoid that, use the proper flag: ```
sudo apt-get install remastersys --no-install-recommends
```

---

### Post by utnubuuser on 2009-07-17
hi - for future reference: apt-get is able to do a dry run.  check > man apt-get

---

### Post by aysiu on 2009-07-17
You can also permanently change the apt-get preferences (in terms of pulling in recommended packages or not):
[http://www.ubuntu.com/getubuntu/releasenotes/904#Recommended%20packages%20installed%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/904#Recommended%20packages%20installed%20by%20default)

---

### Post by pythonscript on 2009-07-18
Ok, I must be missing something, because I ran 

```
sudo apt-get install remastersys --no-install-recommends
``` and I still get a bunch of gnome apps (like nautilus, stuff like that) and when I start the x server, I get nautilus. What setting am I missing that this keeps screwing up my desktop? The iso image that is created freezes on "Configuring network interfaces" when I boot it, too. Thanks for the help!

---

### Post by pythonscript on 2009-07-22
Anyone have any ideas? Should I remove the nautilus package before I run remastersys? Is there any way to simply install remastersys with the basic dependencies and none of the gnome/nautilus apps or applets? Thanks!

---

### Post by trevelyn on 2009-07-26
Yeah. i think that is something new, i am trying to get my hands on the older versions of Remastersys, I made my OS with the first version of Remsys, and it only had e17.  Now, what happens is, i create a lightweight version of WNLA with just fluxbox, and install remastersys which installs fine with the normal 40MB worth of deps.  THEN when you go to actually make the backup/ISO you notice that in xterm Remsys (without your permission) tries to install Gnome2 ~ 320MB.  That's not right.. I messaged Fagedelic tonight, i havent been on the Klikit forums in ages due to some permissions problems they keep having.  I'll let you know how to avoid the bloated WM problem when he gets back to me...

Oh, in the meantime, try the pyscocats method of completely removing Gnome, thats what I did, but I had to reinstall a few things when afterwords (libs and such, just keep track of what goes with it and if you need it put it back). 

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Just chomp off the KDE portion of the command so you don't end up with KDE! (they dont seem to have a "Pure IceWM" command there)

also the:

```

sudo apt-get install remastersys --no-install-recommends

```

thing has no effect on weather remsys installs Gnome or not, if you guys have the older versionso f remsys, i'd say don;t update it yet!

---

### Post by pythonscript on 2009-07-26
Thanks for the tip. I'll hunt around and see what I can find, but let me know what he says about that.

---

### Post by trevelyn on 2009-07-26
sure, 
here is a log of what mine says to me:

[http://weaknetlabs.com/temp/error.txt](http://weaknetlabs.com/temp/error.txt)

does that look familiar?
maybe the "--no-install-recommends" args can be put into the source of remsys, then recomile it to not do this when ran.  Also i can vouch for the pyschocats link, I did that last night.  I had to re-install a bunch of lib files afterwords, but nothing that was too complicated.  

(just log everything that goes and reinstall with aptitude when it's done.)

oh yes! duh! i forgot to mention this:
"Need to get 0B/48.9MB of archives."  which i found odd.  its at the bottom of the log in the link above! (i guess they are cached somewhere on my system..)

---

### Post by trevelyn on 2009-07-27
i fixed it.

in Jaunty do: 
```

root@<yourhostname>:~#apt-get remove remastersys --purge

```
then reinstall it and check your version:
```

root@<yourhostname>:~#apt-get install remastersys
root@<yourhostname>:~#remastersys

```
now you should have either version: 
2.0.11.x
or 
2.0.12.x
do:
```

root@<yourhostname>:~#cd /tmp && mkdir remsys

```
and If you have 2.0.11-x:
```

root@<yourhostname>:~#wget http://www.geekconnection.org/remastersys/fragtemp/source/ubuntu-source/remastersys_2.0.11-1.tar.gz

```
or if you have 2.0.12-x:
```

root@<yourhostname>:~#wget http://www.geekconnection.org/remastersys/fragtemp/source/ubuntu-source/remastersys_2.0.12-1.tar.gz

```
now untar it:
```

root@<yourhostname>:~#tar vzxf rem*

```
and open the file "remastersys" in nano and do a CTRL+K on the line that says "apt-get install metacity"
that you will see a few lines below the "help" section near the top-middlish..
it's right below this line:
```

apt-get -y -q remove ubiquity-frontend-kde

```
(you can do a search for it with "CTRL+W") :)
Then, once that line is gone, you do:
```

root@<yourhostname>:~#cp remastersys /usr/bin/remastersys

```
which will write over your old version with your fixed version.
Now you can run it without it installing Gnome or Metacity, the only downfall is that you ar ewithout the "install" option at the Grub screen, as that is what the 
"go-straight-into-the-installer" uses.  So you may want to edit the file isolinux.cfg to not include that option (which may just confuse people who use your distro) 
That file is:
```

/etc/remastersys/isolinux/isolinux.cfg.hardyorlater

```
which is called by /usr/bin/remastersys to "create" (uses it as a template) the actual "isolinux.cfg" file.  (Do another "CTRL+W" in nano on the /usr/bin/remastersys file and search for "isolinux.cfg.hardy"

The answer was right in front of me i can't believe i couldn't figure it out until tonight! w00t! :)

---

### Post by pythonscript on 2009-09-05
Thanks for the help! I've got this working perfectly now.

---

