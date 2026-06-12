---
title: "Duplicate sources.list entry error?"
date: 2010-05-06
forum: General Help
---

### Post by HHx66 on 2010-05-06
Everytime I sudo apt-get update or do anything in synaptic I get this error message:

```
W: Duplicate sources.list entry http://archive.getdeb.net karmic-getdeb/games Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_karmic-getdeb_games_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

```

I've checked my sources.list file, no duplicates that I can see, I've sudo apt-get clean and then updated, same problem,I don't know what the cause is, it doesn't stop funcionality more than just being annoying. Any idea how to fix this?

---

### Post by wojox on 2010-05-06
Have you looked in:

```
ls -l /etc/apt/sources.list.d/
```

That's probably where the dupes are hiding.

---

### Post by HHx66 on 2010-05-07
I just checked and don't see any duplicates, I do see some that are the same but the file ends in .save ?

Any other ideas?

---

### Post by wojox on 2010-05-07
Try going into System > Administration > Software Sources > Other Software 

Look for anything relating to getdeb and uncheck it. See if it still throws that error.

---

### Post by HHx66 on 2010-05-07
Only one entry there, if I uncheck it no problem, but I use the repo so, I don't know.

---

### Post by kevin.krenz on 2010-05-07
Could you post the /etc/apt/sources.list file, as well as the files in /etc/apt/sources.list.d/ ?

---

### Post by HHx66 on 2010-05-08
Yeah I can, heres the sources.list file:

```
# deb cdrom:[Xubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted

deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe

deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://archive.getdeb.net/ubuntu karmic-getdeb games

deb http://archive.getdeb.net/ubuntu karmic-getdeb apps

deb http://download.bitdefender.com/repos/deb/ bitdefender non-free

# deb http://download.virtualbox.org/virtualbox/debian karmic non-free

deb http://winff.org/ubuntu karmic universe

```

heres the directory of sources.list.d (sorry about the format, I'm actually in Windows right now):

```
05/06/2010  07:05 PM                64 akirad-akirad-karmic.list
05/06/2010  07:05 PM                64 akirad-akirad-karmic.list.save
05/06/2010  07:05 PM                65 docky-core-ppa-karmic.list
05/06/2010  07:05 PM                65 docky-core-ppa-karmic.list.save
05/06/2010  07:05 PM                50 google-chrome.list
05/06/2010  07:05 PM                50 google-chrome.list.save
05/06/2010  07:05 PM                76 matthaeus123-mrw-gimp-svn-karmic.list
05/06/2010  07:05 PM                76 matthaeus123-mrw-gimp-svn-karmic.list.sav
e
05/06/2010  07:05 PM               273 medibuntu.list
05/06/2010  07:05 PM               273 medibuntu.list.save
05/06/2010  07:05 PM               355 opera.list
05/06/2010  07:05 PM               355 opera.list.save
05/06/2010  07:05 PM                68 paul-climbing-ppa-karmic.list
05/06/2010  07:05 PM                66 paul-climbing-ppa-karmic.list.save
05/06/2010  07:05 PM                57 playdeb.list
05/06/2010  07:05 PM                68 zachanimerulz-ppa-karmic.list
05/06/2010  07:05 PM                68 zachanimerulz-ppa-karmic.list.save
              17 File(s)          2,093 bytes
               2 Dir(s)  17,615,200,256 bytes free
```

---

### Post by kevin.krenz on 2010-05-09
Try running this Python script - it might help you find where the duplicate is hiding.

```

#! /usr/bin/python
# Kevin Krenz 9 May 2010
# This script is designed to find duplicate sources

import os

# build list of files to look for sources
list = os.listdir('/etc/apt/sources.list.d/')
files = ['/etc/apt/sources.list.d/' + file for file in list if not('.save' in file)] # use full path names, skip backup copies
files.insert(0, '/etc/apt/sources.list')
sources = []
dup = False

# loop through files 
for file in files:
  oFile = open(file)
  for line in oFile:
    piece = line.split()
    if piece and not(line[0] == '#'): # quit if line is empty or a comment
      for i in piece[3:]:
        src = piece[0] + ' ' + piece[1] + ' ' + piece[2] + ' ' + i
        if src in sources:
          print 'Duplicate: ' + src + ' in ' + file
          dup = True
        else:
          sources.append(src)
  oFile.close()

if not(dup): print 'No duplicates found'



```

---

### Post by HHx66 on 2010-05-09
Okay, I'll try it tonight when I have the time and when I'm booted into ubuntu.

---

### Post by HHx66 on 2010-05-10
Thanks that python script actually helped a lot! I found it.

---

