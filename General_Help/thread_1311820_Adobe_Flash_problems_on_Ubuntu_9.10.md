---
title: "Adobe Flash problems on Ubuntu 9.10"
date: 2009-11-02
forum: General Help
---

### Post by ghindo on 2009-11-02
I've been using Ubuntu Karmic since about June.

Recently, I've noticed I am unable to interact with Flash objects in Firefox.  For example, a YouTube video loads fine, but I am unable to adjust the volume within the video itself, skip ahead, pause, etc..

I've tried reinstalling several times through the Software Center, but every time I reinstall Flash, I encounter the same problems.  How do I purge every trace of Flash from my computer so I can start with a clean slate?

---

### Post by StaticIp on 2009-11-02
Same trouble here, any solutions yet?

---

### Post by ea1387 on 2009-11-02
Same Problem here

---

### Post by tudor117 on 2009-11-02
I had this too but it's an on off thing.
It works sometimes but other times it does not.
However, I can use the keyboard. So put mouse over sound and use arrow keys. I thought it was my mouse running out of batteries but the button was clicking but not doing anything.
Just use "space" to play.

---

### Post by jnew93 on 2009-11-02
I had the same problem. I decided to manually reinstall, and downloaded the alpha 64bit flash from Adobe and extracted it to ~/.mozilla/plugins, now flash works fine, albeit a bit buggy.

---

### Post by sambita on 2009-11-02
I did a clean install of Karmic and have the same problems, would love to know the solution. :)

---

### Post by ghindo on 2009-11-03
> **jnew93 said:**
> I had the same problem. I decided to manually reinstall, and downloaded the alpha 64bit flash from Adobe and extracted it to ~/.mozilla/plugins, now flash works fine, albeit a bit buggy.I had tried to manually install the 64-bit version as well; however, Firefox kept segphaulting every time I tried to launch it after I'd installed 64-bit Flash.

---

### Post by karesz on 2009-11-04
Same problem here... Seems like something eats the mouseclick event before it reaches the flash. But it's not only flash video related, and (as I've read somewhere else) it's not only a 64bit related problem. So don't bother reinstalling the flashplugin...

---

### Post by Strongman332 on 2009-11-04
i also have this problem is has become very annoying

---

### Post by Nilafhiosagam on 2009-11-04
and me...

---

### Post by Bunnybugs on 2009-11-04
You can download it from the repositories of Ubuntu, and you can download the direct Firefox plug in trough the Mozilla Add-on repositories...

This worked for me, so why not for you?

---

### Post by darksoul7 on 2009-11-04
I downloaded from the Ubuntu repo and I have this problem. It's quite frustrating.

---

### Post by bedhead75 on 2009-11-04
Flash from the repositories is always 32-bit, even if you're running a 64-bit system.  To install 64-bit flash you have to download it directly from the Adobe site.  I followed these instructions and it worked for me, and it also worked for a 64-bit Karmic installation running in Virtualbox.

[http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

But BEFORE you do the above, you have to remove all traces of 32-bit flash and the nspluginwrapper that comes with it, otherwise you might get conflicts and crashes.  I removed them using Synaptic, but I also ran the following from the terminal to make sure:

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

I then followed the instructions on that site, I haven't had a problem with flash or a Firefox(ver 3.0.15)crash since.

---

### Post by ghindo on 2009-11-05
> **bedhead75 said:**
> Flash from the repositories is always 32-bit, even if you're running a 64-bit system.  To install 64-bit flash you have to download it directly from the Adobe site.  I followed these instructions and it worked for me, and it also worked for a 64-bit Karmic installation running in Virtualbox.

[http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

But BEFORE you do the above, you have to remove all traces of 32-bit flash and the nspluginwrapper that comes with it, otherwise you might get conflicts and crashes.  I removed them using Synaptic, but I also ran the following from the terminal to make sure:

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

I then followed the instructions on that site, I haven't had a problem with flash or a Firefox(ver 3.0.15)crash since.Thanks for the reply, bedhead!

Unfortunately, I followed your instructions for installing 64-bit Flash and Firefox segphaults!  I had to revert back to 32-bit Flash from the repositories.

And just to clarify, these issues are occurring with 64-bit Ubuntu 9.10 in Firefox 3.5.4.

If anybody knows anything more about this issues, please let us know!

---

### Post by WildCard77 on 2009-11-07
I am seeing the same thing in Ubuntu 9.10 64 bit clean install on Firefox 3.5.4.

---

### Post by Vl@dimir on 2009-11-08
[B]Adobe Flash problems on Ubuntu 9.10

Me to
[/B]

---

### Post by Ozzman on 2009-11-11
> **bedhead75 said:**
> Flash from the repositories is always 32-bit, even if you're running a 64-bit system.  To install 64-bit flash you have to download it directly from the Adobe site.  I followed these instructions and it worked for me, and it also worked for a 64-bit Karmic installation running in Virtualbox.

[http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

But BEFORE you do the above, you have to remove all traces of 32-bit flash and the nspluginwrapper that comes with it, otherwise you might get conflicts and crashes.  I removed them using Synaptic, but I also ran the following from the terminal to make sure:

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

I then followed the instructions on that site, I haven't had a problem with flash or a Firefox(ver 3.0.15)crash since.

heh well now it just crashes my firefox instead of just messing it up..

EDIT SOLUTION: Added the 64 bit .so plugin from adobe to the other folders then did a reboot and that fixed it for firefox (swiftfox still doesnt use it though)

sudo cp /usr/lib/mozilla/plugins/libflashplayer.so ~/.mozilla/plugins/
sudo cp /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox/plugins/

obviously I had already tried adding it only to the mozilla plugins folder and that didnt work..

P.S. I'm watching hulu at 480p while posting this.. so it seems all is well :-) thanks for the directory listings.

---

### Post by andreo on 2009-11-12
> **bedhead75 said:**
> Flash from the repositories is always 32-bit, even if you're running a 64-bit system.  To install 64-bit flash you have to download it directly from the Adobe site.  I followed these instructions and it worked for me, and it also worked for a 64-bit Karmic installation running in Virtualbox.

[http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

But BEFORE you do the above, you have to remove all traces of 32-bit flash and the nspluginwrapper that comes with it, otherwise you might get conflicts and crashes.  I removed them using Synaptic, but I also ran the following from the terminal to make sure:

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

I then followed the instructions on that site, I haven't had a problem with flash or a Firefox(ver 3.0.15)crash since.


Thanks! Note that you should edit version of adobe flash plugin which you want to install . Instead of  *libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz* I used* libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz* .

Works perfectly!!!

---

### Post by Terad on 2009-11-14
> **andreo said:**
> Thanks! Note that you should edit version of adobe flash plugin which you want to install . Instead of  *libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz* I used* libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz* .

Works perfectly!!!
I tried it with *libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz* too and it works just fine! Thanks!

---

### Post by tudor117 on 2009-11-15
I tried libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz but it was very slow and it used up ALL my CPU. I don't understand :(

Oh, and though I said some sites don't work with flash when you click, they only partially work. If you *left click + middle click* at the same time, multiple times, it ends up working. It's a pain in the behind but its better than having it lag like crazy...

---

### Post by QfwfQ on 2009-11-19
I'm also having the "flash problem". Using Ubuntu 9.10 (32bits) upgraded from 9.04.

When i watch something like youtube videos I can see the processor "fully loaded" (on panel applet), sometimes to the point firefox and everything else stop responding.

Sorry I can't help...

---

### Post by nunovi on 2009-11-21
Hi,

It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.

If we make this issue big enough, we can gain a higher priority for Adobe to solve this issue. Please go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692), register and vote for this issue. If we all take 5 minutes to do this, I'm sure we can reach a very high number of votes and let Adobe know Linux is an important community to take into consideration.

Nuno

---

### Post by t2491tom on 2009-11-30
I have been having the same problem, but i have the fix and it's very simple. 
Simply type this into your terminal:
> **wget [http://queleimporta.com/downloads/flash10_x64_en.sh](http://queleimporta.com/downloads/flash10_x64_en.sh) && sudo chmod +x flash10_x64_en.sh && sudo sh ./flash10_x64_en.sh****source**: [http://www.tishon.net/index.php/2009/11/14/problems-with-adobe-flash-player-in-ubuntu-9-10-64-bit/](http://www.tishon.net/index.php/2009/11/14/problems-with-adobe-flash-player-in-ubuntu-9-10-64-bit/)

---

### Post by tuxeee on 2009-11-30
is that for ubuntu 64bit?

theres also a problem with java :/
same flashing thing as streaming a youtube vid

---

### Post by t2491tom on 2009-11-30
Yes, the code is fr 64 bit Ubuntu 9.10's flash player. I don''t know much about Java and don't have that problem. If you upgraded to 9.10 I strongly suggest a fresh install. I had many problems after I upgraded too.

---

### Post by tudor117 on 2009-11-30
For those still wondering, it's fixed.
> **Xebec said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line: ```
export GDK_NATIVE_WINDOWS=1
``` **before** this line: ```
. /usr/lib/nspluginwrapper/noarch/npviewer
```

---

### Post by Dr Sketch on 2009-11-30
> **t2491tom said:**
> I have been having the same problem, but i have the fix and it's very simple. 
Simply type this into your terminal:
**source**: [http://www.tishon.net/index.php/2009/11/14/problems-with-adobe-flash-player-in-ubuntu-9-10-64-bit/](http://www.tishon.net/index.php/2009/11/14/problems-with-adobe-flash-player-in-ubuntu-9-10-64-bit/)

Thank you thank you thank you thank you!  I've been fighting with getting video to work since I upgraded two weeks ago, and this is the first thing I've found that worked.  You, sir, are my hero.

---

### Post by tuxeee on 2009-12-01
> **t2491tom said:**
> Yes, the code is fr 64 bit Ubuntu 9.10's flash player. I don''t know much about Java and don't have that problem. If you upgraded to 9.10 I strongly suggest a fresh install. I had many problems after I upgraded too.

i have done a fresh install...so it wont work for 32bit?

---

### Post by Alex_J on 2009-12-12
#26 works like a charm. 
Just add this extra line (*export GDK_NATIVE_WINDOWS=1*) to your */usr/lib/nspluginwrapper/i386/linux/npviewer*
Thanks [tudor117]("http://ubuntuforums.org/member.php?u=890431")

---

### Post by LuisGMarine on 2009-12-12
Try this link out. This installs the latest Adobe Flash plugin specificly for 64-bit Linux.  It was released on December 8th, 2009.  I went ahead and even made a video tutorial, that I hope someone will find helpfull.  This has fixed my problem as far as not being able to interact with youtube, and other stuff like that.  Hope this helps you guys!

[http://ubuntuforums.org/showthread.php?t=1352617]("http://ubuntuforums.org/showthread.php?t=1352617")

---

### Post by JDorfler on 2009-12-12
Go to your terminal and use:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 61E46227
```

Then add these to your repositories:

```
deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu karmic main #Flash

deb-src http://ppa.launchpad.net/sevenmachines/flash/ubuntu karmic main #Flash
```

That fixed it for me.

---

### Post by ddg1015 on 2009-12-13
I'm also having the same problem and have tried numerous things and nothing seems to work. Some help anyone??

---

### Post by ddg1015 on 2009-12-13
this Flash Optimization clean mine up and fixed all the problems i was having.


[COLOR=#cc0000][SIZE=4]Removing Conflicting Plugins[/SIZE][/COLOR]

Ubuntu comes with swfdec plug-in, but it doesn't work on several sites. Installing the version from Adobe might solve this problem and improve performance. 

To remove other flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

 	Code:
 	sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

---

### Post by Xander {MP} on 2009-12-13
and me...

---

### Post by Uachtarain on 2009-12-13
Install Google Chrome ASAP.... Remove other browsers or leave them??. This problem has been with Firefox and has been for a couple of years now. Not worth the time to fix. Sit back and watch your blood pressure go way down....!!

Fergal

---

### Post by rabb_i on 2010-01-09
Chrome fixes some problems. For example, it doesn't crash when Flash crashes, so GMail still works fine.

BUT, Flash still doesn't work on some sites when using Flash 10 64bit on Ubuntu 9.10 64bit. On those sites I just get a sad face in a black box... less annoying, but equally functional (not at all)

For me that's the problem anyway

Has anyone found a solution to stop Flash from crashing yet?

---

### Post by rabb_i on 2010-01-10
I found the problem on my machine!

When I have Twhirl, TweetDeck, or any other Adobe Air application it causes the "Flash GMail Bug".

As soon as I close all Air apps (without even restarting browser) all problems seem to disappear.

My current solution is to replace Twhirl with Choqok as my twitter client. 

If anyone else comes up with a more direct solution it would be great to hear it

---

### Post by Torchmann on 2010-01-14
Are you entirely sure flash is working perfectly for you?
try wiping the drive and doing a virgin install. install all your apps and add-ons EXCEPT for flash10
reboot.
bring up the system monitor. log your cpu,memory and network traffic.
Install flash 10 and log the readings.
Now reboot and bring up system monitor again and log the readings.
Now uninstall flash 10 and reboot.
Bring up system monitor and log the readings. 
I suspect you will have the same increase in activity with flash uninstalled as when it was installed. I suspect that if you were to reinstall your OS fresh without flash the readings would be the same as with flash until you reinstall after wiping the drive...


I'm having problems with flash also. I've done some extensive iteration with a multitude of linux and flash installs by different degrees of cleanliness.

I started with a wiped drive and created 2 partitions. I did a fresh virgin windows xp install on the primary partition and got it up and running perfect with firefox and flash 10.

The problems I'm having related to flash are not related to my system hardware. flash works perfectly under windows XP even with firefox. There is a problem between flash and linux.
Flash causes my Linux system to run like when my windows xp gets a bunch of rootkits, viruses and trojans in it. It also causes My linux to act like it does when I don't have flash installed but browse to an attack site that is trying to run something Ill in memory that's trying to install itself in a windows system but is stuck in a Linux environment. You know...when nothing is successfully installed by the attack site but lags you out until you reboot???

On the second partition I installed jaunty.
It was working fine until I started installing Firefox add-ons and trying different Linux media editing applications.
I Googled around and first assumed Firefox was hanging up and did all the popular optimizations one at a time with no improvement in performance. 
I upgraded to Karmic with ill results, performance degraded.
I wiped the Linux partition and did a clean Install of karmic. It was working fine until I installed my favorite apps and add-ons including flash 10.
I couldn't get sound working for Urban Terror and after making the recommended change to libsdl1.2debia-pulse (or something like that) UT would run with sound but would crash. After googling, I assumed it was the sound card crashing and locking up gnome. I couldn't even come up with a theory why Firefox was lagging out so bad at the time.
I tried installing Ubuntu Studio, Debian Lenny, and Ubuntu Ultimate Edition with similar results.
Not having done a drive wipe since my last successful install I again wiped the drive and installed Ubuntu9.10 Ultimate Edition.
It worked perfect. Now this time I did not install any firefox add-ons. I attempted to install Urban Terror first. It ran perfect with no sound. I changed from the Alsa to the pulse sdl library and Urban Terror was now working perfectly. everything was. I installed my other apps one-by-one with no degradation in performance. I had everything installed as before except for flash and now everything was working perfect..
Then I got cocky and installed flash10. everything went haywire. Not only was Firefox lagging if you looked closely the entire system was lagging system app windows were fading in and out instead of popping and everything was hanging up as if over-tasked but the cpu, memory and net traffic was less than 25% of what it actually takes to cripple my system.
I was watching and documenting my cpu usage, memory usage and network traffic throughout this last install mention so far.
With everything but flash installed; a fresh boot and no applications started yet my cpu runs at 10-12% memory is at 10-12% and net traffic runs about 3-4k.
After calling up Firefox all 3 graphs increase minimally. I could barely perceive the difference in the system monitor.
There was some activity loading and installing flash 10 which afterward dropped to a point where my system was now 50% taxed.
I performed a fresh restart and then system monitor shows 20-25% cpu, 25-30% memory, and 6-8k latent network traffic.
everything monitored increased by I'm guessing 200%-300% over the previous readings. This was under a fresh boot with no apps called up yet. 
I installed flash block. 
Firefox would lag unacceptably with flash content disabled then worse with flash content activated. There was always about a 2-3 second lag between mouse commands or keystrokes when scrolling and when trying to enter text into a secure information text box but not into message boxes.

I uninstalled flash 10 and the problems persisted.
I reformatted the partition and re-installed Ubuntu and the problems persisted.
I wiped the partition then reinstalled the same Ubuntu and all the same apps and add-ons except for flash 10 and everything including UT is performing swimingly.

I'm not technically adept to look into the programming but from my ham-fisted neolithic perspective utilizing the scientific method and drawing from my vast experience crashing windows trying freeware and going to pornsites I would have to suspect the following:

Flash 10 is Viral.
The viral activity is sanctioned.
If the viral activity were not sanctioned by flash it would cause problems running under windows which it does not.
Windows is implicate in permitting and abetting sanctioned viral activity to function asymptomatic. 
Linux programmers do not promote a culture of sanctioned viral activity.
If Flash did theoretically have sanctioned viral content in the binaries they would not be able to reconcile it with the Linux OS. They might be able to get it to work but would not be able to get it to work smoothly without cooperation of the Linux programmers at which point th cat would be out of the bag and someone would come up with a fix...
So any sanctioned viral activity designed to run under Linux would have to be hidden from Linux developers because The Linux community helps my system to meet my needs in contrast to Windows where Bill Gates decides my needs.
A lot of this is preposterously conjectural, but possible.
It's just an unproven model that fits the evidence, I'm making no direct accusations.

The Flash 10 binaries install something on my drive outside of linux's file system that taxes system resources, affects secure text entry and internet browsing.
It is nonexistent on any install of Linux with any aps and other add-ons I've tried and appears immediately with the flash 10 install
Whatever it is also is persistent through various installs of Jaunty, Karmic, Debian Lenny, Ubuntu 9.10 Studio, and Ubuntu 9.10 Ultimate Edition. 
It is not persisting in memory. It is not uninstalling through Synaptic even though installed through Synaptic and is not written over by reinstalling the OS.
It is only purged by a drive wipe...writing random data to every sector on the partition to destroy any latent code.

I hope this profiling of the problem may lead someone to correct the issue.
I've corrected the issue by using Windows XP for my recreational flash media browsing and using Linux without flash for anything needing to be secure and going places that would corrupt my WindowsXP install.

---

