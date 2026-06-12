---
title: "Flash buttons are sometimes unresponsive"
date: 2009-10-31
forum: General Help
---

### Post by Mike_IronFist on 2009-10-31
I'm liking NVIDIA's new drivers, and as far as Adobe goes, I dig that Flash almost works right! ...except for an extremely frustrating issue - when I watch Youtube vidoes, visit flash sites like Homestarrunner.com, etc, sometimes, or all times for certain flash stuff, I can click something, and it will indicate that it was clicked, but it won't do anything! Youtube is hit and miss, as is Hulu, with some videos always working, and some never responding to any clicks and forcing me to use the keyboard to control the videos. On [www.homestarrunner.com](www.homestarrunner.com) I can't even click "Come on in" and get a response.

Is there any way to make this issue go away? I don't seem to see any other users reporting this issue, so it seems to be isolated to just me...

---

### Post by rifak on 2009-10-31
ahhh yes!! someone else with this problem..i've been searching for a while now and have come up with nothing. one question though: does this happen in firefox for you? i ask this because for me, everything works fine in firefox, but it's google chrome that i get the unresponsive button-clicking. your homestarrunner.com link works in firefox, but it will not work in chrome for me. but to be clear, i can see the flash animation, but i cannot click anything or interact with the buttons (in chrome). so yes, i get this problem but only in chrome...firefox works fine for me.

---

### Post by Mike_IronFist on 2009-11-01
> **ego-sum-deus said:**
> ahhh yes!! someone else with this problem..i've been searching for a while now and have come up with nothing. one question though: does this happen in firefox for you? i ask this because for me, everything works fine in firefox, but it's google chrome that i get the unresponsive button-clicking. your homestarrunner.com link works in firefox, but it will not work in chrome for me. but to be clear, i can see the flash animation, but i cannot click anything or interact with the buttons (in chrome). so yes, i get this problem but only in chrome...firefox works fine for me.

It happens for me in ALL browsers, Firefox, Galeon, etc. etc.

(off-topic: "I-am-God". Are you?)

---

### Post by rifak on 2009-11-02
> **Mike_IronFist said:**
> It happens for me in ALL browsers, Firefox, Galeon, etc. etc.

(off-topic: "I-am-God". Are you?)

it's written in words, so it has to be true.

---

### Post by sn4re on 2009-11-02
I am having the same problem (animation etc. plays, just nothing happens when I click on buttons). Have only tried in firefox. I am using Adobe's Flash (non-free). Didn't have this problem before - just started today.

---

### Post by coffeecat on 2009-11-02
Are you all using 64-bit Ubuntu? I had a similar issue with some, but not all, flash sites with the repo version of flashplugin-nonfree. This is fairly well known. One option is to follow this howto:

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

It involves uninstalling all of your present flash player, downloading the tar.gz of the latest alpha version, unpacking the .so file from this and putting this .so file in a 'plugins' folder that you make in ~/.mozilla. Don't worry that it's seemingly for Intrepid. It worked for me in Karmic.

But be aware that this is an alpha version of the Adobe player.

---

### Post by P4man on 2009-11-02
Im having it too on 32 bit ubuntu. Been having it since jaunty at least, and maybe I always had. On some sites for instance the full screen button or the links to other clips will not work. I figured it was due to the youtube player they are using to wrap the flash video

---

### Post by lbedubourg on 2009-11-02
Same problem here, only with google-chrome, 32 bit.

After some investigation, changing the flash element's 'wmode' param modify the behaviour.

wmode=window produces the bug

It is the default wmode value and it is  impossible to activate flash buttons and stuff on most flash movies because the mouse button event does not get to flash.

wmode=transparent and wmode=opaque seems to fix the problem.

---

### Post by rifak on 2009-11-02
> **lbedubourg said:**
> Same problem here, only with google-chrome, 32 bit.

After some investigation, changing the flash element's 'wmode' param modify the behaviour.

wmode=window produces the bug

It is the default wmode value and it is  impossible to activate flash buttons and stuff on most flash movies because the mouse button event does not get to flash.

wmode=transparent and wmode=opaque seems to fix the problem.

could you elaborate more on how one could go about doing this? or is this something that is only on the dev end of things. well, whatever it is, i would love to try and get this fixed

---

### Post by nevermind86 on 2009-11-02
yes, please elaborate! I am having this problem as well :(

---

### Post by P4man on 2009-11-02
curious too. If its in the html/javascript, would it be something we could fix with greasemonkey?

---

### Post by lbedubourg on 2009-11-03
Well wmode is an HTML attribute/param for flash animations, this parameter can have different values and there is a bug (at least in google chrome) which prevent mouse clics when this attribute's value is set to 'window' which is the default value when not specified.

The user cannot do anything but report this bug with as much information as possible to developpers... 

Which I'd like to do but I am not yet sure if this bug is related to a new version of google-chrome or should be reported to some ubuntu maintainer since it seems to be related to the karmic upgrade.

---

### Post by lbedubourg on 2009-11-03
I found a workaround after reading this bug report :

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/442216](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/442216)

**Disabling compiz fixed this problem in google chrome.**

---

### Post by Digikid on 2009-11-09
Bumping this up because I need a solution for this in Firefox...Karmic 64 Bit.  Flash is useless.  Reinstalling Flash did nothing to help the issue.

---

### Post by coffeecat on 2009-11-10
> **Digikid said:**
> Bumping this up because I need a solution for this in Firefox...Karmic 64 Bit.

Have a look in my earlier post in this thread. Go to the softpedia link.

There's just one slight amendmend for Karmic to that howto that you might need. When I marked nspluginwrapper for complete removal, it wanted to take acroread out as well. OK if you don't have acroread, but tedious if you do. So I simply uninstalled flasgplugin-installer. Now download the libflashplayer-10.0-32.18.linux-x86_64.so.tar.gz file from the link in the howto. Extract it - there's just a single libflashplayer.so file. Create a ~/.mozilla/plugins folder and move libflashpayer.so into it. Restart firefox.

Although that's a 64-bit alpha, it seems to work better on 64-bit systems that the repository wrapped 32-bit version. But keep an eye on things. Hopefully, it will go final in due course and we'll be able to get a repo installed 64-bit non-free player. Er - hopefully. :|

---

### Post by Jbike on 2009-11-10
Just so that I am counted statistically, I to have fallen victim to the bug, but for me only on my brand new 64 bit Athlon duel core. Additional sties where the buttons do not work are Pandora and play.clubpenguin.com. I am also really interested in an official "fix"  ...  Flash is so ubiquitous that I would think that this should be a top priority problem!

Jbike

---

### Post by coffeecat on 2009-11-10
> **Jbike said:**
> I am also really interested in an official "fix"  ...  Flash is so ubiquitous that I would think that this should be a top priority problem!

Jbike

Unfortunately an "official" fix will have to come from Adobe. The non-free flash plugin is proprietary. There is nothing the open source community, including Ubuntu, can do about that, except for what they have done: create a wrapper to be able to use the 32-bit flash player in 64-bit systems.

Unfortunately, that creates problems on some sites as you have found. The alternative is to use the 64-bit alpha as I have just described. I'm afraid we're at the mercy of Adobe.

---

### Post by 3rdalbum on 2009-11-10
I'm getting this problem with the 64-bit alpha. I've definitely noticed it in Opera, and I think I've seen it happen in Firefox too.

This really is a pretty horrible bug. Nothing I've seen has stopped the problem yet. The bug report linked to is completely unrelated (it's about slow performance, not about the button clicks not reaching Flash).

---

### Post by awilkins on 2009-11-10
I don't think this is the flash plugin ; I think it might be the same underlying problem as 

[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/443004](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/443004)

In that AFAIK, Flash 10 on Linux requires GTK and the behaviour is the same - buttons that "press" but do not respond.

Try starting your browser in a terminal thus :

```

export GDK_NATIVE_WINDOWS=1
firefox
```

.. although I just uninstalled the distribution version and installed the 64-bit version which seems to work better.

---

### Post by _khAttAm_ on 2009-11-10
I also face it sometimes. And it works when I hold on the Shift key while clicking. I'm on 64bit Ubuntu with 64bit flash plugin for firefox 3.5.4.

---

### Post by megamania on 2009-11-10
Disabling Compiz fixes the problem for me (9.10 64-bit).

However, I can live with using the keyboard (TAB+Enter to play-pause) when the mouse doesn't work...

---

### Post by Digikid on 2009-11-10
Thanks for that shortcut.  Did not know about that.

---

### Post by H4F on 2009-11-10
any other workaraun beside stoping compiz. ?

---

### Post by Delvien on 2009-11-11
I am also experiencing this.. for a while i thought I was the only one spam clicking play... and then blaming hulu.

---

### Post by Delvien on 2009-11-11
temp work around quoted from :[http://ubuntuforums.org/showthread.php?t=1275500&page=2](http://ubuntuforums.org/showthread.php?t=1275500&page=2)


>  Here is a bug report on the problem.
[https://bugs.launchpad.net/ubuntu/+s...ee/+bug/410407](https://bugs.launchpad.net/ubuntu/+s...ee/+bug/410407)

Switching from metacity to compiz makes the bug go away for a lot of people, including me. But this was not a workaround I could use while this gets fixed. But never fear, there is a better way around this bug.
Go to the page with the Flash.
Right-click outside the Flash content and keep the button depressed
Move your cursor just enough to where a Left-click will cause the menu to go away (still with the Right button held down)
With the Right button held down you can use the Left-click to interact with the Flash buttons as normal. (ex. play and pause your Flash movies) 

---

### Post by H4F on 2009-11-11
> **Delvien said:**
> temp work around quoted from :[http://ubuntuforums.org/showthread.php?t=1275500&page=2](http://ubuntuforums.org/showthread.php?t=1275500&page=2)

wow that  looks weird. but thanks.

---

### Post by robert114 on 2009-11-14
that work-a-round worked here too! Thanx, but it's not a solution for me. 

Yet another annoying problem for Linux here. Hope my friends won't use flash-pages soon.

Robert

---

### Post by fakeollie on 2009-11-14
Not only am I getting the dreaded non-responsive flash buttons and elements, sound is also randomly failing (demanding the browser be restarted in order to work again).

This flash sound issue happened to me before on hardy, was fixed by jaunty and now it's back. 

OH JOY.

---

### Post by Colonel Kilkenny on 2009-11-17
Prerelease of Flash 10.1 seems to be fixing the problem where Flash doesn't respond to clicks. Available at labs.adobe.com

edit. I take it back. Problem is still present with some flash objects...

---

### Post by Jbike on 2009-11-19
I concur If anyone has the solution, detailed instructions would be greatly appreciated.

Thanks, Jbike

---

### Post by H4F on 2009-11-19
> **Jbike said:**
> I concur If anyone has the solution, detailed instructions would be greatly appreciated.

Thanks, Jbike

The solution for me was to disable compiz.
System-preference-apperance-visual_effects-NONE!!

---

### Post by Jbike on 2009-11-20
That is a good short term solution... 

Jbike

---

### Post by Ric_NYC on 2009-11-21
> **Colonel Kilkenny said:**
> Prerelease of Flash 10.1 seems to be fixing the problem where Flash doesn't respond to clicks. Available at labs.adobe.com

edit. I take it back. Problem is still present with some flash objects...



Any solution for the problem?

---

### Post by Hesediel on 2009-11-21
i have the same problem i'm on 9.10 64 bit...but... when i have installed the sistem all worked fine until today when i have installed the package ubuntu-resctricted-extras  and now...i have purged it..but the problem sill stay :(

---

### Post by Irishpolyglot on 2009-11-21
For anyone interested, when I disabled my Nvidia drivers the problem disappeared. This unfortunately makes any videos grainy so it's not a practical solution. For the moment I'm right clicking then left clicking as suggested above.
I tried to install the Alpha version of the 64 bit flash, but it just crashes the 'fox. Hopefully there will be a fully operative version that doesn't piggy back off the 32 bit one soon enough!

---

### Post by Hesediel on 2009-11-21
But...not in all videos there is the problem...for example:

in this video i didn't have the problem

[http://www.youtube.com/watch?v=1w2pVCtftuw](http://www.youtube.com/watch?v=1w2pVCtftuw)

or this

[http://www.youtube.com/watch?v=0ORfOi9jyo4](http://www.youtube.com/watch?v=0ORfOi9jyo4)


but if i try to open this one 

[http://www.youtube.com/watch?gl=IT&hl=it&v=bZLSKTClPt0](http://www.youtube.com/watch?gl=IT&hl=it&v=bZLSKTClPt0)

here is the problem, and if i do the right button on those videos the menu that comes out is different in those, so is different also the type of player...why?

---

### Post by Hesediel on 2009-11-22
This solved the problem for me, i don't konw if this can help some others:

remove all flash plugin and add this repository


remove flash plugin -> ```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```

add repository -> ```
sudo add-apt-repository ppa:debfx
``` 

then install:

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

This is a one command string:

```
sudo add-apt-repository ppa:debfx && sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper && sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

so this solved for me, the problem of non working flash buttons. Let me know
thanks to dr.gonzo

---

### Post by drakkahn on 2009-11-23
The above solution fixed the button issue, but now my browser crashes when viewing hulu.
I haven't tried the other solutions on here yet...

Running 9.10 64bit

---

### Post by Hesediel on 2009-11-23
> **drakkahn said:**
> The above solution fixed the button issue, but now my browser crashes when viewing hulu.
I haven't tried the other solutions on here yet...

Running 9.10 64bit



and trying this repository?


deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main

---

### Post by drakkahn on 2009-11-24
> **Hesediel said:**
> and trying this repository?


deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main

Yes, it still freezes.  Works great on Youtube, but not HULU.  It gets through the beginning commercial and when the show should start the browser just closes :(

---

### Post by Hesediel on 2009-11-27
This seems to fixed the problem, like the freeze on full screen that appears with others solution posted before

1)Uninstall your flash plugin

2)then uninstall from synaptic the package:

ia32-libs


3)Then install the jaunty version from here 

[http://packages.ubuntu.com/jaunty/amd64/ia32-libs/download](http://packages.ubuntu.com/jaunty/amd64/ia32-libs/download)

4)Then always from synaptic reinstall the adobe flash plugin / flash installer
after reinstall programs like skype and wine and all programs that will be removed from point 2.

---

### Post by Xebec on 2009-11-28
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

---

### Post by dreadood on 2009-11-28
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

That seems to work for me, thanks! ;)

dreadood

---

### Post by H4F on 2009-11-28
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

that didn't help me ?

---

### Post by ozymand1as on 2009-11-28
Worked perfectly!
Thanks!

---

### Post by a!man_96 on 2009-11-28
I never had this type of problem yet..
Guess i had to prepare for it..

---

### Post by CRIMPS on 2009-11-28
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```


This seemed to work for me as well.  Thanks!!!

---

### Post by H4F on 2009-11-28
do I have to restart after that ?

---

### Post by Jbike on 2009-11-29
Ok, I must be missing the boat. When I run the command [COLOR="Red"]" gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer "[/COLOR] I end up with an empty file. When try to navigate directly, I get as far as: /usr/lib/nspluginwrapper... What am I missing? I expected to find a file with existing code so that I could add:  export GDK_NATIVE_WINDOWS=1?

Help!  Thanks, 
Jbike

---

### Post by dreadood on 2009-11-29
> **Jbike said:**
> Ok, I must be missing the boat. When I run the command [COLOR="Red"]" gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer "[/COLOR] I end up with an empty file. When try to navigate directly, I get as far as: /usr/lib/nspluginwrapper... What am I missing? I expected to find a file with existing code so that I could add:  export GDK_NATIVE_WINDOWS=1?

Help!  Thanks, 
Jbike

Have you got all flash packages (still) installed?
you need the 32bit version for this to work

flashplugin-installer
nspluginwrapper

first remove the 64bit flashplayer, or delete the 64bit .so plugin file if you installed the 64 bit flash plugin manually (~/.mozilla/plugins)
then install the flashplugin-installer from synaptic.
 
dreadood

---

### Post by Jbike on 2009-11-29
Thanks so much. Your instructions were correct dreadood. It is all fixed up. 

Jbike

---

### Post by Jbike on 2009-11-30
Thanks so much. It does work if you begin with the flash from the repos. I had tried so many things- I forgot where I ended up. 

Jbike

---

### Post by seeker5528 on 2009-11-30
For my 64bit installation I purged all flash stuff and nsplugin wrapper, then went to:

[ftp://ftp.debian-multimedia.org/pool/main/f/flash-player-amd64/](ftp://ftp.debian-multimedia.org/pool/main/f/flash-player-amd64/)

: and downloaded:

flashplayer-mozilla_10.0.d32.18-0.0_amd64.deb

: then opened the filemanager and clicked on the file to trigger gdebi to do the installation.

Before hand when I went to Hulu, no buttons worked and I had to hit the space bar to start the video playing.

Afterwards all the stuff I expected the mouse to work for seem to be working.

From what I have read in this thread and elsewhere there doesn't really seem to be a universal solution that works for everybody, so YMMV.

Later, Seeker

---

### Post by ph1 on 2009-11-30
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Fixed it for me too, thanks man!

---

### Post by tudor117 on 2009-11-30
Another temp fix is to hold the middle mouse button (if you have one) and then left-click with the middle clicked. It should work the first or second click.
However....

> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Worked for me too.
Thanks!
You should write a how to or something similar as it seems there are multiple posts in the forums with similar problems.

---

### Post by sportsdude81 on 2009-12-07
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

This worked for me as well.  An admin should make a howto on the forums with these instructions.  For anybody who is wondering.  After I made this change I just restarted (closed and reopened) firefox and the buttons were then responsive.

---

### Post by AlmoG on 2010-07-29
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

That seemed to fix my problem :D thanks
I've been messing with this bug for 2 days now

---

### Post by RabbitWho on 2010-07-29
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

that's for 32 bit, right? 64bit alternative?

---

### Post by Jbike on 2010-08-18
I believe that if you installed the 64 bit version of Ubuntu, then you should install the 32bit version of flash from the repos only (don't go directly to Adobe site), then apply the changes that you outlined.

Jbike

---

