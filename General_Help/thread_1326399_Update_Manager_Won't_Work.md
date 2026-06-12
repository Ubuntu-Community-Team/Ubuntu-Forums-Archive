---
title: "Update Manager Won't Work"
date: 2009-11-14
forum: General Help
---

### Post by ukapolog on 2009-11-14
Upon using my update manager I got the following message:

Could not initialise the package information.

An unresolvable problem occurred while initialising the package information.
Please report this bug for the 'update-manager' and try to include the following error message:
'E:type 'sudo' is not known on line 56 in source list /etc/apt/sources.list,E: the list of sources could not be read.

Can anything be done about this? Or should I just delete the whole of Ubuntu??

---

### Post by ukapolog on 2009-11-14
I am now told to "Go to repository dialogue to correct the problem."

I am new to Ubuntu, I cannot find such a thing as the "repository dialogue." I thought it might be in the Synaptic Manager but that does not even allow me in whilst the error occurs.
I am bound to ask: *Why doesn't Ubuntu make some of these things simpler??*

---

### Post by toammann on 2009-11-14
Ok, you can do the following: first type ```
sudo kate
``` or ```
sudo mousepad
``` or just sudo and the name of whatever editor you like into the Terminal. You find it in Accessories.

You then enter the following:

```
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
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

and then you save it to /etc/apt/sources.list

---

### Post by toammann on 2009-11-14
...the graphical tool is somewhere near System/Settings/Software Sources. I'm not sure, because I'm using Xubuntu and probably have names that differ a little. You will see a dialog to check and uncheck different software sources like main, backports, universe, etc. Just uncheck and recheck them again. I hope that will create a file like the one above.

What I told you above, should work too. It's a crude hack, but that will let you use the package manager tools again. Later you can then use them to reconfigure the package repositories back to what ever you like.

---

### Post by nikgare on 2009-11-14
You appear to have (inadvertedly) typed the word **sudo** it line 56 in the file /etc/apt/sources.list.

Please post your sources.list file here.

---

### Post by ukapolog on 2009-11-14
Wow! I'm still struggling with this. I just noted that Ubuntu deprives me of my right-click 'select all' facility and my mouse doesn't want to highlight just bits at a time.

I opened gedit easily enough but so far have got no further.

Why does Ubuntu not allow 'select all' on the mouse right-click?

---

### Post by ukapolog on 2009-11-14
Okay, I think I did all that but no difference has been made, I still get the error message.
Do I need to restart?
I will try restarting.

---

### Post by ukapolog on 2009-11-14
No change on restart.

There must be some easier way of doing this??

Ubuntu remains perfectly useable but I have no functioning update manager which I am going to need again at some point.

---

### Post by jeb800e on 2009-11-14
Try going to the Synaptic Package Manager. If you can get into it, go to Edit < Fix Broken Packages

---

### Post by ukapolog on 2009-11-14
Nope. It doesn't allow me in.
But thanks to you all for your advice, but it's looking a bit hopeless isn't it?
 
Any further suggestions appreciated.
 
 
ukapolog

---

### Post by ukapolog on 2009-11-14
When I try to get into synaptic package manager, I am refused entry but I am told to go to the 'repository dialogue' to fix the problem.

Where the heck is that??

---

### Post by jeb800e on 2009-11-14
There was a special prompt to put into the terminal to fix this problem... I know. I had a little similar problem on one of my PCs... but I forgot it. Let me try to find it and maybe you can get your Ubuntu PC running normally again.

---

### Post by jeb800e on 2009-11-14
Prompt:

sudo aptitude

Click "b" on your keyboard to search for broken packages.
If nothing shows up, click the "Packages" tab on the third line, under the command menus and keys. Now, click "g" on your keyboard. A list should show. Click "g" again.
(You may need to become Root by clicking "Actions", and click "Become Root".)

Once done, click on "Actions", and click "Quit". Type "exit".

---

### Post by jeb800e on 2009-11-14
Did you try it?

---

### Post by ukapolog on 2009-11-14
Sorry but I had to go away and get some rest.

I did what you suggest. Yes, four errors come up in red, all marked E:
But I clicked on Actions, followed by quit. But the errors still remain.

---

### Post by wilee-nilee on 2009-11-14
If you want to post the at/sources list in the terminal type

sudo gedit /etc/apt/sources.list 

Then be careful this opening to edit. Copy it to a new gedit or just post a copy and paste on the thread, hit save before you close the source list

---

### Post by ukapolog on 2009-11-14
Okay, here it is:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
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
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
 deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
sudo apt-get update
 sudo apt-get install ubuntu-tweak

---

### Post by wilee-nilee on 2009-11-14
The last two lines need to be remove the sudo update and the sudo ubutu tweak. so open it again with the 

sudo gedit /etc/apt/sources.list

Then remove those two lines at the bottom hit save and then run,

sudo apt-get update 

in the terminal. 
If you want to add the launchpad ppa of ubuntu tweak to the list let me know but you can add a tweak repository off the web but I think these are for previous distro's before karmic. Ubuntu tweak is a 3rd party so it has to be added to the source list for regular updates, but it can be loaded I think as a stand alone program.

So here is alink to the unstable Ubuntu Tweak PPA I have never found it to be unstable but it is the development ppa.
[https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa](https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa)

So you put the deb http links on the site at the bottom of that apt/source list, then copy the key byclicking on it and saving in a gedit file in home then adding the key to the software sources under add in the 4th tab I think.

I am assuming you don't have Ubuntu tweak installed so after putting the links in and setting up the key in software sources run the sudo update command again and the sudo apt-get install ububtu-tweak. There is actually easier ways to this especially in Karmic with adding repositories and keys but I haven't looked at these easier ways.

---

### Post by ukapolog on 2009-11-14
Wow!! You are a clever man, sir.
Your recipe worked like magic!
Only thing now is I am going to be wary of updating or adding anything.
Thank you very much.

ukapolog.

---

### Post by jeb800e on 2009-11-14
Well, after the four errors show up in the Terminal, you have to click "g" on your keyboard again to fix the problem(s).

---

### Post by ukapolog on 2009-11-15
Yes, I did try clicking on 'G' again to fix the problem yet the problem remained.
Anyhow it is fine now.
Thanks to all for your considerable patience and help.
ukapolog

---

### Post by toammann on 2009-11-16
Can you type ```
sudo apt-get update
``` into a Terminal and post the output here? Maybe I can help you then.

---

