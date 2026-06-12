---
title: "ubuntu 10.10, firefox 8 64bit - flash not working"
date: 2011-11-26
forum: General Help
---

### Post by bobdobbs on 2011-11-26
Hi all.
I have ubuntu 10.10, 64bit.

I downloaded firefox 8.01, and installed it in my /home/user/opt dir.

Flash was not working, so I downloaded the adobe flash 64bit version from adobe. I unpacked it, changed the perms to 777, and placed the plugin in firefox's base dir.

Still no flash.

I placed a copy of the new .so in /usr/lib/firefox/plugins.
Still no flash.

How can I get flash working in 8.02?

---

### Post by ajgreeny on 2011-11-26
Try using the firefox add-on Flash-aid.   Do not let it install the beta version of flash, which is its default action, but choose the stable version of flash from the ubuntu repos, and see if that helps.

There have been a number of flash problems over the last few weeks, much more than usual, which some people are putting down to the new beta flash version that flash-aid installs.  I don't know about the truth of that, but I do know that the beta version will not work at all on my FF 8 on Lucid 10.04 32 bit, whereas the stable version from ubuntu's own repos is great.  Your 64 bit system may mean there is no stable version available in the repos, but I will have to leave that to you to find out.

---

### Post by oldtimer7777 on 2011-11-26
I've also noticed that the:

sudo add-apt-repository ppa:sevenmachines/flash

appears to have deleted their Flash 64 bit package, sadly.. That would always fix it for me.

> **ajgreeny said:**
> Try using the firefox add-on Flash-aid.   Do not let it install the beta version of flash, which is its default action, but choose the stable version of flash from the ubuntu repos, and see if that helps.

There have been a number of flash problems over the last few weeks, much more than usual, which some people are putting down to the new beta flash version that flash-aid installs.  I don't know about the truth of that, but I do know that the beta version will not work at all on my FF 8 on Lucid 10.04 32 bit, whereas the stable version from ubuntu's own repos is great.  Your 64 bit system may mean there is no stable version available in the repos, but I will have to leave that to you to find out.

---

### Post by Gremlinzzz on 2011-11-26
> **bobdobbs said:**
> Hi all.
I have ubuntu 10.10, 64bit.

I downloaded firefox 8.01, and installed it in my /home/user/opt dir.

Flash was not working, so I downloaded the adobe flash 64bit version from adobe. I unpacked it, changed the perms to 777, and placed the plugin in firefox's base dir.

Still no flash.

I placed a copy of the new .so in /usr/lib/firefox/plugins.
Still no flash.

How can I get flash working in 8.02?
 Try going to home folder,click view and choose show hidden files,
find .mozilla folder open, in folder create new folder name it plugins ,
put new  libflashplayer.so file in it. :popcorn:

---

### Post by Foxcow on 2011-11-26
I don't recommend using any of the automated flash installers.  For the maximum control and flash for all users on your system, try this:


-Open Software Center, search for flash, and remove anything to do with flash.
-Run these commands:
```
sudo apt-get autoclean && sudo apt-get autoremove
```

-Get 64-bit Flash from Adobe and extract it in you downloads folder
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
the file should be libflashplayer.so 

-Open a terminal and type
```
cd /usr/lib/mozilla/plugins
```
this will take you to the directory that the flash plugin needs to be put so that all users can use it.

-Now you want to copy the file you extracted in your Downloads folder to this directory by typing:
```
sudo cp ~/Downloads/libflashplayer.so .
```
you will be prompted for your password.

-After that that is done, restart Firefox and viola!

---

### Post by bobdobbs on 2011-11-27
The automated installer didn't work.

I used it both in wizard mode and in quick mode. Restarted my browser in between attempts. No luck.

I tried to do it manually too, following the instructions in the last post, with one exception: I made the plugin globally executable.
But that didn't work either.

What's the next thing to try?

---

### Post by bobdobbs on 2011-11-27
> **Gremlinzzz said:**
> Try going to home folder,click view and choose show hidden files,
find .mozilla folder open, in folder create new folder name it plugins ,
put new  libflashplayer.so file in it. :popcorn:

Just tried that. Didn't work.

---

### Post by hic3456 on 2011-11-27
Similar issue - not a newbie, but constantly frustrated by how idiotically incompatible Firefox and Flash seem to be in Ubuntu - one would've thought that between Mozilla and Adobe they'd have figured out a way to install the latter without having to pull one's hair.

My Ubuntu 10.10 has the 'stock' Firefox install 3.6.24 (Firefox for Canonical 1.0) - ancient stuff, AFAICT

So, I've downloaded and installed Firefox 8 in /opt/firefox
works just fine, only for the fact that it does not pick any single plugin.

My 'stock' FF (/usr/bin/firefox) picks all the plugins in /usr/lib/firefox/plugins - the one in /opt/firefox none at all.

I've tried adding libflashplayer.so (freshly downloaded from Adobe) in ~/.mozilla/plugins, in /opt/firefox/plugins and replacing the one in /usr/lib/firefox/plugins - no joy.

To be very clear: Flahs works just fine with the 'official' FF (3.6.24) so I am sure it is NOT a version issue - FF 8 (/opt/firefox) just does not show any plugin at all in about:plugins (even those in /opt/firefox/plugins)

So, a very simple question: does anyone know how to make the 'download' install of FF pick any plugins? where would it go looking for them?
Alternatively, is there a way using apt-get to get the latest FF? (ideally, FF 8 for Linux)

thanks!

---

### Post by Foxcow on 2011-11-27
> **bobdobbs said:**
> The automated installer didn't work.

I used it both in wizard mode and in quick mode. Restarted my browser in between attempts. No luck.

I tried to do it manually too, following the instructions in the last post, with one exception: I made the plugin globally executable.
But that didn't work either.

What's the next thing to try?

If you remove all instances of flash in the home directory and the automated flash aids and installers, my instructions will work for you.  Also, if you want to install the lates Firefox, install it from a ppa.  Its a lot easier and you will remain up-to-date automatically.  I had a 10.10 install that updated to 8.0x basically right after it launched.

---

### Post by hic3456 on 2011-11-27
> **Foxcow said:**
> Also, if you want to install the lates Firefox, install it from a ppa.  Its a lot easier and you will remain up-to-date automatically.  I had a 10.10 install that updated to 8.0x basically right after it launched.

Do you happen to know what is the PPA for Maverick?
I found a thread about that, but it was far from clear which one to use.
Also, I'm a bit reluctant to nuke my 3.6.24 install, as it works fine - my preference would be to just figure out how to make FF 8 find the plugins.

---

### Post by Foxcow on 2011-11-27
> **hic3456 said:**
> Do you happen to know what is the PPA for Maverick?
I found a thread about that, but it was far from clear which one to use.
Also, I'm a bit reluctant to nuke my 3.6.24 install, as it works fine - my preference would be to just figure out how to make FF 8 find the plugins.



I can understand your reluctance :D.

Here is the ppa: ppa:mozillateam/firefox-stable
I've recently used thsi one on a 10.10 64-bit install to update Firefox

```
 sudo add-apt-repository ppa:mozillateam/firefox-stable
       sudo apt-get update
       sudo apt-get upgrade 
```

As I said, remove flash (especially the one in the software center) and my instructions will work.  This is the method I've used to install flash since 10.04 and it has never failed me.

---

### Post by jawilljr on 2011-11-27
What I did is use one of the [two scripts in this post.](http://ubuntuforums.org/showpost.php?p=11491890&postcount=15) In my case I used the 64 bit version. It will automatically remove all previous versions of flash and install the stable version of either the 32 bit or 64 bit version of flash...restart firefox and it will work.

Jerry

---

### Post by bobdobbs on 2011-11-27
Hey foxcow.

I gave this another shot: I removed the automatic installers and restarted. Then I used the software center to remove anything related to flash in the browser. 

I then ran the apt commands, re-downloaded the plugin and moved it to the mozilla lib directory.

I'm afraid I'm still getting no results.

---

### Post by Foxcow on 2011-11-27
> **bobdobbs said:**
> Hey foxcow.

I gave this another shot: I removed the automatic installers and restarted. Then I used the software center to remove anything related to flash in the browser. 

I then ran the apt commands, re-downloaded the plugin and moved it to the mozilla lib directory.

I'm afraid I'm still getting no results.

Very, very bizarre...

Just to make sure, did you remove the plugin from the .mozilla folder in your home directory?

Also, what version of flash, if any, shows up when you type "about:plugins" into your browser url bar?

I think your fix will be very simple but we need to do a little detective work.

---

### Post by bobdobbs on 2011-11-27
> **Foxcow said:**
> Very, very bizarre...

Just to make sure, did you remove the plugin from the .mozilla folder in your home directory?


Yeah. There was nothing else in that directory, so I just rm -rf'd the whole thing.


> **Foxcow said:**
> 
Also, what version of flash, if any, shows up when you type "about:plugins" into your browser url bar?


Nothing for flash shows up.

---

### Post by Foxcow on 2011-11-27
> **bobdobbs said:**
> Yeah. There was nothing else in that directory, so I just rm -rf'd the whole thing.




Nothing for flash shows up.


Ok, and you are absolutely sure that you move libflashplayer.so to /usr/lib/mozilla/plugins directory?  If you navigate to that directory, you can verify that the most up-to-date version that you downloaded was moved there by checking the date on the plugin if you type in
```
 ls -l 
```

I just tried with a Mint install and I did it with my primary Arch install a few days ago.

What do you see listed for flash (if anything) when you type "about:plugins" in your Firefox url bar?

** edit: **I'm not sure how advanced a user you are so please forgive me if I insult your intelligence.

---

### Post by Foxcow on 2011-11-27
I just thought of another thing you can try.  To make sure you know where all instances of libflashplayer.so are located, try this:

```
 cd / && sudo find -name libflashplayer.so 
```


It will search every directory from root on down.

---

### Post by bobdobbs on 2011-11-27
When I enter 'about:plugins' in the url bar, I get 'no plugins found'.

I cd'd to '/' and used the find command. The .so showed up a few times, but mostly in my 'work area' directory - ie, not in my path. An identically named .so shows up in an opt directory, included with adobe AIR. This is in my path.

But then, I'm talking about my executable path. I don't know how linux or firefox searches for libraries.

'ls -al' in /usr/lib/mozilla/plugins, against the flashplayer library, gives yesterdays date. It must be the one that I downloaded and installed yesterday.

---

### Post by Foxcow on 2011-11-27
> **bobdobbs said:**
> When I enter 'about:plugins' in the url bar, I get 'no plugins found'.

I cd'd to '/' and used the find command. The .so showed up a few times, but mostly in my 'work area' directory - ie, not in my path. An identically named .so shows up in an opt directory, included with adobe AIR. This is in my path.

But then, I'm talking about my executable path. I don't know how linux or firefox searches for libraries.

'ls -al' in /usr/lib/mozilla/plugins, against the flashplayer library, gives yesterdays date. It must be the one that I downloaded and installed yesterday.

Ok, I just got home to my Ubuntu system and ran " cd / && sudo find -name libflashplayer.so" and have it only in one location (.usr/lib/mozilla/plugins).  I'm guessing that all of the automated scripts and such installed the plugin to all kinds of crazy places.  As far as I know, for the plugin to be globally available, you only need to put it in /usr/lib/mozilla/plugins.  I would remove all other instances.


A few more troubleshooting questions:

Was the update to 8.0x successful via PPA?

If you run "about:plugins" in your 3.6xx browser, what do you get?

---

### Post by bobdobbs on 2011-11-27
> If you run "aboutlugins" in your 3.6xx browser, what do you get? 
I'm not running 3.6. I'm running 6.02. 
My result when I check flash version:

    ```
File: libflashplayer.so
    Version: 
    Shockwave Flash 11.1 r102
```


> Was the update to 8.0x successful via PPA?
No.
After I installed the ppa, I ran 'apt-get update' and then 'apt-get dist-upgrade'. During upgrade, it looked like a new firefox was downloading. But when I started firefox from the gnome toolbar menu, 6.02 started up.

So, I'm still running 8 from an opt dir.

I've cleaned out all instances of the flash plugin from all directories except for the copy in the AIR opt directory and /usr/lib/mozilla/plugins.

Unfortunately, I'm still getting the same result

---

### Post by Foxcow on 2011-11-27
> **bobdobbs said:**
> I'm not running 3.6. I'm running 6.02. 
My result when I check flash version:

    ```
File: libflashplayer.so
    Version: 
    Shockwave Flash 11.1 r102
```


Excellent!  This means you have the most current version installed.  Unfortunately, it doesn't like the way you are running Firefox 8...


> 
No.
After I installed the ppa, I ran 'apt-get update' and then 'apt-get dist-upgrade'. During upgrade, it looked like a new firefox was downloading. But when I started firefox from the gnome toolbar menu, 6.02 started up.

So, I'm still running 8 from an opt dir.

I've cleaned out all instances of the flash plugin from all directories except for the copy in the AIR opt directory and /usr/lib/mozilla/plugins.

Unfortunately, I'm still getting the same result

Honestly, I have no idea why you aren't getting 8 from that ppa.  I simply added the ppa on my 10.10 system, updated, and ran the upgrade.  It was right after I'd formated too so maybe it did it in steps (6 to 8) but I'm not sure as I didn't pay attention as it was working.

Do you have any other Mozilla or Firefox related ppas in your software sources list?

---

### Post by hic3456 on 2011-11-27
> **Foxcow said:**
> As far as I know, for the plugin to be globally available, you only need to put it in /usr/lib/mozilla/plugins.

That may be true for a 'standard' install, but definitely not for the one I downloaded/installed from Mozilla:

```
$ ll /usr/lib/mozilla/plugins/
total 19M
-rw-r--r-- 1 root root  18M 2011-11-27 16:18 libflashplayer.so
lrwxrwxrwx 1 root root   39 2011-11-17 19:17 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root   43 2011-11-19 18:22 libnpgoogletalk64.so -> /opt/google/talkplugin/libnpgoogletalk64.so
lrwxrwxrwx 1 root root   47 2011-11-19 18:22 libnpgtpo3dautoplugin.so -> /opt/google/talkplugin/libnpgtpo3dautoplugin.so
-rw-r--r-- 1 root root 6.0K 2011-01-25 01:54 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root 100K 2010-09-28 02:30 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 108K 2010-09-28 02:30 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  72K 2010-09-28 02:30 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  80K 2010-09-28 02:30 libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   39 2011-03-10 22:30 npPicasa3.so -> /opt/google/picasa/3.0/lib/npPicasa3.so

```

When I start the 'stock' FF (/usr/bin/firefox) it shows all the plugins in about:plugins -- when I start the one in /opt/firefox, it shows none.

Thanks for help, I guess, I'll just carry on using the ancient one for Flash... Chrome is my main browser anyway :)

---

### Post by hic3456 on 2011-11-27
RESOLVED -- This was something to do with 32 v 64bit compatibility:

```
 LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]

```

I was confused by thinking that FF automatic download had done the 'right thing' and selected the right arch (64 bit) for my system (not that it gave me any options to choose from anyway) but there clearly are some issues with 32/64 bit.

Bottom line: I downloaded the 32bit Flash plugin from Adobe (chose the .tar.gz option from here: [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)) copied just the libflashplayer.so in my ~/.mozilla/plugins folder, and all is working now.

---

### Post by bobdobbs on 2011-11-27
> **Foxcow said:**
> 
Do you have any other Mozilla or Firefox related ppas in your software sources list?

'cat /etc/apt/sources-list | grep -i fox' shows nothing.

I just ran through the whole process again... installed the ppa, updated and dist-upgraded.
I was again told that firefox could be updated. So I accepted, and installed ff again. 
When I restarted ff, it was 6.02 again.

Out of curiosity, I ran 'dist-upgrade' again, and was again told that firefox could be updated. 

So, it looks like apt will download  firefox every time dist-upgrade needs to be run. without actually ever installing it. This is getting frustrating.

---

### Post by oldtimer7777 on 2011-11-27
I have had trouble with Firefox like this lately too.

What I did was install the PPAs for Firefox.  

Then I ran PPA purge.  There are a couple of different PPAs you can use. 

It really depends on if you installed any PPAs you can remember...

After you get the purges done, you can pick a PPA and use that to upgrade Firefox to the latest version. 

btw-don't use the purge feature in Ubuntu Tweak to do purges because it never works.. you will have to do it from the command line 
using [http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html](http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html)

> **bobdobbs said:**
> 'cat /etc/apt/sources-list | grep -i fox' shows nothing.

I just ran through the whole process again... installed the ppa, updated and dist-upgraded.
I was again told that firefox could be updated. So I accepted, and installed ff again. 
When I restarted ff, it was 6.02 again.

Out of curiosity, I ran 'dist-upgrade' again, and was again told that firefox could be updated. 

So, it looks like apt will download  firefox every time dist-upgrade needs to be run. without actually ever installing it. This is getting frustrating.

---

### Post by bobdobbs on 2011-11-28
Ok... So, I installed ppa-purge, and then purged the ppa I was using.
I then ran 'dist update', 'dist clean' and then re-installed the ppa.

Then I did 'apt-get firefox', and got the response that the latest version was already installed.

Bugger.

I searched google to find a ppa that would provide the latest version, and I came across this: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

The instructions pretty much told me install the ppa that I already have installed.

So, it looks like I'm stuck with running the latest version from an opt directory... 
Which is fine, but still... how do I get flash to work?

---

### Post by ajgreeny on 2011-11-28
I must have missed something from the thread further back, but I see you are running a version of FF from the /opt folder.  I presume you must have installed the tar.gz which you downloaded direct from mozilla.

Correct?  If so, I wonder if some of the application files that you are using from that are causing the problem with the FF v8 that comes from the ppa repos.  Perhaps you should uninstall the version in /opt, however you do that.

---

### Post by bobdobbs on 2011-11-28
> **ajgreeny said:**
> I must have missed something from the thread further back, but I see you are running a version of FF from the /opt folder.  I presume you must have installed the tar.gz which you downloaded direct from mozilla.

Correct?  If so, I wonder if some of the application files that you are using from that are causing the problem with the FF v8 that comes from the ppa repos.  Perhaps you should uninstall the version in /opt, however you do that.

The ppa repo isn't giving me firefox version 8.
Or, if it is, then my OS isn't running it - running 6.02 instead. 
Both of these possibilities are weird, but I find the first less unlikely.

I installed ff8 into an opt directory so that I could test it before I committed to it. The dir in question is not in my executable path - I start it using a command from the terminal after I've navigated to the dir.
Because it's not in my path, I don't think that the libraries or other files in that dir would be interefering with anything.

---

### Post by Foxcow on 2011-11-28
> **ajgreeny said:**
> I must have missed something from the thread further back, but I see you are running a version of FF from the /opt folder.  I presume you must have installed the tar.gz which you downloaded direct from mozilla.

Correct?  If so, I wonder if some of the application files that you are using from that are causing the problem with the FF v8 that comes from the ppa repos.  Perhaps you should uninstall the version in /opt, however you do that.


I was just going to suggest that.  Try running it from a folder in your home directory.

**edit:**  I just downloaded Firefox 9 beta and it launched but could not load plugins.

I got this error message.  I will troubleshoot further when I get home from class
```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
```

---

### Post by bobdobbs on 2011-12-30
> **jawilljr said:**
> What I did is use one of the [two scripts in this post.](http://ubuntuforums.org/showpost.php?p=11491890&postcount=15) In my case I used the 64 bit version. It will automatically remove all previous versions of flash and install the stable version of either the 32 bit or 64 bit version of flash...restart firefox and it will work.

Jerry

Hi Jerry.

After updating to firefox 9.01, I decided to have another shot at getting flash to work on firefox on linux.

I downloaded and ran your script.
It ran without errors.

But when I restarted firefox, flash was still not working.

---

### Post by lovinglinux on 2011-12-31
> **hic3456 said:**
> Do you happen to know what is the PPA for Maverick?
I found a thread about that, but it was far from clear which one to use.
Also, I'm a bit reluctant to nuke my 3.6.24 install, as it works fine - my preference would be to just figure out how to make FF 8 find the plugins.

Use *firefox-stable* ppa. See [Firefox 9 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by blueshead on 2011-12-31
This worked for me for Firefox 9.01

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by bobdobbs on 2012-01-11
> **lovinglinux said:**
> Use *firefox-stable* ppa. See [Firefox 9 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

I'd like to use this ppa, but apt on my system broke a while ago. I'm using the latest version of firefox, running from an opt directory.

I don't know how apt compares to other package managers, but I find apt generally pretty fragile and very difficult to repair.

However, I just tried to install flash, using synaptic. To my surprise, the installation ran without a flaw and installed flash. However, my version of firefox still doesn't run flash. 

So, at the moment, if I want to watch flash video, I switch browsers. I run firefox for most everything, and chromium for watching flash video.

---

### Post by bobdobbs on 2012-01-11
> **blueshead said:**
> This worked for me for Firefox 9.01

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

I've tried that a few times now, but it still won't get flash running on firefox on my system.

---

### Post by bobdobbs on 2012-01-12
> **bobdobbs said:**
> I run firefox for most everything, and chromium for watching flash video.

Scratch that.

It seems that flash no longer works on my system for chromium either.

---

### Post by bobdobbs on 2012-02-03
I've installed both firefox 10 and firefox 11a.

Neither of them allow me to use flash.

With both of them I've tried various things to get flash to work, but I have been unsuccessful.

What is it about the these later version that makes this so difficult?


Surely other people have managed to get flash working in later versions. How can I fix this? Is it an issue with firefox? Ubuntu? What's going on here?

---

### Post by bobdobbs on 2012-02-28
I've updated to ff 10.02 via apt-get.

I still have no flash.

Is it just me? Or is there just no way to get flash to work on firefox on 64bit ubuntu?

---

### Post by guine on 2012-02-28
Im starting to think it may be an ubuntu issue, I just had flash die for a second time and this time flashaid hasn't been able to fix it.  I have noticed that both times flash died was after downloading updates, although I don't think there was a flash update this time.

---

### Post by bobdobbs on 2012-02-28
> **guine said:**
> Im starting to think it may be an ubuntu issue, I just had flash die for a second time and this time flashaid hasn't been able to fix it.  I have noticed that both times flash died was after downloading updates, although I don't think there was a flash update this time.

It probably is an ubuntu issue. I know people using other 64bit distros who have had no real problems getting flash to work on firefox.

However, I still have flash working in chrome and other browsers. Does flash work for you in other browsers?

---

### Post by Foxcow on 2012-02-28
> **guine said:**
> Im starting to think it may be an ubuntu issue, I just had flash die for a second time and this time flashaid hasn't been able to fix it.  I have noticed that both times flash died was after downloading updates, although I don't think there was a flash update this time.


I think that depends on what version of flash you're using.  If you're on 64-bit Ubuntu and running the stuff that comes in the software center, I bet thats your issue.  Flash in the softeare center is the 32-bit version with a wrapper for 64-bit systemes.  Before Adobe released a pure 64-bit way, using a wrapper is as good as it got.  However, now that there is a fairly good 64-bit version, there is no reason to be using what is in the software center.

As far as the previous poster, I don't know why they are having issues.  I ran 10.10 64-bit flash under Firefox and Chrome with no issue whatsoever (and several people that I've set it up for).  I used the procedure that I outlined earlier in this thread as well.  Maybe their system is messed up from all of the "installs" of Firefox or not following the steps.  I don't know.

---

### Post by guine on 2012-02-28
> **bobdobbs said:**
> It probably is an ubuntu issue. I know people using other 64bit distros who have had no real problems getting flash to work on firefox.

However, I still have flash working in chrome and other browsers. Does flash work for you in other browsers?

Flash isn't working for me in firefox or chrome right now.

---

### Post by guine on 2012-02-28
Well it now appears that flash is only broken on some sites while it run fine on others.

---

### Post by lovinglinux on 2012-02-29
> **guine said:**
> Well it now appears that flash is only broken on some sites while it run fine on others.

It is working fone here. Please post a link were it doesn't work, so we can take a look.

---

### Post by guine on 2012-02-29
> **lovinglinux said:**
> It is working fone here. Please post a link were it doesn't work, so we can take a look.

Well it seems to be working again despite me doing nothing.  These were the two sites I was having trouble with - [http://www.thedailyshow.com/](http://www.thedailyshow.com/) and [http://www.colbertnation.com/](http://www.colbertnation.com/)
When it first starts to load it still quickly pops up a message about needing to install flash, but then the video loads just fine.  Maybe its just something with those sites since they're both comedy central sites.

---

### Post by lovinglinux on 2012-02-29
> **guine said:**
> Well it seems to be working again despite me doing nothing.  These were the two sites I was having trouble with - [http://www.thedailyshow.com/](http://www.thedailyshow.com/) and [http://www.colbertnation.com/](http://www.colbertnation.com/)
When it first starts to load it still quickly pops up a message about needing to install flash, but then the video loads just fine.  Maybe its just something with those sites since they're both comedy central sites.

Most likely. Let me know if the problem comes back.

---

### Post by bobdobbs on 2012-03-29
I'm still stuck.

No flash on either firefox, chrome or chromium.

I'm over this crap. Ubuntu can't even get flash right. My next distro will not be ubuntu.

---

### Post by Foxcow on 2012-03-29
Honestly, I have no idea why you are having issues.  I've installed flash on many, many linux computers and most of the methods outlined in this thread work without fail.

That being said, if you switch, check out Arch Linux.  It is my distro of choice for many, many reasons.

---

### Post by bobdobbs on 2012-03-29
Yeah - I can't figure it out either. It's frustrating as hell. I've gone for months without having flash in firefox.

Last night I purged all flash files I could find in my system, and re-installed using synaptic. Still no flash in firefox, but it seems to be working in chrome now. It's very crashy though. The plugin seems to crash if I breath.

Checking out Arch now.

---

### Post by lovinglinux on 2012-03-31
> **bobdobbs said:**
> Yeah - I can't figure it out either. It's frustrating as hell. I've gone for months without having flash in firefox.

Last night I purged all flash files I could find in my system, and re-installed using synaptic. Still no flash in firefox, but it seems to be working in chrome now. It's very crashy though. The plugin seems to crash if I breath.

Checking out Arch now.

[http://ubuntuforums.org/showpost.php?p=11766379&postcount=274](http://ubuntuforums.org/showpost.php?p=11766379&postcount=274)

---

### Post by bobdobbs on 2012-04-01
> **lovinglinux said:**
> [http://ubuntuforums.org/showpost.php?p=11766379&postcount=274](http://ubuntuforums.org/showpost.php?p=11766379&postcount=274)

Ah, ok.

So it's not an ubuntu problem: it's a bug in flash that will not be fixed by the vendor. And there's no way to fix it, except by switching away from linux.

That sucks.

---

### Post by lovinglinux on 2012-04-01
> **bobdobbs said:**
> Ah, ok.

So it's not an ubuntu problem: it's a bug in flash that will not be fixed by the vendor. And there's no way to fix it, except by switching away from linux.

That sucks.

Google will support Flash through Chrome Pepper API, so you don't need to switch away from Linux, just browser. Personally, I really don't like to think about that, but if there is no other way...

---

### Post by bobdobbs on 2012-06-10
In the end the problem had no solution.

I upgraded to 12.04.

12.04 does not have this issue. But it most certainly has other issues.

---

