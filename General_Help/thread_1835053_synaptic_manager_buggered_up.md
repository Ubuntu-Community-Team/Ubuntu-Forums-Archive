---
title: "synaptic manager buggered up"
date: 2011-08-28
forum: General Help
---

### Post by GreenEU on 2011-08-28
I tried to load elegant-gnome following instructions on a website and have only succeeded in fouling up my synaptic package manager. I'm a complete beginner, alas, and now feel like a right idiot.

Details: ubuntu 11.04 on a Dell laptop

error message:
E: Type ‘main’ is not known on line 1 in source list /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

etc/apt/source.list is totally blank. 

I have natty on my netbook and have tried to overwrite the source list with what is on the netbook (which is unspoiled as I run minimally on that), with the result that the system tells me I do not have the requisite permissions.

Help!

---

### Post by t0p on 2011-08-28
To copy a sources list file from one machine to another, make sure you use **sudo** to override permissions issues (or **gksudo** if you're doing all this via GUI.

It would be interesting to know what you actually *did* to mess up like this.  Could you post here the instructions you followed, or at least give us a link to the web page that told you what to do.

---

### Post by GreenEU on 2011-08-29
The instructions I was following are [here]("http://www.youtube.com/watch?v=tm0mgV3TcXQ"), but that gives no clue about getting to a blank sources list - I have no idea how that happened - it was populated the first few times I looked at it, then it was blank, though I never pressed 'save' on a blank page.

I don't suppose you'd take pity on a newcomer and explain what SUDO instruction to use to override permissions? Pretty please?

---

### Post by coffeecat on 2011-08-29
I've watched the video you linked and I have to say that is about the silliest howto I've seen in a long time. They get you to open Synaptic to edit the ppa list file and then close Synaptic to apt-get update, upgrade and then install. Bizarre. Did you see the blatant typo in the terminal? Anyway....

> **GreenEU said:**
> error message:
E: Type ‘main’ is not known on line 1 in source list /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list

This is easily fixed.

> **GreenEU said:**
> etc/apt/source.list is totally blank. 

That's possibly because there is no /etc/apt/source.list. The main source file is /etc/apt/sources.list. Leave it alone. Or if you did mean /etc/apt/sources.list, please confirm.  

Navigate to /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list in a file browser, right-click on it and "Open with Text Editor". Copy and paste the contents into your post. The file will open read-only so you can't damage it. Once I've seen the contents of the file I should be able to tell you how to fix it.

Also - navigate to /etc/apt/sources.list (with an S) and double-check it in the same way. Please let us know whether you were looking for /etc/apt/source.list or if /etc/apt/sources.list really is blank.

**EDIT**: while you are in the /etc/apt folder, and if your /etc/apt/sources.list really is blank, look for a file called sources.list.save. Do you have one?

---

### Post by GreenEU on 2011-08-29
> **coffeecat said:**
> 
That's possibly because there is no /etc/apt/source.list. The main source file is /etc/apt/sources.list. Leave it alone. Or if you did mean /etc/apt/sources.list, please confirm.  


Apologies, I meant sources.list. It's blank.

> 
Navigate to /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list in a file browser, right-click on it and "Open with Text Editor". Copy and paste the contents into your post. The file will open read-only so you can't damage it. Once I've seen the contents of the file I should be able to tell you how to fix it.


It has one word: main. Nothing else.

> 
**EDIT**: while you are in the /etc/apt folder, and if your /etc/apt/sources.list really is blank, look for a file called sources.list.save. Do you have one?

Yes:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party 
## developers who want to ship their latest software. 
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 

## Major bug fix updates produced after the final release of the 
## distribution. 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party 
## developers who want to ship their latest software.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main

---

### Post by coffeecat on 2011-08-29
> **GreenEU said:**
> It has one word: main. Nothing else.

That explains why you were getting a parsing error with /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list. That is completely non-functional. I believe I know why that is like that, but I'll get back to you on that one. In the meantime, simply delete the file with:

```
sudo rm /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list
```

I suggest you copy and paste that command into the terminal. You use ctrl+shift+v to paste in the terminal.

With regard to your main sources.list file, you can simply copy the sources.list.save version to get a working sources.list. In the terminal:

```
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
```

Once you've run those two commands, run:

```
sudo apt-get update
```

.... and post back if you get any errors. You won't have the elegant-gnome ppa working, but I'm going to do some experimenting on that, and I'll get back to you.

---

### Post by coffeecat on 2011-08-29
> **coffeecat said:**
> I'll get back to you.

That didn't take long. :)

I'm not quite sure how the elegant-gnome list got messed up, nor how your main sources.list was blanked out, but it should be easy to get the elegant-gnome ppa working. You should have a /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list.save file. If you do, post the contents and I'll show you how to edit it manually to enable the elegant-gnome ppa.

---

### Post by GreenEU on 2011-08-29
> **coffeecat said:**
> . and post back if you get any errors. 


No errors - that worked a treat, thanks. :)  Now I've decided to return to Linux and stick with it, I need to pick up the manual and start mastering some of the coding, as the syntax is so simple. Your patience is appreciated!  

> 
You won't have the elegant-gnome ppa working, but I'm going to do some experimenting on that, and I'll get back to you.

Heh - that would be fun. The crap YouTube vid was all I could find about getting it onto natty. There's a fair amount around about getting it onto Maverick or Lucid, and I hear it might come as a standard option on Oneiric.

---

### Post by coffeecat on 2011-08-29
> **GreenEU said:**
> Heh - that would be fun.

You missed my post at #7. :) Post the contents of the /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list.save file and we'll take it from there.

---

### Post by GreenEU on 2011-08-29
Whoops!

OK, this is the elegant-gnome file:


deb [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu) natty main

---

### Post by coffeecat on 2011-08-29
> **GreenEU said:**
> Whoops!

OK, this is the elegant-gnome file:

deb [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu) natty main

For some reason best known to the ppa developer, they want you to edit the file to reference maverick even though you are running natty. What you do is, from a terminal:

```
gksudo gedit /etc/apt/sources.list.d/elegant-gnome-ppa-natty.list.save
```

It will open in a text editor with adminstrative privileges, so that you will be able to edit it. Now change it so that it reads as follows:

```
deb http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu maverick main
```

Now choose "save as" from the file menu, and save it as "elegant-gnome-ppa-natty.list". (No quotes.) Close the text editor, and run:

```
sudo apt-get update
```

If you get any errors, post them. If not, you should be able to install the elegant-gnome theme now. I hope it's worth it! :wink:

---

### Post by GreenEU on 2011-08-31
Sorry about delay, busy elsewhere. Worked a treat again. Many thanks! :D

---

