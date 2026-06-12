---
title: "Update Manager Problem"
date: 2010-11-28
forum: General Help
---

### Post by Vicedi on 2010-11-28
I'm running Ubuntu 10.10

now all of a sudden my Update Manager will not work, I'm getting this error:  E:Type'wget' is not known on line 66 in source list/etc/apt/sources.list' any help would be Greatly appreciated!

don't know if it's from the same problem but my Ubuntu Software Center will not open as well...Thanks!!

---

### Post by wojox on 2010-11-28
Post back from the terminal:

```
cat /etc/apt/sources.list
```

---

### Post by Vicedi on 2010-11-28
I hope this is what you wanted to see,,,Thanks for any advice you can give me!

# added by the release upgrader
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner



deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository

deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock
wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -

---

### Post by plucky on 2010-11-29
This is the problem.

> wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add - 

Edit the file and remove that line.As it is a system file you will have to use sudo as in ```
gksudo gedit /etc/apt/sources.list
``` and delete that line.Then run ```
sudo apt-get update
``` and see if the problem is fixed.

Also put a # in front of the line ```
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
``` so that it doesn't ask you to load the CDrom when you are updating or installing.

Good luck

---

### Post by Vicedi on 2010-11-29
THANKS!!! plucky,,,,after doing what you told me I was able to open the Synaptic Package Manager and run Updates. 

I've had a few problems since the upgrade,,,half of my dual processor started maxing out with nothing showing up in "Processes",,,not sure but I found some problems with my Docky and I guess in the process of fixing this I started another problem....Hopefully I've gotten the "Bugs" out now and Thanks for your help. I've had some training using the "text editor" as they call it now. and set mine to number the lines to see where line 66 was. But wasn't really sure or confident enough to mess with it. I learn new things everyday and still put Ubuntu over Microsofty anyday.....Thanks!

---

### Post by Cloink on 2011-01-06
Hello.

I have exactly the same problem, however the above fix hasn't worked for  me.  The command-line command (sudo apt-get update) apparently works  but I get no gui if I choose 'Update Manager' from the System >  Administration menu.  Similarly, my daily updates has disappeared.    Likewise, nothing happens if I select Application > Ubuntu Software  Manager.

I recently installed wicd which added an extra line to my sources.list  as seen below (last line), which I have tried commenting out.  I get a  warning if I include the last line about not having the public key (see  separate box after).
```

cloink@Cloink:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://apt.wicd.net intrepid extras
cloink@Cloink:~$ 

```

Output from sudo apt-get update:-
```

<..lots of Hits and Igns...>
Hit http://security.ubuntu.com lucid-security/multiverse Sources       
Get: 4 http://apt.wicd.net intrepid Release.gpg [197B]
Ign http://apt.wicd.net/ intrepid/extras Translation-en_GB
Get: 5 http://apt.wicd.net intrepid Release [17.3kB]
Ign http://apt.wicd.net intrepid Release 
Ign http://apt.wicd.net intrepid/extras Packages
Ign http://apt.wicd.net intrepid/extras Packages
Get: 6 http://apt.wicd.net intrepid/extras Packages [841B]
Fetched 20.9kB in 9s (2,114B/s)
Reading package lists... Done
W: GPG error: http://apt.wicd.net intrepid Release: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY FEC820F4B8C0755A

```

Any help appreciated!

Thanks,
Clark.

---

### Post by plucky on 2011-01-06
> deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras


Very likely that repository no longer exists as intrepid reached end of life in April 2010.
Open Your **Software Sources** and remove that repo as a source by un-ticking the box for that line.Then reload the repository indexes.

Or 

you could add the key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FEC820F4B8C0755A
``` in a terminal.

Good Luck

---

### Post by Cloink on 2011-01-06
Sorry, no joy.  Don't know how to "reload repo indexes"...? - nothing obvious in the **Software Sources** dialogue.  Have re-booted if that would have done it, but still no Update Manager or Ubuntu Software Centre.  I think this is related too -- I can't open '.deb' files with the gui.  Eg. I have a .deb file on my desktop, if I click it, I get the 'working' cursor for a few seconds, then nothing, it just returns to the default cursor.  Right-clicking tells me it's trying to "Open with GDebi Package Installer".  I'm learning Ubuntu/Linux very slowly so please assume I don't know how to do what you're asking without every single step being spelt out...thanks.

---

### Post by plucky on 2011-01-06
> **Cloink said:**
> Sorry, no joy.  Don't know how to "reload repo indexes"...? - nothing obvious in the **Software Sources** dialogue.  Have re-booted if that would have done it, but still no Update Manager or Ubuntu Software Centre.  I think this is related too -- I can't open '.deb' files with the gui.  Eg. I have a .deb file on my desktop, if I click it, I get the 'working' cursor for a few seconds, then nothing, it just returns to the default cursor.  Right-clicking tells me it's trying to "Open with GDebi Package Installer".  I'm learning Ubuntu/Linux very slowly so please assume I don't know how to do what you're asking without every single step being spelt out...thanks.

If you un-tick a box to de-activate a repo,when you close the **Software Sources** another window will open and ask you to reload or cancel.Select Reload.

Or From a terminal ```
sudo apt-get update
``` will do the same thing,but you will have to edit the sources.list file and put a # in front of the line ```
deb http://apt.wicd.net intrepid extras 
```


To edit the sources.list file,use ```
gksudo gedit /etc/apt/sources.list
```

Good Luck

---

### Post by Cloink on 2011-01-07
Oh sorry, yeah, I did select 'Reload' at that point (just re-done it to check, but yes, it did reload the previous time as well).

I have tried Update Manager both with and without the "deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras" line.  From the original postee's post, that seemed like it might be causing the problem, esp. since Vicedi's Ubuntu Software Centre similarly failed to load.  However I now think the wicd thing is a red herring.

So we're back to square one I'm afraid.  I have no ***gui*** Upd Mgr or Ub. S/ware Ctr and I have absolutely no idea what the problem is.  The "sudo apt-get update" command works from the command line (both with/out the wicd line in sources.list - just with a warning if the wicd line IS in).

Any other ideas?
Thank you.

---

### Post by plucky on 2011-01-07
> So we're back to square one I'm afraid. I have no gui Upd Mgr or Ub. S/ware Ctr and I have absolutely no idea what the problem is. The "sudo apt-get update" command works from the command line (both with/out the wicd line in sources.list - just with a warning if the wicd line IS in).


remove the wicd line then run ```
sudo apt-get update
sudo apt-get upgrade
``` 

The second command actually installs any updates it finds.Post the output of both commands if there are any errors or if any software is being held back.

Good Luck

---

### Post by Cloink on 2011-01-10
Aww man I've been checking for any reply.. and checking.. and checking.  I never noticed the thread had gone onto its second page!!

Anyway apt-get update/upgrade, both worked a charm... but still no gui Update Manager.  Have rebooted since the upgrade.

---

### Post by Cloink on 2011-01-15
Plucky, anyone, any further advice?  Command line apt-get update/upgrade works fine but I still get nothing if I go System > Administration > Update Manager.  Same goes for Applications > Ubuntu Software Centre.  With the latter, it 'thinks about it' for a few seconds (ie. the cursor turns into the 'working' cursor), but then nothing happens.

The same thing happens if I try opening a .deb file (working cursor, then nothing).

Thank you.

---

### Post by plucky on 2011-01-15
Different problem try starting separate thread will probably get more attention from the community.

Also only the original poster can mark a thread as solved.

Good Luck

---

