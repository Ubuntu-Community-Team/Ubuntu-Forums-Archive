---
title: "Synaptic package manager problems :S"
date: 2009-11-23
forum: General Help
---

### Post by lsk3993 on 2009-11-23
I'm a new Ubuntu user and while I was trying to install Adobe Reader (via Medibuntu) I must have done something wrong because now I get this error message when I try open the Synaptic Package Manager: ```
E: Type ‘“deb’ is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

```What have I done wrong and how can I resolve the problem?

Thanks in advance

---

### Post by Filipek on 2009-11-23
> **lsk3993 said:**
> I'm a new Ubuntu user and while I was trying to install Adobe Reader (via Medibuntu) I must have done something wrong because now I get this error message when I try open the Synaptic Package Manager: ```
E: Type &#8216;&#8220;deb&#8217; is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

```What have I done wrong and how can I resolve the problem?

Thanks in advance

Please quote what command exactly are you trying to execute and the contents of sources.list file.

---

### Post by bapoumba on 2009-11-23
There probably is a bad line in your sources.list.

Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by lsk3993 on 2009-11-23
> **Filipek said:**
> Please quote what command exactly are you trying to execute and the contents of sources.list file.
I'm just trying to open the synaptic package manager from system>administration, is that what you are asking?
And what do you mean by sources.list file? (New user remember)

---

### Post by lsk3993 on 2009-11-23
> **bapoumba said:**
> There probably is a bad line in your sources.list.

Please post the output of:

```
cat /etc/apt/sources.list
```
I feel silly for asking this, but where is that file found? I can't seem to find it

---

### Post by bapoumba on 2009-11-23
> **lsk3993 said:**
> I feel silly for asking this, but where is that file found? I can't seem to find it

Please open a terminal (Accessories>Terminal) and paste the command I gave you. Then paste the output here :)

---

### Post by seeker5528 on 2009-11-23
> **lsk3993 said:**
> I feel silly for asking this, but where is that file found? I can't seem to find it

Cat is a command line utility, so you need to open a terminal window (AKA console) and type in the command as requested in the previous post.

Later, Seeker

---

### Post by lsk3993 on 2009-11-23
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

---

### Post by NoaHall on 2009-11-23
Delete the last line.

Command  in terminal -
```
gksudo gedit /etc/apt/sources.list
```
Then delete the last line, and save.
 Have you tried installing some very old software?

---

### Post by bapoumba on 2009-11-23
> **lsk3993 said:**
> 
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

This last line should not be here.
In the terminal, please enter:
```
sudo nano -B /etc/apt/sources.list
```
When prompted, enter your password (it will not appear on the screen, hit enter after the password).

Then go down the bottom of the file and delete the last line.

Then save with CTRL-O
Exit with CTRL-X

```
sudo apt-get update
```
Do you still have an error ?

---

### Post by lsk3993 on 2009-11-23
> **NoaHall said:**
> Delete the last line.

Command  in terminal -
```
gksudo gedit /etc/apt/sources.list
```Then delete the last line, and save.
 Have you tried installing some very old software?
Yay that worked :D
Actually i was trying to install Adobe Reader because Evince won't open my pdf. It says "File type plain text document (text/plain) is not supported". 
I tried to install automatix2 because the download from Adobe's site wouldn't work for me

---

### Post by lsk3993 on 2009-11-23
Actually, I really should mark this thread solved... but how?

---

### Post by bapoumba on 2009-11-23
> **lsk3993 said:**
> Actually, I really should mark this thread solved... but how?

It's under Thread Tools, I just did it for you.

---

### Post by lsk3993 on 2009-11-23
> **bapoumba said:**
> It's under Thread Tools, I just did it for you.
Ah thanks, when I saw it marked solved I thought I magically did it somehow...

---

### Post by bapoumba on 2009-11-23
> **lsk3993 said:**
> Ah thanks, when I saw it marked solved I thought I magically did it somehow...

Almost, hehe ;)

---

### Post by Filipek on 2009-11-23
Oh, I haven't been here for 10 minutes or so and everything is solved it seems :-) Good for you mate!

---

### Post by scorp123 on 2009-11-23
> **lsk3993 said:**
> I tried to install automatix2  Never ever do that!

Automatix is a horrible piece of software (it breaks stuff and does more damage than good) and it's been obsolete for ages now.

---

### Post by NoaHall on 2009-11-23
Yes, indeed. Try Ubuntu Tweak, or maybe ultamatix(although, try not to use it, it's not great, but it does work.. a bit better than automatix.)

---

### Post by lsk3993 on 2009-11-26
> **The-Red-Baron said:**
> hello there.. new user too... have the same problems with the synaptic package... thanks.... here´s my list:

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
Just marked the thread as unsolved again... perhaps you should just make a new thread though?

---

### Post by bapoumba on 2009-11-26
I have moved the off topic post to its own thread and removed the OP's post quoting it.

Thanks for helping though, you can mark your thread as solved again :)

---

### Post by b_stockton13 on 2009-12-02
Hi i have been trying to figure out why sometimes things i install from the package manager cant be found, i have tried everything i can thing of from beagle to find command. if im overlooking something please clue me in. any help would be appreciated. thanks

---

### Post by CurlySurmudgeon on 2009-12-02
> **bapoumba said:**
> This last line should not be here.
In the terminal, please enter:
```
sudo nano -B /etc/apt/sources.list
```
When prompted, enter your password (it will not appear on the screen, hit enter after the password).

Then go down the bottom of the file and delete the last line.

Then save with CTRL-O
Exit with CTRL-X

```
sudo apt-get update
```
Do you still have an error ?

I'm having the identical problem.  After wrestling with many 9.10 new install problems I tried installing adobe flash because youtube wouldn't work.  Synaptic said that the latest was already installed and aborted.  Now I cannot get Synaptic to run with the same error msg: 

```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."
```

Where my situation differs is in /etc/apt/sources.list, mine ends with:

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
```

Which does not include the line of the original poster.  How do we know which line to delete in order to fix what seems to be a reoccurring problem?

--Thanks, Curly

---

### Post by bapoumba on 2009-12-03
@curly: please try editing the /var/lib/dpkg/status as specified in post #8 of this thread
[http://ubuntuforums.org/showthread.php?t=1285455](http://ubuntuforums.org/showthread.php?t=1285455)

---

