---
title: "UBUNTU  disaster"
date: 2009-07-13
forum: General Help
---

### Post by Jerriy on 2009-07-13
Just now I decided to upgrade from Intrepid Ibex to Jaunty... then after I finished and restarted the PC funny things started happening right away:

- The apps & Internet (Frfx) windows that I just opened don't appear to have a corresponding "rectangle" visible on the startup panel ("window list" 2.26.0)

- all stored shortcuts gone, including the ones on the F buttons

- Printscreen button isn't responding

- most amazing of all: all opened windows (and I mean ALL: whether it be installed apps., Internet or even dialogue popups) have no edges at all!!! They all appear for lack of a better word "shaved". An this means I am having a huge difficulty using my ubuntu! Just to make it clear: by "edge" I mean the top bar where the title of the page automatically appears and where on the top-left side is a standard drop-down menu and where on the top-right side are those three standard buttons: minimize, maximize and close [X] buttons.

---

### Post by Jerriy on 2009-07-13
Likewise the side and bottom of the edges are gone also. So I cant move any of the windows. And resizing is only possible from the "triangle" at the bottom-right corner and not from elsewhere on the edge of the windows/boxes.

---

### Post by JillSwift on 2009-07-13
It sounds like your window decorator or manager is crashing.

Is, by chance, your video card an ATI?

---

### Post by Ra-Hoor-Khuit on 2009-07-13
Two words for you (learn them, love them, LIVE them):

CLEAN.  INSTALL.

---

### Post by ibizatunes on 2009-07-13
Clean install, backup your dater, download and install 9.04 with 2 partitions one fore /home and / using ext4 file system, this will make your computer run faster
best of luck

---

### Post by Jerriy on 2009-07-13
This is exactly what I was afraid of - this is why I didn't upgrade when Jaunty appeard on April. 

I want to uninstall. Right now it is not possible for me to take the time and learn the basics of Ubuntu or linux. Weekend is the time for that. Right now I want to access my programmes and the internet ASAP
 
So my question is: how do I "un-upgrade"? I wanna go back to where I was: back to Intrepid

---

### Post by Jerriy on 2009-07-13
> **JillSwift said:**
> It sounds like your window decorator or manager is crashing.

Is, by chance, your video card an ATI?Nvidia

---

### Post by LewRockwell on 2009-07-13
new version and with it come the new graphical "enhancements" lol

you'll probably need to make some adjustments to suite your own tastes

it would be great if upgrades would leave you with your pre-upgrade settings and then just advise you that there were new "enhancements" that you might want to try out...instead of just making the new stuff the default...

go figure...

title is a little over the top though, since you're not dead in the water with all your data going up in smoke...

.

---

### Post by LewRockwell on 2009-07-13
> **Jerriy said:**
> Nvidia

in system or administration there is a selection called "hardware drivers" or something similar

you'll probably need to enable those drivers and everything will work properly then

.

---

### Post by Jerriy on 2009-07-13
I went to Control Center >> look and feel >> Windows

Then I just got slapped a red sign iconed message:[INDENT]**Cannot start the preference application for your windows manager**

Windows manager "unknown" has not registered a configuration tool [/INDENT]

---

### Post by 5nak3 on 2009-07-13
you may not need to clean instal...
That problem could be because compiz is not running properly to show the window decorator

try this in terminal

fusion-icon (or if you do not have it installed sudo apt-get install fusion-icon) then run fusion-icon in terminal

This should start up a program which is symbolized by a blue cube in the top task bar.

Right click that icon select your window manager (use metacity to be safe) and then that should work...if that doesn't try selecting reload window manager from the right click list.

Hope that helps...

---

### Post by scorp123 on 2009-07-13
> **Jerriy said:**
> Just now I decided to upgrade from Intrepid Ibex to Jaunty... then after I finished and restarted the PC funny things started happening right away ... most amazing of all: all opened windows have no edges at all!!! They all appear for lack of a better word "shaved" ... 

How exactly did you attempt to upgrade? Also --and this is a very important point: Did you use plenty of third-party repositories prior to the upgrade? Or was your 8.10 "Intrepid" upgrade pretty much "vanilla"?

Why I am asking: I had the very same behaviour you now experience a few releases ago ...

I used plenty of third-party stuff, e.g. "Beryl", "Emerald", and what not.

The point is this: 

If you stick to the official "Upgrade How-To" and do a "do-release-upgrade" then this upgrade process will disable all the third-party repos you were using. Meaning: Only the core OS will really be upgraded, all your third-party stuff (codecs, compiz plugins, themes, and whatnot) probably won't. 

What you have to do _BEFORE_ attempting an upgrade is to make sure that you have valid repo lists and replacements for _ALL_ your installed packages. Or you need to have equivalent replacements.

So when the upgrade finishes (or so it will claim) and you reboot for the first time: Go straight to your /etc/apt/sources.list.d/* folder and check all your repo lists there ... Chances are all those repositories got disabled (= there will be a "#" comment sign on each line) and the packages never got updated. So you have to uncomment all the relevant lines again and do a "sudo apt-get update && sudo apt-get dist-upgrade" to really make sure that these packages get upgraded as well (and of course: The URL's of all those repos have to point to the new release now, e.g. there should be the keyword "jaunty" everywhere ... )

Chances are that there will be a few 100 more updates to go.

If you use tons of third-party stuff and forget to take care of those repos before an upgrade you will likely end up with a broken system.

As for the question: "Clean Install" vs. "Upgrade" .... It depends. Upgrading "vanilla Ubuntu" always works in my experience. Upgrading a heavily tweaked Ubuntu with tons of third-party repos will work too if you take care of the repos before attempting the upgrade. Upgrading a heavily tweaked Ubuntu using "The Debian Way" (have repos point to the new release and then trigger "sudo apt-get dist-upgrade" ...) might work too but you will have to know what you're doing because there will be a few bumps along the road.

What you can do now:

My suspicion is that you used a lot of stuff from third-party repos (sorry if I am wrong...) and that this stuff didn'get properly upgraded. As your GUI doesn't seem to be working you will have to use the shell or a live CD. In any case:  Please check these files:
[LIST]
[*]/etc/apt/sources.list
[*]/etc/apt/sources.list.d/*.list
[/LIST]

Especially that last location might be interesting to check. Please make sure your repos are not commented out, and please also make sure that any third-party repo is pointing to the new release, e.g. keyword "jaunty" in its repo URL.

Once you have made sure the repos are uncommented please trigger these commands: ```
sudo apt-get update
sudo apt-get dist-upgrade

```

Chances are that now all of a sudden plenty of packages will want to upgrade as well ... And if all goes well this might fix your problems (as I said: I had the very same problem a few releases ago ...)

Or maybe I was guessing too much and I'm completely wrong? Sorry then :)

---

### Post by Jerriy on 2009-07-13
I just did that - terminal claimed fusion-icon wasn't installed so I installed it.

An now what - restart?

---

### Post by 5nak3 on 2009-07-13
if you have installed fusion-icon

in the terminal type

fusion-icon

Since it is now installed, it should run and as a result you should get a little blue cube on the top taskbar.

If you right click that you can try "reload window manager" and/or selecting metacity as your window manager

---

### Post by Jerriy on 2009-07-13
> **scorp123 said:**
> How exactly did you attempt to upgrade?Just by clicking the since April existing button at the top of the regular application-upgrade window/popup. 

> Also --and this is a very important point: Did you use plenty of third-party repositories prior to the upgrade? Or was your 8.10 "Intrepid" upgrade pretty much "vanilla"?

Why I am asking: I had the very same behaviour you now experience a few releases ago ...

I used plenty of third-party stuff, e.g. "Beryl", "Emerald", and what not.

The point is this: 

If you stick to the official "Upgrade How-To" and do a "do-release-upgrade" then this upgrade process will disable all the third-party repos you were using. Meaning: Only the core OS will really be upgraded, all your third-party stuff (codecs, compiz plugins, themes, and whatnot) probably won't. Well I of course did use third party stuff but some of which still seems to work so I have no Idea. Anyway since when is the standard parts windows/popups (like the minimize, maximize, close, move, resize) since when are those "third party" things? I thought they were as basic to graphical user interfaces as apple pie 

*confused*

---

### Post by onomou on 2009-07-13
I have had similar issues upgrading to previous versions of Ubuntu. As said before, it sounds like your window decorator is broken. You might try reinstalling the compiz package using aptitude. Also, are your graphics drivers up-to-date and from the Ubuntu repository? At least one time I broke my WM I had tried to use a binary straight from NVidia and had to spend a lot of time getting rid of all their files and reinstalling supported drivers before it worked again.

Agreed, it can seem that the windows decorator should be an integral part of the OS, but the nice thing is that it is modular so you can use Beryl or Compiz with Emerald etc. or something else if you want.

---

### Post by sdlynx on 2009-07-13
```
metacity&
``` will get your titlebars back

---

### Post by Jerriy on 2009-07-13
> **5nak3 said:**
> if you have installed fusion-icon

in the terminal type

fusion-icon

Since it is now installed, it should run and as a result you should get a little blue cube on the top taskbar.

If you right click that you can try "reload window manager" and/or selecting metacity as your window managerI don't see no blue cube anywhere.

If you by any chance mean the "go to desktop" button then it isnt' working either (but the firefox button on the same paned does open firefox... though again as I said the "open winsows display" on the panel is empty... as if I haven't opened anything!!

---

### Post by Jerriy on 2009-07-13
Terminal is open but I can't type anything on it!!! I have no idea what's going on

---

### Post by onomou on 2009-07-13
Can you login to another terminal by pressing ctrl+alt+F1 and reinstall compiz through aptitude that way? If nothing is working, you might want to reboot into recovery mode and try it that way.

---

### Post by Jerriy on 2009-07-13
> **onomou said:**
> I have had similar issues upgrading to previous versions of Ubuntu. As said before, it sounds like your window decorator is broken. You might try reinstalling the compiz package using aptitude.How does one do that when you can't type any damn thing inside the terminal?(except being able to click on the GUI menu at the top of the terminal window.

---

### Post by Jerriy on 2009-07-13
> **onomou said:**
> Can you login to another terminal by pressing ctrl+alt+F1 and reinstall compiz through aptitude that way? If nothing is working, you might want to reboot into recovery mode and try it that way.Thanks for the tip

Here is the message I get when I typed metacity&[PHP]Window manager error: Unable to open X display[/PHP]

---

### Post by Jerriy on 2009-07-13
Don't have enough time to continue with these "funny jaunty surprises" today - it's getting late... be back tomorrow

---

### Post by Tamlynmac on 2009-07-13
Not sure why this thread is in this section and not in one of the help sections? Logic suggest routing this to the appropriate help section would benefit the OP. As this is not a support section of the forum.

Just a thought.

---

### Post by pizza-is-good on 2009-07-13
[http://ubuntuforums.org/showthread.php?t=1201112](http://ubuntuforums.org/showthread.php?t=1201112)
 
Why is there so many threads about window manager problems? But more importantly, why are so many people having window manager problems?
 
Hope that helps

---

### Post by Crafty Kisses on 2009-07-13
If your Window Decorator is supposedly "crashing". Check a couple things out. Check if Window Decorations in the Compiz Manager is selected. Once you have done that, if you're using Emerald, just run:
```
emerald --replace
```
I haven't read the thread in detail, but just a thought.

---

### Post by scorp123 on 2009-07-14
> **Jerriy said:**
> Just by clicking the since April existing button at the top of the regular application-upgrade window/popup. That one has the same effect like a "sudo do-release-upgrade". It disables all third-party repos and will only update the core OS.

> **Jerriy said:**
> Well I of course did use third party stuff but some of which still seems to work so I have no Idea. Check those repo files again! You must update those files so each and every single one of them is now pointing to the correct release. And then check if those packages that came from those repos can be upgraded as well.

> **Jerriy said:**
>   Anyway since when is the standard parts windows/popups (like the minimize, maximize, close, move, resize) since when are those "third party" things? They are if you use third-party stuff such as compiz PPA's, emerald themes, or SVN versions of any GUI stuff.

> **Jerriy said:**
>  Here is the message I get when I typed metacity&[PHP]Window manager error: Unable to open X display[/PHP] Of course, you're not in a graphical environment anymore and therefore the command will not know what to do. It's like saying: "Ahumm, dude: I can't see no GUI here .... "

Workaround: Tell it where the GUI stuff is and trigger the command again, e.g. like this:
[LIST]
[*]Hit CTRL+ALT+F2 to get to a pure text terminal
[*]Login using your username and password (password will not be echoed back! Just keep tyiping!)
[*]Once you see the black & white terminal, type this into it:
[/LIST]
```
DISPLAY=:0.0 metacity &
```
... Now hit these keys: CTRL+ALT+F7 ... this should take you back to your GUI screen, and hopefully you would now have those window controls again.

---

### Post by Jerriy on 2009-07-14
> **pizza-is-good said:**
> [http://ubuntuforums.org/showthread.php?t=1201112](http://ubuntuforums.org/showthread.php?t=1201112)
 
Why is there so many threads about window manager problems? But more importantly, why are so many people having window manager problems?
 
Hope that helpsIt worked!!!

I came back to this thread and followed the next advice that showed up, which was your post pointing to that thread of yours. So I opened the Startup-Applications and added the two things ("compiz --replace" & "/usr/bin/fusion-icon")

Now I've got the window/popup title bar, prntscreen is also working and I've got my programmed shortcuts back! So Thanks a lot, pizza!

---

### Post by Jerriy on 2009-07-14
Hey 5nak3 I see that compiz fusion icon on the panel now... hehe.

So far so good - now let's see if all the applications are working...

---

### Post by Jerriy on 2009-07-14
> **scorp123 said:**
> Check those repo files again! You must update those files so each and every single one of them is now pointing to the correct release.That is going to be more complicated that I thought. I see that things have changed - look what I found after hitting the menu System > Administration > Software Sources

---

### Post by Jerriy on 2009-07-14
*post deleted*

---

### Post by Jerriy on 2009-07-14
How do I go about updating my third party apps?  I went back to one of yer previous posts and followed your advice and opened a full terminal and [COLOR="blue"]typed[/COLOR] the commands you provided - here are the results:```
home:~$ [COLOR="Blue"]/etc/apt/sources.list[/COLOR]
/etc/apt/sources.list: line 5: deb: command not found
/etc/apt/sources.list: line 13: deb: command not found
/etc/apt/sources.list: line 20: deb: command not found
/etc/apt/sources.list: line 36: deb: command not found
/etc/apt/sources.list: line 37: deb-src: command not found
/etc/apt/sources.list: line 39: deb: command not found
/etc/apt/sources.list: line 40: deb: command not found
/etc/apt/sources.list: line 41: deb: command not found
/etc/apt/sources.list: line 47: deb: command not found
home:~$ [COLOR="Blue"]/etc/apt/sources.list.d/*.list[/COLOR]
bash: /etc/apt/sources.list.d/medibuntu.list: Permission denied
home:~$ 

```

---

### Post by Jerriy on 2009-07-14
> **Codename said:**
> If your Window Decorator is supposedly "crashing". Check a couple things out. Check if Window Decorations in the Compiz Manager is selected. Once you have done that, if you're using Emerald, just run:
```
emerald --replace
```
I haven't read the thread in detail, but just a thought.
You're on Dapper - very smart of you ;)

---

### Post by Jerriy on 2009-07-14
Take a look at that medibuntu.list:```
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ jaunty free non-free # disabled on upgrade to jaunty
# deb-src http://packages.medibuntu.org/ jaunty free non-free # disabled on upgrade to jaunty
```What on earth mean "disabled on upgrade to jaunty??? I didn't ask anything to be disabled. When did disabling stuff come into it? Is the concept "backward compatibility" a non-existant phenomenon in Jaunty/Ubuntu/Linux? I thought I was updating an OS, i.e. I was bringing up-to-date a Disc Operating System. Or is there something else going on and my understanding of Linux is neanderthal?

---

### Post by cariboo on 2009-07-14
Third party repositories and ppas should be disabled when doing a distribution upgrade because of varying dependencies, packages from repositories other than default may use different versions of the defautl files causing problem with the upgrade. Once the upgrade is finished then you can then enable all the third party repositories and ppas and just run a normal update/upgrade.

---

### Post by Jerriy on 2009-07-14
By enable all the repos and ppas you mean tick all those "disabled" boxes below, right?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121066&d=1247585000[/IMG]

---

### Post by scorp123 on 2009-07-14
> **Jerriy said:**
> How do I go about updating my third party apps?  You open those files in an editor. They are not system commands!


> **Jerriy said:**
>   I went back to one of yer previous posts and followed your advice and opened a full terminal and [COLOR="blue"]typed[/COLOR] the commands you provided ...  See above: They are **_not_** commands but files that you're supposed to take a look at using an editor.

e.g. like this:
```
gksudo gedit /etc/apt/sources.list
```

And you obviously did not understand the meaning of this:
```
/etc/apt/sources.list.d/*.list
``` ... my bad. So I am going to spell it out for you: "*" (asterix or asterisk) is a so called "wildcard", a placeholder. It usually means "all". So when someone writes stuff such as ....
> Please go and check /etc/apt/sources.list.d/*.list ... ... then by this they mean:
> Please go and check all files named something-dot-list underneath the directory /etc/apt/sources.list.d/ .... 

Best thing would probably be if you could attach those files here so we could take a look and help you correct them. Re-enabling those files won't do you any good because they'd still be pointing to the repos for the old "Intrepid" release .... So we'd need to find the correct pointer to the "Jaunty" repos for each of those entries.

Can you do that please? Post your **/etc/apt/sources.list** and all files underneath **/etc/apt/sources.list.d/** here so we can help you correct those files?

---

### Post by Jerriy on 2009-07-14
> **scorp123 said:**
> Post your **/etc/apt/sources.list**Here it is:```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://mirror.noreply.org/pub/tor jaunty main
deb http://www.awxcnx.de/apt jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
# deb http://archive.ubuntu.com intrepid main universe
```As for the file underneath /etc/apt/sources.list.d that is "medibuntu.list" which i posted about earlier. That's when I found out and updated the whole thing (with sudo apt-get...) so now look and compare the content of medibuntu.list that I posted earlier and and compare that with this latest one:```
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free
```Does that look good? The main universe deb "http://archive.ubuntu.com intrepid" seems to be lacking a jaunty version. And I do need that for some installed applications

---

### Post by scorp123 on 2009-07-14
> **Jerriy said:**
>  Here it is: .... The main universe deb "http://archive.ubuntu.com intrepid" seems to be lacking a jaunty version. And I do need that for some installed applications In my opinion it should be OK to replace the keyword "intrepid" with "jaunty" there. Then execute this command and see if you get an error:
```
sudo apt-get update
``` ... If you do get an error, disable that line again, we'd need to do something different then.

As for your sources.list file, I have more or less similar entries, except I am based in Switzerland, hence I prefer to use the "ch.ubuntu.com" servers.

Here is my perfectly working sources.list file so you can take a look e.g. for comparison purposes:

```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ch.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ch.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ch.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ch.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse 
```

My medibuntu repo list looks like this:

```
## Medibuntu - Ubuntu 9.04 "jaunty jackalope"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free
``` ... If I am not mistaken that's the same like your's?

Apart from that I have repo lists for Google software, Opera, Compiz and a few other things. Are you interested in that? As I said in my previous posting: If ever you decide to upgrade to a new release (the next one would be "Karmic Koala") you'd have to make sure you find updated addresses for all those repo lists or else you will be left stranded with packages that did not get updated ... and this might cause the troubles you and me experienced here.

---

### Post by Jerriy on 2009-07-14
I do get an error. I replaced the "intrepid" bit on the deb "http://archive.ubuntu.com" but it didn't help. So I have disabled it. The rest is jaunty and seemingly working. So hopefully most of the appls. are now updated and, we'll see in the coming time if I bump into an appl. that isn't working...

---

### Post by scorp123 on 2009-07-14
> **Jerriy said:**
> I do get an error. I replaced the "intrepid" bit on the deb "http://archive.ubuntu.com" but it didn't help. And if you add your country code to that one? e.g. change ....
```
http://archive.ubuntu.com
``` ... into ... ```
http://be.archive.ubuntu.com
``` (you're in Belgium, right?)

---

### Post by Jerriy on 2009-07-15
Nope! that address isn't working - and the same base level domain combined with other 2-letter country-codes don't work either. Dunno what is going on.

---

### Post by Jerriy on 2009-07-15
I found a new funny jaunty problem: I can't switch off my computer! You probably think it's a joke but I'm serious: the "shut down" menu option that is available on the panel does NOT shut the computer. It only starts a timer!

---

### Post by Jerriy on 2009-07-15
The disaster continues: I dunno what happened but Jaunty suddenly "switched off" my "delete" key on my keyboard. I can't delete anything now. I'm now using backspace only. 

Before you assume that the keyboard is mechanically broken lemme tell you that the keyboard is in a perfect working condition. This never happened when I used intrepid, until 2 days ago) and is not happening in Windows Vista (which is also installed).

How on earth do these funny things happen? I didn't even knew these things were possible. Just switching off one key - lol

---

### Post by ramnarayan on 2009-07-15
> **Jerriy said:**
> I found a new funny jaunty problem: I can't switch off my computer! You probably think it's a joke but I'm serious: the "shut down" menu option that is available on the panel does NOT shut the computer. It only starts a timer!

did you allow the 60 second time to go off / or did you try and press the shutdown button - both work (or should work)

---

### Post by Jerriy on 2009-07-15
> **ramnarayan said:**
> did you allow the 60 second time to go off / or did you try and press the shutdown button - both work (or should work)I pressed the shutdown button on the panel (that thing at the corner of the desktop panel where you can pull a dropdown menu and then all the options popup (options like shutdown, restart, hibernate, suspend and so on) 

That's the funny part of this whole thing: before the update Jaunty (i.e. when I was on Intrepid) I did NOT allow any automatic switchoff option. That option was off. When I pressed "shutdown" it used to immediately shut the whole computer. That is how it was before. Jaunty however seems to have completely ignored my previous setup and installed itself with it's own set of defaults. Now the funny thing is this: Why on earth is Jaunty's shutdown default on a 60 second timer? Who came up with this "brilliant" idea to make a timer an exclusive computer shutdown default?

---

### Post by Jerriy on 2009-07-15
Can somebody please tell me what is going on? 

How do I restore the "delete" button????? 

Thx in advance

---

### Post by ubudog on 2009-08-08
Back up your data, and do a clean install.  It always works. :)

---

