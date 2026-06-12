---
title: "ubuntu 9.10: upgrade problem to firefox 3.6"
date: 2010-01-24
forum: General Help
---

### Post by mettaman on 2010-01-24
hello all,

1) i'm a ubuntu-newbie. i'm not computer illiterate --- but pls be patient.

2) for some days i tried to upgrade to firefox 3.6. similarly to the way described here

[http://www.unixmen.com/linux-tutorials/737-install-and-upgrade-to-firefox-36-final-on-ubuntu-linux](http://www.unixmen.com/linux-tutorials/737-install-and-upgrade-to-firefox-36-final-on-ubuntu-linux)

all went fine. 

but when i started firefox... it still numbers itself 3.5.7 & it does _not_ behave like 3.6 (i installed ff 3.6 on win7).

i tried a couple of approaches - none worked. here are results:

3a) UPDATE MANAGER

shows 5 packages to be installed from LP-PPA-ubuntu-mozilla-daily:

firefox, firefox-3.5 [a "dummy package"... whatever that may be], firefox-3.5-branding, firefox-branding (New install), firefox-gnome-support

if i hit "install updates"... i'll get a dreaded "Could not apply changes! Fix broken packages first."

-

3b) SYNAPTIC PACKET MANAGER

shows _no_ "broken packages". it _does_ show a couple of ff entries - among those a "firefox" entry, identified as version 3.5.7 & a "firefox-3.5" entry, also identified as version 3.5.7.

no... no trace of a ff 3.6 in SYNAPTIC

-

3c) TERMINAL

[CORRECTION: i made a copy/paste-mistake. it should read:]
when i run "sudo apt-get update && sudo apt-get install firefox-3.6"... result is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.6 is already the newest version.


when i continue "sudo apt-get update && sudo apt-get upgrade"... result is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  firefox firefox-3.5 firefox-3.5-branding firefox-gnome-support
The following packages will be upgraded:
  firefox-3.5-gnome-support xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
3 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


* * *

4) i'm clueless.

i considered uninstalling all ff-entries --- but that brings up some dependencies-warnings... so... before i create more havoc...

maybe a kind soul & experienced user will be able to offer a hint or direction :-)

thanks for your time, mind, attention

---

### Post by mikewhatever on 2010-01-24
No matter what you want to install, you'll have to deal with the broken package first. Run the following command in terminal:

sudo apt-get install -f

---

### Post by mettaman on 2010-01-24
i'm sorry,

i had a similar problem a couple of days ago. similar with regards to this error msg about "broken packages". it took me a couple of days to review dozens of different solutions...

so, i'm aware of this swiss-army-knife "sudo apt-get install -f".

but it does _not_ work. it does neither change the error msg in synaptic, nor does it change any state of withhold packages [see terminal msgs above], nor does it allow to upgrade to ff 3.6.

thanks.anyhow.mikewhatever 

> **mikewhatever said:**
> No matter what you want to install, you'll have to deal with the broken package first. Run the following command in terminal:

sudo apt-get install -f

---

### Post by akhilbehl on 2010-01-24
when you say you ran firefox.. how did you run it?

AFAIK firefox-3.6 will not show itself as firefox on your machine since ubuntu/firefox has not yet provided the branding for it..
it should run namoroka or something..

you should perhaps try to run 'namoroka' or 'firefox-3.6' in the terminal or the run dialog (Alt <F2>).

according to what you say it is already installed.. but is not showing up because it does not have its own 'profile' (whatever that is.. i picked up the word when i ran into a similar problem with firefox-3.5.4).

try that and see what it says..

---

### Post by lovinglinux on 2010-01-24
> **akhilbehl said:**
> when you say you ran firefox.. how did you run it?

AFAIK firefox-3.6 will not show itself as firefox on your machine since ubuntu/firefox has not yet provided the branding for it..
it should run namoroka or something..

Additionally, since recent changes in update policy, **firefox-3.6** package will not be installed. Instead, package **firefox-3.5** package will be upgraded. The package name won't change. So, to make sure you have Firefox 3.6 installed, start Firefox from the default launcher or using the command **firefox**. then got o the help menu in Firefox and open "About Namoroka" or "About Firefox". It should display the version of the running application.

> **akhilbehl said:**
> you should perhaps try to run 'namoroka' or 'firefox-3.6' in the terminal or the run dialog (Alt <F2>).

It doesn't work that way. Since **firefox-3.6** is not installed and **firefox-3.5** is upgraded to 3.6 instead, you should run the command **firefox** or **firefox-3.5**. I know, it's weird to run **firefox-3.5** to launch Firefox 3.6. But that is the way things are being doing right now.

> **akhilbehl said:**
> according to what you say it is already installed.. but is not showing up because it does not have its own 'profile' (whatever that is.. i picked up the word when i ran into a similar problem with firefox-3.5.4).

The profile has nothing to do with Firefox showing up or not, unless is corrupted. But then Firefox would probably not even start. A profile is where Firefox saves settings, passwords, cookies, extensions and so on. It resides in the user home directory, under the hidden folder ~/.mozilla/firefox. The same user profile can be and will be used after the upgrade and Firefox will take care of checking if the extensions are compatible with the new version. When you installed **firefox-3.5.4** using the same PPA, it created a copy of your profile under ~/.mozilla/firefox-3.5, but this behavior no longer applies. Firefox 3.6 will use the same profile of the default Firefox installation.

---

### Post by mettaman on 2010-01-24
dear akhilbehl, dear lovinglinux -

thx for direction :-) i just fumbled on & came across term "namoroka"... & that gave direction.

now it's running.

problem is: i can't say... what _solved_ issue ;-) [well, maybe i can't have it all... all the times :-)]

*

re lovinglinux. i learned about the incremental upgrades while looking through previous packages. ok, it made sense. but ff still identified itself as 3.5.7 --- though apt claimed 3.6 had been installed.

from that reasoning... it wasn't weird to conceive to start ff 3.5 --- but it just didn't work.

*

thanks again for comments. thanks a LOT! :-)

---

### Post by akhilbehl on 2010-01-24
@lovinglinux.. right.. thanks for the information.. i was going by the information i gathered when i had earlier run into a similar problem.. thanks for the clarifications.

btw.. did i say i am pretty new to linux-ubuntu.

---

