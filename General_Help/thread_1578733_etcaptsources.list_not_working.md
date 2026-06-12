---
title: "/etc/apt/sources.list not working"
date: 2010-09-20
forum: General Help
---

### Post by geckopunk on 2010-09-20
Hello everyone,

As much as it pains me to post this, I have tried to add repositories to my /etc/apt/sources.list file and have managed to create an error by doing so. When I try to do a 'sudo apt-get update' or use my Update Manager, I get the following error: An unresolvable problem occurred while initializing the package information. Please report this bug against the 'update manager' package and include the following error message: 'E:Type " is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Here is a printout of what my /etc/apt/sources.list file looks like. Seeing as how it says "on line 1" I'm sure many of you will easily find the error and laugh at my inexperience with Ubuntu.

                     pre.western { font-family: "Times New Roman"; }pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to # newer versions of the distribution.  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties  ## Major bug fix updates produced after the final release of the ## distribution. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team. Also, please note that software in universe WILL NOT receive any ## review or updates from the Ubuntu security team. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  ## team, and may not be under a free licence. Please satisfy yourself as to  ## your rights to use the software. Also, please note that software in  ## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse  ## Uncomment the following two lines to add software from the 'backports' ## repository. ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse  ## Uncomment the following two lines to add software from Canonical's ## 'partner' repository. ## This software is not part of Ubuntu, but is offered by Canonical and the ## respective vendors as a service to Ubuntu users. # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main 
Any help is appreciated! Thank you

---

### Post by jgull8502 on 2010-09-20
Could you attach a copy of the sources.list? It's kind of hard to read in this format.

---

### Post by geckopunk on 2010-09-20
Note that I had to change the filename to sources.list.txt to make it a viable extension as I couldn't just upload sources.list

Thank you for your help... It is taken with much appreciation.

---

### Post by Chris1274 on 2010-09-20
.

---

### Post by kevin.krenz on 2010-09-21
I'm not quite sure what's going on, but if you delete the very first line, it should work.

---

### Post by 3rdalbum on 2010-09-21
See my signature.

---

### Post by sikander3786 on 2010-09-21
Well I really couldn't find anything that would annoy apt-get in line 1. Your sources.list seems to be ok. If the problem isn't solved yet, could you please go through the following commands and post back the results. After you have pasted them, select and click the # button on top. That will make it more easy to read.

```

cat /etc/apt/sources.list

```

I know you have posted your sources.list already but I want to make sure. Also,

```

sudo apt-get update

```

---

### Post by geckopunk on 2010-09-21
> **kevin.krenz said:**
> I'm not quite sure what's going on, but if you delete the very first line, it should work.

I tried that and it still gave me the same error again. It makes me think that this would be some kind of file format issue or something completely different because Line#2 would be the new Line#1.

Also, I don't know if this would help contribute to the issue: When I changed the sources.list file, I used oowriter, but I saved it using the non-ODF format.

---

### Post by geckopunk on 2010-09-21
> **sikander3786 said:**
> Well I really couldn't find anything that would annoy apt-get in line 1. Your sources.list seems to be ok. If the problem isn't solved yet, could you please go through the following commands and post back the results. After you have pasted them, select and click the # button on top. That will make it more easy to read.

```

cat /etc/apt/sources.list

```I know you have posted your sources.list already but I want to make sure. Also,

```

sudo apt-get update

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main

And again, after typing 'sudo apt-get update', I get the following error: E: Type ' ' is not known on line 1 in source list /etc/apt/sources.list  

Would there be a default /etc/apt/sources.list file that I can download from Ubuntu or anywhere else on the Internet and just add all the additional repositories I have?

Thank you,
Derek

---

### Post by geckopunk on 2010-09-21
p { margin-bottom: 0.08in; }  On a side note, I also have another error regarding my sources.list error:
 

 Could not initialize the package information.
 

 An unresolvable problem occurred while initializing the package information.  
 

 Please report this bug against the 'update-manager' package and include the following error message:
  
 **'E:Type '' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read.'**

---

### Post by wilee-nilee on 2010-09-21
> **geckopunk said:**
> I tried that and it still gave me the same error again. It makes me think that this would be some kind of file format issue or something completely different because Line#2 would be the new Line#1.

Also, I don't know if this would help contribute to the issue: When I changed the sources.list file, I used oowriter, but I saved it using the non-ODF format.

It should be gedit.

run this command and put the apt.list in it.

sudo gedit /etc/apt/sources.list

Then run the update.

---

### Post by drs305 on 2010-09-21
> **geckopunk said:**
> 
Would there be a default /etc/apt/sources.list file that I can download from Ubuntu or anywhere else on the Internet and just add all the additional repositories I have?

Thank you,
Derek

You can generate one from this site:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by sikander3786 on 2010-09-21
It really seems to be a bug to me. The line to which the error is mentioning is **deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted** and the error is '' these quotation marks and I can't see those quotation marks in the sources.list.

It was a fresh install with lucid or an upgrade? Wait, let me check my sources.list and post it to you if needed. At least 10 min.

---

### Post by snowpine on 2010-09-21
Never use OpenOffice to edit system files! Use a plain-text editor such as Gedit or Nano.

---

### Post by geckopunk on 2010-09-21
Hello all,

It seems as though I've just created a new sources.list file by renaming my previous file to sources.list.old and then running gpedit /etc/apt/sources.list and then running sudo apt-get install and I was given a new Repository list file...

I cat'd the sources.list file and found out that it was changed to:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted

I'll see what I can do about backing up this file and adding the rest of my repositories.

Again, THANK YOU all for your support. I appreciate your responses.

---

