---
title: "Unable to open Synaptic package manager / Ubuntu software center"
date: 2011-10-24
forum: General Help
---

### Post by DrArroganto on 2011-10-24
When I open Synaptic package manager it gives this error:

E: Malformed line 59 in source list /etc/apt/sources.list ([http://packages.dfreer.org](http://packages.dfreer.org) is not an assignment)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

This hasn't worked since yesterday (After upgrading ubuntu)
And I have a red square with a white line on the middle.. Which say "A problem occurred when checking for the updates.", when I press it.

---

### Post by 2F4U on 2011-10-24
There seems to be a problem in your /etc/apt/sources.list and you have to correct it. I would suggest that you post the content so we can take a look at it.

---

### Post by Elfy on 2011-10-24
In that file you should only have lines that start wit #, deb or deb-src - anything else will cause it to fail.

You can open the file to edit it - I would backup first

In a terminal 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Then open the file to edit it, in a terminal again

```
gksudo leafpad /etc/apt/sources.list
```

Look at line 59 and on for errors

Once edited - close and save and update

```
sudo apt-get update
```

If you are not sure - copy and paste the sources.list here

---

### Post by DrArroganto on 2011-10-24
@2F4U This is what it says on sources.list

# deb cdrom:[Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main

@Forestpiskie

When I insert the first code, it doesn't do anything..

atte@Atte:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
[sudo] password for atte: 
atte@Atte:~$ 

And when I insert the second one..
It does the same thing..

And on the third one it gives the error that on line 59 there's something wrong whatever..

---

### Post by antiplex on 2011-10-24
> **DrArroganto said:**
> When I insert the first code, it doesn't do anything.. i bet it does, but only if you enter you password. it does a copy in the background so you can safely edit the original file.

> **DrArroganto said:**
> And when I insert the second one..
It does the same thing.. it does not the same thing but you might get asked for your password as well. if you enter it, a text-editor window showing the contents of the sources.list. here you should take a look at the mentioned lines.

> **DrArroganto said:**
> And on the third one it gives the error that on line 59 there's something wrong whatever.. probably because you did not apply any changes in step 2.

to me, these seem the lines that you should try commenting out by prepending a #-symbol to each: 

[INDENT]deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
[/INDENT]

then try again step 3

regards,
anti

---

### Post by DrArroganto on 2011-10-24
> **antiplex said:**
> i bet it does, but only if you enter you password. it does a copy in the background so you can safely edit the original file.

 it does not the same thing but you might get asked for your password as well. if you enter it, a text-editor window showing the contents of the sources.list. here you should take a look at the mentioned lines.

 probably because you did not apply any changes in step 2.

to me, these seem the lines that you should try commenting out by prepending a #-symbol to each: 
[INDENT]deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
[/INDENT]then try again step 3

regards,
anti

This is what happens if I don't give the password/incorrect

atte@Atte:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
[sudo] password for atte: 
Sorry, try again.
[sudo] password for atte: 

And this is  what happens when I do give it

atte@Atte:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
[sudo] password for atte: 
atte@Atte:~$ 

......

And I don't know what to do @

to me, these seem the lines that you should try commenting out by prepending a #-symbol to each: 
deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
deb [http://packages.dfreer.org]("http://packages.dfreer.org/") feisty main

---

### Post by Elfy on 2011-10-24
> atte@Atte:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
[sudo] password for atte:
atte@Atte:~$ This is correct - it's copied (cp) the original to the new filename,

Delete these lines - save and close

> deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main

Now run the 

sudo apt-get update 

in a terminal, if you get no more errors.

Those are very old repositories. 


When you say  
> And when I insert the second one..
It does the same thing..

It should open the file in a text editor.

---

### Post by DrArroganto on 2011-10-24
> **forestpiskie said:**
> 
Delete these lines - save and close

Well ****.. It says: "Can't open file to write" When I try to save :/ Tried to change the access on properties and it's not possible...

---

### Post by gsmanners on 2011-10-24
How about this:

```
gksudo leafpad /etc/apt/sources.list
```

---

### Post by DrArroganto on 2011-10-24
> **gsmanners said:**
> How about this:

```
gksudo leafpad /etc/apt/sources.list
```
Yes, thank you! :) Some files are repairing now.. I think it works tho.

---

### Post by Elfy on 2011-10-24
Gah - so sorry - didn't notice the xubuntu prefix - you'll have no gedit.

Thanks for catching that gsmanners. I should know better - I've not got gedit either ...

---

