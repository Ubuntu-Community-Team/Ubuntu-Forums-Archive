---
title: "Ubuntu 9.10 hangs / freezes"
date: 2009-11-19
forum: General Help
---

### Post by greenwom on 2009-11-19
My fresh install of 9.10 on an older Compaq desktop is working great except that the system freezes every once and a while (when using firefox is when I've noticed it, then again I always have a browser open)

Symptoms:
Screen stay static where ever it frooze.
Mouse still tracks around the screen 
Can't drop to shell with Ctrl-Alt-F2

Have to then do a hard reboot....
What logs should I be looking into to find a problem. 

I did a search and can't find anything of use.  Once I can find a error in a log I'll post a bug.
Thanks in advance

---

### Post by colonelk on 2009-11-20
I have the exact same issue.

HP Compaq D310, p4 2.66ghz, 1GB RAM, 80GB Disk


Its not a matter of 'if' its 'when' and it is always firefox which causes it.  I'm using Opera as a workaround.

---

### Post by patate91 on 2009-11-20
I have the same issue and I tought it was Evolution that was causing the freezes. I installed Thunderbird, and same thing, ubuntu is still freezing. I also got freezes with gimp....

---

### Post by Sevy on 2009-11-20
I too am having this issue,usually whilst running Firefox & Wine

---

### Post by greenwom on 2009-11-20
can anyone force this to happen. 
if so post it.  I cant

---

### Post by djhk on 2009-11-27
I have a Wubi install of 9.10.
Firefox works fine on an ethernet connection.
If I use a wireless connection, Firefox hangs on my Google home page.
Some web pages load ok.

---

### Post by Jan Crikemans on 2009-11-28
I am working with Ubuntu 8.04 Hardy Heron. I have the same problem:  when I use Evolution, my screen freezes.  I can move my mouse pointer but that's all.  I have to do a hard reboot to start up again.  In my opinion it happened always while I was working with Evolution.  Thats why I installed Claws Mail this week.  But I have the same problem in Claws Mail.  
I think, there must be some problem with a network connection, but I have no idea what this could be.  I have a little home network with two ubuntu desktops and one netbook.  (Dual boot, Windows XP and Ubuntu Netbook Remix 9.10)  I make connection between my computers by SSH.
Can anyone tell me what's the cause of this problem.

---

### Post by pbhill on 2009-11-28
Same problem here. I'm using Opera to write this. Started about a week ago and has gotten progressively worse. I've never had any problems with Firefox before in either Ubuntu or Windows.

---

### Post by pbhill on 2009-11-28
As I was again attempting to use my favorite browser, it froze and I could see the memory usage slowly climbing to over 60%. The CPU usage was 128% (dual core). Then I got this error message. Can anyone decode it for me?

---

### Post by bluestar14 on 2009-11-28
same here, i am running a gateway...especially when using chrome, but then it spread to other programs, like the file explorer, ccsm, etc.

---

### Post by Jan Crikemans on 2009-11-29
I think in my case it has something to do with network problems.  I have disabled the automatically check for new mail.  I ask myself if the problem could have something to do with a system conflict on the moment when the mail program is uploading new mails. (Claws mail for the moment, but I had the same problem with Evolution.)

---

### Post by Jan Crikemans on 2009-11-29
I think in my case it has something to do with network problems. I have disabled the automatically check for new mail. I ask myself if the problem could have something to do with a system conflict on the moment when the mail program is uploading new mails. (Claws mail for the moment, but I had the same problem with Evolution.)

---

### Post by pbhill on 2009-11-29
I bit the bullet and did a clean reinstall of Karmic. The freeze ups and high CPU use (120%) in Firefox were affecting other apps. Unfortunately the reinstall had absolutely no effect on fixing Firefox's problem. I can't use it at all. I will say that the clean install has improved several issues, such as an overall increase in speed.
I hate to give up on Firefox, but I guess at this point I have little choice.

---

### Post by jimgeiser on 2009-11-30
> **pbhill said:**
> As I was again attempting to use my favorite browser, it froze and I could see the memory usage slowly climbing to over 60%. The CPU usage was 128% (dual core). Then I got this error message. Can anyone decode it for me?

I am having same problem and it seems to happen when there is a lot of traffic on internet. I am on cable and always on. I had a freeze up last evening while I was playing Klondike with only Thunderbird running in background. I suspect it is a program using java script that is causing a loop. I'm not sure how TB gets new messages, but it must be a js to set the timer to check for mail.
I have had Ubuntu 9.10 freeze and require a rd shut down on just about every situation so it is hard to find what it could be. looked through all kind of logs this morning and none shows what happened on last freeze.

---

### Post by mittwit on 2009-12-01
I have a Dell D630 and it too has been hanging with just mouse pointer movement. This started maybe a week ago and I was on 9.04 then. It seemed to have something to do with firefox or Prism. My Dell has nvidia graphics built in and I had the extra drivers running and thought that may have been the problem but I'm on the standard driver now and it still hangs.
I upgraded to 9.10 to see if that would fix the problem but I was still having problems a day ago. I used Epiphany instead of Firefox and Prism for a few hours and had no problems.
I'm trying to get it to hang now. I use Prism to display my google calendar, mail, docs and I thought I got into trouble after resizing a google doc spreadsheet but I can't get it to happen now.
My other theory was the pc was overheating but it dual boots to windows XP and it hasn't had a problem.
If it hangs tomorrow I will report back.

Update:
I think my problems lie with the nvidia graphics, maybe faulty hardware, though it is working now.
I had nasty messed up displays on ubuntu and xp. It seems more likely to work running xp.
Since I installed the latest driver from dell xp has been ok and now ubuntu is ok. I wouldn't think a xp driver would effect ubuntu unless there are some general machine settings that come with the dell update.

Currently I'm not using the special nvidia drivers for ubuntu and since the machine is working I will leave it as it is.

---

### Post by krimzonstarr on 2009-12-01
Running Karmic 9.10 desktop on AA1 ZG5 non-SSD. Been having the same exact problems, except it tends to drop to kernel panic and forces a hard power cycling. The problem started with flash video through firefox, then seemed to extend to any "heavy" network or processor use. Watching videos from my cellphone with VLC, downloading with Transmission, opening multiple tabs on Firefox, all reproduce the problem. Downloaded Midori, Chrome, Chromium, and Opera, and all have similar issues with video or high bandwidth. I am assuming this is some issue with the wifi or intel drivers, but have been unable to pinpoint the issue. Have tried clean installs of 9.10 and 9.10 UNR, issue persists.

---

### Post by geodanny on 2009-12-02
This problem also has plagued me for way too long. My computer will freeze. I can move the mouse but not click anything or close windows, and keyboard shortcuts do not respond. I had been thinking it was something pegging the CPUs or hogging memory. I have not had a freeze up in more than a week (knock on wood) since I disabled FF add ons: ad block, no script, ubuntu firefox modifications, flashblock, and greasemonkey. With any one of those enabled, it freezes once a day, usually after it wakes up from suspend mode. I can still use flash, Y! toolbar, delicious toolbar, and recap. I also run thunderbird but the only add on I use is enigmail.

I have a dell latitude d620 and run Ubuntu 9.10.

---

### Post by aum11 on 2009-12-02
I have had the same problem for a week or so.  Memory usage for firefox went all the way to well over 3gb. All that can happen is slow and jerky mouse movements.  I was also running prism gmail at the same time.

---

### Post by Sevy on 2009-12-02
Well I think Ive found a workaround for those who are using an Intel graphics card.I found the following post on linuxquestions.org forum

Found this in the ubuntu bugs (launchpad):

I found a workaround to this issue for those of you who have an intel graphic card (which is what HP Pavillion PCs come with).
you must revert to an older version of the graphic card driver by following these instructions:
[https://wiki.ubuntu.com/ReinhardTart...telDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")
The instructions were intended for Jaunty but they also work for 9.10

Ive been running 9.10 all day with no problems,hope someone can find a better solution

---

### Post by aum11 on 2009-12-02
I am having the memory problem using nvidia graphics

---

### Post by pbhill on 2009-12-02
> **krimzonstarr said:**
> Running Karmic 9.10 desktop on AA1 ZG5 non-SSD. Been having the same exact problems, except it tends to drop to kernel panic and forces a hard power cycling. The problem started with flash video through firefox, then seemed to extend to any "heavy" network or processor use. Watching videos from my cellphone with VLC, downloading with Transmission, opening multiple tabs on Firefox, all reproduce the problem. Downloaded Midori, Chrome, Chromium, and Opera, and all have similar issues with video or high bandwidth. I am assuming this is some issue with the wifi or intel drivers, but have been unable to pinpoint the issue. Have tried clean installs of 9.10 and 9.10 UNR, issue persists.

I have tried Midori and Opera, both worked just fine in Ubuntu. If I run Linux Mint via VirtualBox I have similar Firefox issues. When Running Mandriva with VirtualBox, Firefox works just fine... What's up here?

---

### Post by krimzonstarr on 2009-12-03
For the better part of the time since my last comment, I have reduced the kernel panic/lockups to only rarely during high bandwidth usage. I followed instructions on launchpad for upgrading to the custom ubuntu .15 kernel. Seems to be helping a lot. Unfortunately, I have made so many other config changes on this setup, it's hard to pin-point, and I simply refuse to do my 5th karmic reinstall lol. Working for now, so I'll take it.

---

### Post by Jan Crikemans on 2009-12-08
I have the impression that it happens when my emailprogram is downloading or uploading messages.  Could it be that there is some systemconflict then?

---

### Post by BroadArrow on 2009-12-25
> **greenwom said:**
> My fresh install of 9.10 on an older Compaq desktop is working great except that the system freezes every once and a while (when using firefox is when I've noticed it, then again I always have a browser open)

Symptoms:
Screen stay static where ever it frooze.
Mouse still tracks around the screen 
Can't drop to shell with Ctrl-Alt-F2

I'm experiencing the same thing, only I'm using Chrome. It seems the lowest common denominator is running a web browser?

---

### Post by earonesty on 2010-01-12
ubuntu 9.10 (installed via WUBI) hangs .... nothing i can see in the message log.   my solution is to start in "recovery mode", then "resume normal boot", then log in, then type "startx"

everything works when i do that

let me know if it works for you, i think it might point to the cause of the problem

 someone who knows a bit more about exactly what "recovery mode" does might be able to pinpoint things - for example

(but here i am, posting, using ubuntu on a machine that runs about 5 times better than when it was running win-slows vista... so i'm willing to boot that way if i have to)

---

### Post by Uadebisi on 2010-01-12
Same problem here! I use FF, although the freeze occurred while in Evolution as well as FF. Not sure if FF was open. 

I started my own thread here as well:
[http://ubuntuforums.org/showthread.php?p=8655632#post8655632](http://ubuntuforums.org/showthread.php?p=8655632#post8655632)

---

### Post by Uadebisi on 2010-01-14
Anyone find a solution for this yet?

---

### Post by the grey side on 2010-01-15
If your problem is similar to mine

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948)

(nvidia GPU, keyboard/mouse unresponsive etc.) you might want to try kernel 2.6.32-020632

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")

if you haven't already. It is the earliest kernel that has never given my any problem, but I always used it *without* Nvidia drivers.
I'm currently trying the later kernel 2.6.32-02063203

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.3/")

*with* Nvidia drivers installed. So far so good, but it's too early to be sure. I will post in my thread when I think I've done enough testing.

---

### Post by nexoncore on 2010-01-15
FireFox is known to be a memory hog, and the problem you are all having doesnt seem to be with ubuntu itself. You all appear to be running simultanious programs wich are resource hungry.

I am running ubuntu 9.10 on a p4 2Ghz Machine with 512mb Ram and a 30GB HDD ( Test Machine ) and have not had any issue, except with the wireless ( Netgear wpn111 ) which has always been an issue.

Just keep an eye on what programs are using too much, bare in mind each tab you have open in a browser means more resources the browser will use. Stop using programs which appear to be using way too much.

---

### Post by the grey side on 2010-01-15
I have a similar problem with windows 7, however I never experienced it with either 9.04 or vista. Moreover, I had freezes while running only Firefox, and even on login and shut down. And with a dual core processor and 4 GB of RAM I refuse to believe that merely running a browser can freeze my system.
At least for me, it is a software problem, be it a bug in 9.10 and windows 7, a strange driver incompatibility, or whatever else.

---

### Post by Uadebisi on 2010-01-21
> **the grey side said:**
> If your problem is similar to mine

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948)

(nvidia GPU, keyboard/mouse unresponsive etc.) you might want to try kernel 2.6.32-020632

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")

if you haven't already. It is the earliest kernel that has never given my any problem, but I always used it *without* Nvidia drivers.
I'm currently trying the later kernel 2.6.32-02063203

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.3/")

*with* Nvidia drivers installed. So far so good, but it's too early to be sure. I will post in my thread when I think I've done enough testing.

Hi grey side,

How exactly do I revert back to an old kernel? How do I determine which driver I am using from Ubuntu? Sure, I can look from Windows but I would like to know how to from Ubuntu :-)

I have tried Ubuntu a couple of times on different machines & there are always problems that render the OS more trouble than it is worth. Too bad really, as I like much about Ubuntu, it's simply not reliable. I spent countless hours in this forum recently in regards to another install on another machine only to eventually reformat & reinstall XP. I hope someone will fix this bug!

Thanks!

---

### Post by earonesty on 2010-01-21
[QUOTE=nexoncore;8668187]FireFox is known to be a memory hog, and the problem you are all having doesnt seem to be with ubuntu itself. You all appear to be running simultanious programs wich are resource hungry.
/QUOTE]

Mine hangs without needing to run anything.  It hangs shortly after login,regardless of running applications.

---

### Post by dineshbabumm on 2010-01-21
I am facing the same problem.. It just hangs every 15-20 min. It is very irritating. Any solutions or should we be reverting back to 9.04?

---

### Post by earonesty on 2010-01-22
Strange idea... but do you notice if it hangs shortly after the system makes a sound or as it's supposed to make a sound?  I'm starting to suspect an issue in the audio system.

---

### Post by tomtom12 on 2010-01-22
Since two weeks 9.10 I've got some freezes as well. Also loosing wireless Internet 3-4 times per day. Also got the idea it was related to FF. 

Seems some combination with Thunderbird. Since thismorning, I now use version 3 of TB and 3.6pre of FF ... and had no problems since :) ... keep fingers crossed.

---

### Post by johnstip on 2010-01-22
I am new to Ubuntu (about one month) and am having the same freezing problem running 9.1 on a Dell GX260 in a partition on a second hard drive.  The freeze happens in just about any program including simple games such as Solitaire which is hardly a memory hog.  This is particularly annoying when trying to build a spreadsheet.

With so many users reporting the same  problem in various ways and no real solution over two months of postings I am beginning to wonder if Ubuntu is the escape from Windows that I had hoped it would be. Is there a real solution out there?:confused:

---

### Post by Uadebisi on 2010-01-22
> **johnstip said:**
> I am new to Ubuntu (about one month) and am having the same freezing problem running 9.1 on a Dell GX260 in a partition on a second hard drive.  The freeze happens in just about any program including simple games such as Solitaire which is hardly a memory hog.  This is particularly annoying when trying to build a spreadsheet.

With so many users reporting the same  problem in various ways and no real solution over two months of postings I am beginning to wonder if Ubuntu is the escape from Windows that I had hoped it would be. Is there a real solution out there?:confused:

Hi,

I feel ya...I too came to Ubuntu a couple of months ago as I was tired of the work involved with A/V & A/S scanning, protection, etc with Windows. Well, I have already removed Ubuntu from 1 machine & went back to Windows, of which I have an entirely new appreciation! I figured I would try Ubuntu again on an old machine, as there wasn't much to lose & now I have the freezing problem. 

In my experience, Ubuntu is not a stable, reliable OS. This can be debated all day but that has been my experience. I was told as much by a friend of mine who is an IBM systems designer & computer wiz & he warned me...but I didn't listen.  I am an average computer user in regards to knowledge, & that is probably a conservative estimate. I have spent countless hours in this forum trying to get help for all of the countless problems that I've experienced. Some issues were resolved, & some not. I do like certain things about Ubuntu, so I stick around & people in the forum try to help but even the experienced tech type, seem to share our problems, albeit they are more apt to rectify such problems.

So....we wait & freeze...such is life with Ubuntu!

---

### Post by the grey side on 2010-01-22
> **Uadebisi said:**
> Hi grey side,

How exactly do I revert back to an old kernel? How do I determine which driver I am using from Ubuntu? Sure, I can look from Windows but I would like to know how to from Ubuntu :-)

Thanks!

The kernels I suggested are not old, they are newer than those you can install through the update manager. You can install them following this guide:

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

Those instructions are for the kernel 2.6.32, if you want kernel 2.6.32.3 instead you have to download the .deb files from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.3/")

(you need linux-headers-2.6.32-02063203_2.6.32-02063203_all.deb and the two packages for your architecture. You don't need linux-source-2.6.32_2.6.32-02063203_all.deb.)
Just be sure that you download the files for your architecture -- i386 if you have a 32-bit processor, AMD64 if it's a 64-bit processor (works both with AMD and Intel CPUs). If you don't know your CPU's architecture, look it up (on your manual, or the manufacturer's site, or Wikipedia, etc.)
If you have an Nvidia graphics card and an installed and working Nvidia driver in Ubuntu, you should find a "NVIDIA X Server Settings" link under applications/system tools or system/preferences in the menu. That should tell you driver version and other useful info, such as the GPU's temperature.
If not, you'll have to [download]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and install it. Note that you can't see which driver you have on Windows if you have installed it on Ubuntu, because drivers are dependent on the OS in which they are installed.
Installing NVIDIA drivers in Ubuntu is slightly more difficult than in Windows, I suggest you don't and try the kernel without drivers first. See if it works well, then try the drivers. There are installation guides for drivers around, or you can ask here and I'll (eventually) answer.

As for problems with Ubuntu, I've been using it since 8.10 and only 9.10 has given me so much trouble. I guess that such things happen now and then. 9.04 was more stable for me, if you can't solve your problems use that instead, if you want, or wait for 10.04.

---

### Post by juky on 2010-01-24
Hi,

I've just did the kernel update according to the above instructions. I will post here, if I notice changes, either good or bad.

Cheers,
juky

---

### Post by earonesty on 2010-01-26
Have you all tried dropping to a "recovery terminal" (1. boot to recovery mode/2. click resume) and then running "startx" from the terminal.

For me, that fixes it.  Except that various gdm services don't work.   Looks like it's gdm's fault.

---

### Post by nevdelap on 2010-02-02
I have a problem with the same symptoms, but while others are using Opera as a workaround I think Opera is causing my problem. When it happens it is always when Opera is minimized and I bring it up by clicking on it's icon in the system tray. It comes up, with the address bar drop down open and empty. At this point the mouse is movable, but clicks are ignored, any keyboard activity is ignored, and I have to go to my other laptop and reboot via ssh.

Nev

I am running 9.10 with Opera 10.10 4742. It started happening maybe two or three weeks ago for me.

I tried to attach a dpkg -l but the limit on txt files is a poor 19.5KB!

I've removed the Opera system tray icon, hopefully will workaround the problem.

---

### Post by juky on 2010-02-03
> **juky said:**
> Hi,

I've just did the kernel update according to the above instructions. I will post here, if I notice changes, either good or bad.

Cheers,
juky

So, after upgrading to 2.6.32 no freezing anymore. Will keep you posted.

Cheers,
juky

---

### Post by the grey side on 2010-02-04
Glad to hear that it worked for you!
For anyone who still experiences freezes, read this post if you haven't already, it might help you:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8766852&postcount=148](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8766852&postcount=148)

---

### Post by archish on 2010-02-07
I tried updating to 2.6.32.7 but still facing the same problems :/
I am actually pretty sick of this now. The Launchpad bug is here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498495)

---

### Post by the grey side on 2010-02-07
If you have time, you could try the earlier kernel 2.6.32.3, just in case the bug resurfaced in the kernels after that one.
Personally, since 2.6.32.3 solved my problem, I'm too afraid to try any later release. I really hope that 10.04 will squish this bug for good and we'll remember 9.10 as Krashing Koala with a mix of relief and nostalgia for those afternoons lost in front of a frozen monitor.

---

### Post by Amrobadr on 2010-02-07
Facing the same problem :(

but my PC totally hang, I can't even move the mouse !!

Any Solutions for this bug !!

---

### Post by archish on 2010-02-07
> **the grey side said:**
> If you have time, you could try the earlier kernel 2.6.32.3, just in case the bug resurfaced in the kernels after that one.
Personally, since 2.6.32.3 solved my problem, I'm too afraid to try any later release. I really hope that 10.04 will squish this bug for good and we'll remember 9.10 as Krashing Koala with a mix of relief and nostalgia for those afternoons lost in front of a frozen monitor.


Lucid will use the latest kernel version + ubuntu specifi patches so if the issues was not there for one particular version of kernel then Lucid too may have the same hanging issue :(

I had installed the kernel 2.6.32.5 initially which was stable for a week before upgrading to 2.6.32.6 which started hanging. Now I am not sure where to track this bug as there is no error or anything logged anywhere :@

The closest bug I found to this issue was this: [http://bugzilla.kernel.org/show_bug.cgi?id=14922](http://bugzilla.kernel.org/show_bug.cgi?id=14922) 
My system is based on MCP79/MCP7A chipset whose related bug is here: [http://bugzilla.kernel.org/show_bug.cgi?id=14817](http://bugzilla.kernel.org/show_bug.cgi?id=14817)
Both the bug is not there for users in 2.6.31 :/ so its not related
Will monitor both these bugs and test the new kernel when they are patched. Have loaded Jaunty with 2.6.30 kernel as of now.

---

### Post by Rehdon on 2010-02-08
I have this problem too: tried almost everything that was suggested in this and other threads, to no avail ...

BTW, I have a Sony laptop with an ATI card (HD3400), what happens if I upgrade to the new kernel? how do I install the corresponding fglrx driver?

Rehdon

---

### Post by zackpuse on 2010-02-08
I have the exact same issue.

Compaq presario v3000 centrino duo 2.2ghz, 4GB RAM, 320GB Disk.

Its not a matter of 'if' its 'when' and it is always firefox namoroka 3.6.2pre which  causes it.

---

### Post by archish on 2010-02-09
for all who are having stability issues try upgrading to 2.6.32 kernel. For me the system is stable with 2.6.32.5. The issue reappears with 2.6.32.6 and higher. There are links to how to install the new kernel by* the grey side* in this thread.

---

### Post by Rehdon on 2010-02-10
> **archish said:**
> for all who are having stability issues try upgrading to 2.6.32 kernel.

Upgrading to a new kernel is easy, updating the graphic drivers not as much: I tried, could not install it (also tried from the ATI site, generating debs) and had to go back to the previous kernel :(

Is there a repository with the latest flgrx drivers? Or should I simply put the lucid repos in my sources.list?

Rehdon

---

### Post by science.copperfield on 2010-02-11
I'm running a fresh install of 9.10 on an old Dell Inspiron 1100.  After following these instructions, my "freeze" issues have been resolved.

I felt it necessary to report duplicated success with this solution because I have seen numerous other posts on this forum where an individual attempts a solution, reports a resolution, then a retraction (their install still freezes)

So...after 2 days of running the 2.6.32.3 kernel, my freezes have permanently been thawed out :p

> **the grey side said:**
> The kernels I suggested are not old, they are newer than those you can install through the update manager. You can install them following this guide:

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

Those instructions are for the kernel 2.6.32, if you want kernel 2.6.32.3 instead you have to download the .deb files from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.3/")

(you need linux-headers-2.6.32-02063203_2.6.32-02063203_all.deb and the two packages for your architecture. You don't need linux-source-2.6.32_2.6.32-02063203_all.deb.)
Just be sure that you download the files for your architecture -- i386 if you have a 32-bit processor, AMD64 if it's a 64-bit processor (works both with AMD and Intel CPUs). If you don't know your CPU's architecture, look it up (on your manual, or the manufacturer's site, or Wikipedia, etc.)
If you have an Nvidia graphics card and an installed and working Nvidia driver in Ubuntu, you should find a "NVIDIA X Server Settings" link under applications/system tools or system/preferences in the menu. That should tell you driver version and other useful info, such as the GPU's temperature.
If not, you'll have to [download]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and install it. Note that you can't see which driver you have on Windows if you have installed it on Ubuntu, because drivers are dependent on the OS in which they are installed.
Installing NVIDIA drivers in Ubuntu is slightly more difficult than in Windows, I suggest you don't and try the kernel without drivers first. See if it works well, then try the drivers. There are installation guides for drivers around, or you can ask here and I'll (eventually) answer.

As for problems with Ubuntu, I've been using it since 8.10 and only 9.10 has given me so much trouble. I guess that such things happen now and then. 9.04 was more stable for me, if you can't solve your problems use that instead, if you want, or wait for 10.04.

---

### Post by ibates on 2010-02-12
A first for me with Ubuntu. The system has hung. Well almost hung.

After installing the  automatic updates for 29 January 2010 - when selecting almost any application the system almost hangs. By almost hangs, I mean, the cursor will move very slightly once every 10 seconds or so, but even if it can be manipulated to a certain point, no action can be taken.

The only way out of this situation that I have been able to find is a hard reboot. (I was used to this type of thing with Windows XP, but had never seen it before with Ubuntu).

Reverting to Ubuntu Linux 2.6.31-17-genereic-PAE at the GRUB boot up option screen lessens, but does not solve, the problem.

After update to 2.6.31-17-genereic-PAE system still freezes up (partly - if there is a movie going at the time for example, the sound will continue in the background but everything else comes to a near standstill. And of course it happens with or without anything running at the time. Sometimes the system is idle when the freeze occurs).

As I mentioned above, it is not a complete freeze because if one waits for ten or fifteen seconds, the mouse pointer can be moved normally for a few seconds then it quickly slows down to a stop. No action can be taken no matter where the pointer is positioned. The only recovery from this situation is a hard reboot.

Sometimes it will operate normally for hours on end and then all of a sudden, for now apparent reason - freeze. But mostly it is within the first fiftennminutes of startup.  It is getting to be just like Microsoft Windows - intolerable.

This does NOT happen if I return to running Win XP, which it is starting to look like I may have to do, God forbid.  But having a machine hang every fifteen minutes or so is simply not on.

I can find no hardware inconsistency.

(This is an extract from a thread of mine elsewhere on this forum which to date, has had no response.  Hopefully someone might notice this).

Assistance please.

---

### Post by juky on 2010-02-12
> **ibates said:**
> A first for me with Ubuntu. The system has hung. Well almost hung.

After installing the  automatic updates for 29 January 2010 - when selecting almost any application the system almost hangs. By almost hangs, I mean, the cursor will move very slightly once every 10 seconds or so, but even if it can be manipulated to a certain point, no action can be taken.

The only way out of this situation that I have been able to find is a hard reboot. (I was used to this type of thing with Windows XP, but had never seen it before with Ubuntu).

Reverting to Ubuntu Linux 2.6.31-17-genereic-PAE at the GRUB boot up option screen lessens, but does not solve, the problem.

After update to 2.6.31-17-genereic-PAE system still freezes up (partly - if there is a movie going at the time for example, the sound will continue in the background but everything else comes to a near standstill. And of course it happens with or without anything running at the time. Sometimes the system is idle when the freeze occurs).

As I mentioned above, it is not a complete freeze because if one waits for ten or fifteen seconds, the mouse pointer can be moved normally for a few seconds then it quickly slows down to a stop. No action can be taken no matter where the pointer is positioned. The only recovery from this situation is a hard reboot.

Sometimes it will operate normally for hours on end and then all of a sudden, for now apparent reason - freeze. But mostly it is within the first fiftennminutes of startup.  It is getting to be just like Microsoft Windows - intolerable.

This does NOT happen if I return to running Win XP, which it is starting to look like I may have to do, God forbid.  But having a machine hang every fifteen minutes or so is simply not on.

I can find no hardware inconsistency.

(This is an extract from a thread of mine elsewhere on this forum which to date, has had no response.  Hopefully someone might notice this).

Assistance please.

This surely looks like a driver problem (video driver possibly). I am not such a huge expert on troubleshooting. Try again to repost in some other, maybe driver related thread, with details on your graphics HW.

Good luck,
juky

---

### Post by archish on 2010-02-18
I have raised a bug report in nvidia forums, It may be driver issue :(
[http://www.nvnews.net/vbulletin/showthread.php?t=147981](http://www.nvnews.net/vbulletin/showthread.php?t=147981)

---

### Post by timpo17 on 2010-02-18
hey all,

I'm getting the same results as others with kernel 2.6.31-14. freezes if i overload the memory running multiple apps, using multiple tabs in a web browser, and if i leave the system untouched for a few minutes. Its been freezing 5-10x a day and frequently has trouble loading the kernel.

Ive been having to reboot using ALT+PRNTSCRN+B, after having unmounted my drive when the kernel hasn't crashed(when you are still able to use the mouse)...otherwise, once tab starts blinking and the mouse stops moving, i have to do a hardboot. 

I tried downgrading my intel driver, as it was suggested someplace, but they(the freezes) are still happening (perhaps a little less frequently).  
I also tried upgrading to 10.04 (Lucid) but they were happening there as well.

I'm going to try the kernel *Grey Side* suggested and will report back.  If it doesn't solve it, I'm giving up...rolling back to HARDY.

-timpo

---

### Post by juky on 2010-02-19
> **timpo17 said:**
> hey all,

I'm getting the same results as others with kernel 2.6.31-14. freezes if i overload the memory running multiple apps, using multiple tabs in a web browser, and if i leave the system untouched for a few minutes. Its been freezing 5-10x a day and frequently has trouble loading the kernel.

Ive been having to reboot using ALT+PRNTSCRN+B, after having unmounted my drive when the kernel hasn't crashed(when you are still able to use the mouse)...otherwise, once tab starts blinking and the mouse stops moving, i have to do a hardboot. 

I tried downgrading my intel driver, as it was suggested someplace, but they(the freezes) are still happening (perhaps a little less frequently).  
I also tried upgrading to 10.04 (Lucid) but they were happening there as well.

I'm going to try the kernel *Grey Side* suggested and will report back.  If it doesn't solve it, I'm giving up...rolling back to HARDY.

-timpo


As I already mentioned, no issues for me after upgrading to 2.6.32. Hope you will have the same.

Cheers,
juky

---

### Post by timpo17 on 2010-02-19
Juky n Grey Side-

I've been using 2.6.32 for about 48hrs now.  the majority of the problems are gone, esp the one where it can't stay idle w/o freezing.  the kernel sticks when i overload the web browser, not the biggest prob(its happened to me dating back to hardy)..also, when grub is loading there seems to be a few errors. 

still a **major** improvement to .31-14! 
THANK YOU

they should rename the release karmic "krash" koala:wink:

-tpo

EDIT: forget what i said- .32 crashes a bunch as well..

---

### Post by Uadebisi on 2010-02-26
Well, I finally upgraded the kernel to 2.6.32.3 as per Grey Side's suggestions. We'll see what happens...

**Grey Side** said,
> If you have an Nvidia graphics card and an installed and working Nvidia driver  in Ubuntu, you should find a "NVIDIA X Server Settings" link under  applications/system tools or system/preferences in the menu. That should tell  you driver version and other useful info, such as the GPU's temperature.
If  not, you'll have to download ([http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us))  and install it.I do not understand this though. Why the talk of an Nvidia graphics card & do I need to download one for some reason?

Also, don't understand this either... > you should find a "NVIDIA X Server Settings" link under  applications/system tools or system/preferences in the menuI followed the paths above but find no "applications/system tools" in the menus & "system/preference" & then where?

Thanks!

UPDATE- About 10 minutes after updating, I heard the Ubuntu drum sound & the screen went black. I used cntrl alt del to restart. But why did the screen go black...now what?

Also, when Ubuntu updates, won't that again change the kernel?

---

### Post by Uadebisi on 2010-02-26
Another update & would love an opinion...

Left the pc alone for a while & when I came back, it was again frozen on a blank, black screen. This time however, I could not use control-alt-delete to reboot as the machine was frozen. I did notice that the monitor light was yellow, not green which would indicate that it was frozen in sleep mode.

---

### Post by the grey side on 2010-02-26
> **"Uadebisi"]I do not understand this though. Why the talk of an Nvidia graphics card & do I need to download one for some reason?[/quote]
> I followed the paths above but find no "applications/system tools" in the menus & "system/preference" & then where?I added the part about Nvidia cards in case you have one in your PC said:**
> About 10 minutes after updating, I heard the Ubuntu drum sound & the screen went black. I used cntrl alt del to restart. But why did the screen go black...now what?No idea, could you use the PC after restarting? Did you notice some improvement?

> Also, when Ubuntu updates, won't that again change the kernel?It will install new kernels, but 2.6.32.3 should be on top of the GRUB list, and will remain the default option, until a kernel with a higher number after 2.6 is installed. Until now, only 2.6.31 kernels have been released for 9.10 through the update manager. None of those should be above 2.6.32 kernels, even if installed later.
Anyway, in case you need it, you can access the GRUB menu with the list of kernels when you power on your PC, and select the kernel you want. All installed kernels can be used. I dual boot Ubuntu and Vista and the GRUB menu is always displayed for me on boot. If you have only Ubuntu, you should be able to display the menu by pressing either esc or shift when you see the word GRUB, a few moments after pressing the power on button.

edit:

> Left the pc alone for a while & when I came back, it was again frozen on a blank, black screen. This time however, I could not use control-alt-delete to reboot as the machine was frozen. I did notice that the monitor light was yellow, not green which would indicate that it was frozen in sleep mode.Make sure that your computer is set to never hibernate or suspend, I have read that those options can cause problems.

---

### Post by Uadebisi on 2010-02-26
Thanks grey side!

As far as the Nvidia card...yea, after rereading your post & checking my pc, I realized that your suggestion did not apply.

> No idea, could you use the PC after restarting? Did you notice some improvement?

Yes, I could use the pc after restarting & the machine is behaving much worse now that I have upgraded to the new kernels as indicated in my two examples :-( I used to get more time between freezes & like I said, now it's freezing while sleeping too.

This is in no way directed at you but this Ubuntu experience has really been disappointing, to say the least. I started using it a few months ago & have always had problems...too many to list. I have tried 9.10 & 9.04 to no avail. It simply cannot be taking seriously as a OS. I was hoping to find a Windows alternative that was virus free but it seems as if Mac is the answer for that, of which I have one. I like Ubuntu... when it's working. 

On the homepage of the Ubuntu site, there should be a warning to the effect of "use at your own risk & expect to spend ungodly amounts of your personal time trying to get this unstable OS to function properly...& whatever you do, DO NOT  REMOVE WINDOWS, as you will need it!" ;)

I will try once more using the suggestion here: [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8766852&postcount=148](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8766852&postcount=148)  ...then that's it for Suckbuntu!

---

### Post by Uadebisi on 2010-03-02
Well, I tried "The Cat's" method of enabling Karmic proposed/pre-released updates & shortly thereafter my screen locked up while in sleep mode again. I have since disabled sleep mode for the monitor & am only using a blank screensaver instead. Doesn't achieve the same results but am curious to see what happens now. 

I am certainly not expecting much considering that I have never had Ubuntu work without an issue for any length of time but we'll see...

---

### Post by bangbong on 2010-03-04
Just update the kernel 2.6.31-20-generic to 2.6.32-020632-generic

so far so good at my side.

---

### Post by Uadebisi on 2010-03-05
So, since upgrading to 2.6.32.3 last week, here's what has happened...

-repeatedly froze while sleeping
-enabled Karmic Pre-Released Updates & still froze
-enabled screen saver & maintained sleep mode & machine stopped freezing while sleeping
-enabled Firebug which seemed to cause machine to freeze vary quickly(not while sleeping)
-disabled Firebug & had no freezing for a day
-disabled Pre-Released to test & machine froze almost immediately
-enabled Pre-Released again & machine didn't freeze for a few hours
-froze again while online

So, there you have it. After all that, the machine is still freezing. Why am I not surprised!
Windows & Mac...here I come with open arms & a new found appreciation! ;)

---

### Post by Rehdon on 2010-03-06
Have fun with Windows and Mac.

For those of us who love Ubuntu Linux, I must say this bug is quite frustrating. Does it affect so few users that no fix is deemed necessary? I've been using the REISUB commands to shutdown my laptop for several weeks now, I hope at least it will be fixed in 10.04.

Rehdon

---

### Post by vodgut on 2010-03-09
Just wanted to follow up on this.

I have two machines on 9.10, and am seeing this on just one of them.

The first has a Asus P6X58D motherboard, i7, with an nVidia GTX280 video card.  It runs fine and I've never seen this issue.  This is a new machine to me.

I have another machine, Asus A8N-SLI with an Athlon 64 X2.  nVidia 7800GT video card.  It happens almost as soon as I try and do anything with X on this machine.  Sometimes prior to login, sometimes I'm able to do something like try and change the desktop background.  Happens before any browser launch (have never been able to get that far without the same freeze described earlier, and X eating up the CPU).  This machine successfully ran 8.04 for years with no issue like this, so I don't think it's hardware.

I set up a static IP and ssh server so I could get into the machine to reboot it.  Killing (kill -9) X remotely will restart just the X server, so the non-graphical parts of the OS were still running fine.

I tried updating with the karmic-proposed packages.  No dice.  Trying the kernel update idea soon.  Thanks all for the suggestions so far.

I would like to use nVidia acceleration for this machine, but it seems like this isn't just specific to nVidia cards.  There was some earlier mention of Intel graphics.

But it seems pretty widespread, and I hope there's a fix for this soon.

---

### Post by vodgut on 2010-03-09
No luck with the new kernels (2.6.32.5 or 2.6.32.3).  Karmic is hosed for that machine, unless I wanted to run with no X, which I don't.

I would classify this as a pretty big bug, and given the number of respondents here not totally uncommon.

Suppose I'll try 9.04 on it.

---

### Post by MasterNetra on 2010-03-09
> **greenwom said:**
> My fresh install of 9.10 on an older Compaq desktop is working great except that the system freezes every once and a while (when using firefox is when I've noticed it, then again I always have a browser open)

Symptoms:
Screen stay static where ever it frooze.
Mouse still tracks around the screen 
Can't drop to shell with Ctrl-Alt-F2

Have to then do a hard reboot....
What logs should I be looking into to find a problem. 

I did a search and can't find anything of use.  Once I can find a error in a log I'll post a bug.
Thanks in advance

Its a video driver/GPU issue. I have the same issue with my Gateway 500se and Linux Distros. It does this with Fedora(less frequently), *buntus, Opensuse (More frequently), Debian, and a number of others. Tinycore and Puppy/MacPup don't seem to have this issue. But Ubuntu Lucid Alpha 3 has been catching these and allowing me to restart xorg and such without restarting the system entirely and so I got to send a bug report and its pointed to the the Drivers/xorg/GPU. Sadly it doesn't save me when I go to screensaver and the preview of the screen savers play... The Ant Light in particular. My Gateway uses NVIDIA drivers...though strange considering its a Intel Video card and not a NVIDIA card.

---

### Post by vodgut on 2010-03-10
New update: 9.04 seems to have the same issue.  Going back to 8.04, which ran fine....

---

### Post by bangbong on 2010-03-10
after the upgrade, my box is working and running fine. no reboot and pulse is working good. stick with 9.10 until it break ....

---

### Post by c-oss on 2010-03-10
I am new to xubuntu - I usually use fedora but recently bought a new laptop and fedora was having trouble with the nvidia driver and wireless - freezing issues on fedora and well, intermittent wireless. Thought i'd try xubuntu - it was running fine live (other than network due to firewall) but no i'm getting intermittent freezing, sometimes i'm running next to nothing (no firefox) and i can't move the mouse and keyboard is deactivated....

---

### Post by dnguyen1963 on 2010-03-10
> **Uadebisi said:**
> Hi,

I feel ya...I too came to Ubuntu a couple of months ago as I was tired of the work involved with A/V & A/S scanning, protection, etc with Windows. Well, I have already removed Ubuntu from 1 machine & went back to Windows, of which I have an entirely new appreciation! I figured I would try Ubuntu again on an old machine, as there wasn't much to lose & now I have the freezing problem. 

In my experience, Ubuntu is not a stable, reliable OS. This can be debated all day but that has been my experience. I was told as much by a friend of mine who is an IBM systems designer & computer wiz & he warned me...but I didn't listen.  I am an average computer user in regards to knowledge, & that is probably a conservative estimate. I have spent countless hours in this forum trying to get help for all of the countless problems that I've experienced. Some issues were resolved, & some not. I do like certain things about Ubuntu, so I stick around & people in the forum try to help but even the experienced tech type, seem to share our problems, albeit they are more apt to rectify such problems.

So....we wait & freeze...such is life with Ubuntu!



I got fed up with Ubuntu 9.04 and 9.10...all the lockups and freezes...went back to Ubuntu 8.10 without a hitch.

---

### Post by timpo17 on 2010-03-10
> **Uadebisi said:**
> So, since upgrading to 2.6.32.3 last week, here's what has happened...

-repeatedly froze while sleeping
-enabled Karmic Pre-Released Updates & still froze
-enabled screen saver & maintained sleep mode & machine stopped freezing while sleeping
-enabled Firebug which seemed to cause machine to freeze vary quickly(not while sleeping)
-disabled Firebug & had no freezing for a day
-disabled Pre-Released to test & machine froze almost immediately
-enabled Pre-Released again & machine didn't freeze for a few hours
-froze again while online

So, there you have it. After all that, the machine is still freezing. Why am I not surprised!
Windows & Mac...here I come with open arms & a new found appreciation! ;)

haha, don't give up! if you want to stay w ubuntu, go back to HARDY 8.04 which is LTS(for a good reason).. last year i had to get away from INTREPID caus of the bugs.

i gave up on 9.04 and on(including the .32 kernel) n switched to xubuntu8.1 \\:D/

theres plenty of distros out there, create a bunch of live cds and explore;)

dnguyen1963, vodgut- im with ya!

c-oss- we're talkin bout the freezes in _ubuntu 9.1_ not xubuntu...but sounds like a driver problem...

peace n love
timpo

---

### Post by ebro173 on 2010-03-10
Just wanted to register that I also have this problem on an old Dell Inspiron 6000.  I installed 9.10 i386 on it and for the most part I like it.  But, in the last couple of weeks it has started to freeze up.  Mostly it seemed to happen when I opened Firefox.  But, it also happens when I'm doing other things too - like copying files to a jump drive.  I've really liked 8.04 LTS.  I was anxiously awaiting the new LTS.  But, this problem is a real pain.  

I also have boot issues.  Some times I have to hard reboot during a frozen bootup.  Its the page table error problem that I'm pretty sure the developers are aware of already.

I've got the 31-19 version of the kernel installed.

PS I'm trying the thing about enabling the Pre-released sources.  Don't know if that is what did it, but, I'm downloading and installing the 31-20 kernel through the update manager.

---

### Post by vodgut on 2010-03-10
Okay, I think I may have fixed my system.  At least, X has been stable for about 30 minutes under Karmic, which is about 28 minutes longer than before.

The problem seems to be the default, non-accelerated X drivers.  Note the following will only work if you actually have an nVidia card.  It's possible native or proprietary drivers exist for other chips, but I haven't used them.  I'm not sure if Intel repackages nVidia, as pretty much everything is nVidia or ATI these days.  You can probably find out what you have by:

```
lspci | grep -i nvidia
```

will have a line, on my problem machine, that looks like:

```
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
```

So the trick is to get the nVidia restricted drivers installed.  The GUI offers to do this for you, but I couldn't get that far as my X would freeze up usually before my first application launch.  It helps massively if you have command line access, and preferably remote access from another machine with ssh.  You can start off before even logging into the GUI by ctrl-alt-F1 to get a console.  You can also install openssh-server

```
sudo apt-get install openssh-server
```

Then configure a static IP to get into it over the network.  Instructions from the command line:

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

That way if X hangs up you can ssh in and, as root, kill -9 the X process.  It'll at least restart you back to the login screen.  You can also perform the other steps over the network if your display gets messed.

Now you need to install and activate the nVidia restricted drivers.  Either sudo these or run them from a root shell.

```
apt-get install nvidia-glx-185
```

(note that 185 is the current version, not sure if this will change).  I think this installs all the dependencies as when I tried to install nvidia-settings it was already there.  To activate them, run the command line:

```
nvidia-xconfig
```

This should set up your system to use the restricted drivers you installed.  Reboot.  At this point, X has been stable for me.  I'll update if it doesn't stay that way.  You can see the settings for your nVidia card once you're back in X via System->Administration->NVIDIA X Server Settings 

I think this bug has been around for a while.  While in the graphical installation for 8.04, I ran into the same issue.  It occurs to me that the first time I installed 8.04 it was over the network and so probably automatically updated the nVidia restricted drivers I already had.

I suppose if you run into this issue during installation you could do the text-mode install (I think that's on the alternate CD)

Anyway, good luck.  I hope this helps some of you.

---

