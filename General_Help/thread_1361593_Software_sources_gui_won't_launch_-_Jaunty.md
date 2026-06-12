---
title: "Software sources gui won't launch - Jaunty"
date: 2009-12-22
forum: General Help
---

### Post by madwoollything on 2009-12-22
I had to ditch Karmic as it broke badly. I've installed Jaunty but am now not able to launch the software sources gui. Nothing seems to happen when trying to launch the gui.

There are a number of archived posts which seem to suggest fixes but I've not been able to get any of them to work. Maybe I'm applying the wrong one? 

My system is fully up to date with all recommended and security fixes applied.

---

### Post by ajgreeny on 2009-12-22
Try opening the /etc/apt/sources.list in gedit to see if anything unusual appears to be there, or just try using the command ```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
``` in terminal; it may give you a clue.

---

### Post by madwoollything on 2009-12-22
> **ajgreeny said:**
> Try opening the /etc/apt/sources.list in gedit to see if anything unusual appears to be there, or just try using the command ```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
``` in terminal; it may give you a clue.

Thanks .... this is the output but I guess the important bit is **Error: could not find a distribution template**. Do you know how to fix this? There are lots of posts but where to go from here??

 /usr/bin/software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

---

### Post by ajgreeny on 2009-12-22
Let's see the sources.list file as I said before, though whatever is in it, the application should still open, it would just not perhaps work as it should.

Secondly did you do anything to the python software that you know of, as it appears that python is having problems.  If none of that helps, I'm afraid it is probably beyond my capabilities to help you any more.

---

### Post by madwoollything on 2009-12-22
> **ajgreeny said:**
> Let's see the sources.list file as I said before, though whatever is in it, the application should still open, it would just not perhaps work as it should.

Secondly did you do anything to the python software that you know of, as it appears that python is having problems.  If none of that helps, I'm afraid it is probably beyond my capabilities to help you any more.

Here is my sources.list file ....... thanks (I've not consciously done anything with python .... not sure which apps use this)

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria main upstream import
deb [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) jaunty main
deb [http://ppa.launchpad.net/tomboy-packagers/stable/ubuntu](http://ppa.launchpad.net/tomboy-packagers/stable/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tomboy-packagers/stable/ubuntu](http://ppa.launchpad.net/tomboy-packagers/stable/ubuntu) jaunty main
deb [http://ppa.launchpad.net/testdrive/ppa/ubuntu](http://ppa.launchpad.net/testdrive/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/testdrive/ppa/ubuntu](http://ppa.launchpad.net/testdrive/ppa/ubuntu) jaunty main

---

### Post by ajgreeny on 2009-12-22
Well, nothing there that looks odd to me, so as I said in my last post, I think it's all beyond me now.

Sorry I have not been much help, but as a last resort try renaming the current sources.lst file as a backup, then see if making a temporary new one from this site helps in any way.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
If it is no help at all, you can delete the new one and restore your backup old one.

Finally, what happens if you open synaptic and try to go to Settings->Repositories?  Perhaps exactly the same, but worth a try.

---

### Post by madwoollything on 2009-12-23
> **ajgreeny said:**
> Well, nothing there that looks odd to me, so as I said in my last post, I think it's all beyond me now.

Sorry I have not been much help, but as a last resort try renaming the current sources.lst file as a backup, then see if making a temporary new one from this site helps in any way.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
If it is no help at all, you can delete the new one and restore your backup old one.

Finally, what happens if you open synaptic and try to go to Settings->Repositories?  Perhaps exactly the same, but worth a try.

Thanks for your help .... still have the same problem with the new sources.list file. Must be the python problem?

---

