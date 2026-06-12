---
title: "GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)"
date: 2010-03-30
forum: General Help
---

### Post by cheinze5719 on 2010-03-30
Currently running 10.04. Just did some updates and when it finished rebooting it just doesn't work right. Whenever I click on my user name to enter my password it freezes for 3-5 seconds then the screen reloads. If I do Ctrl+Alt+F7 I get this error(the title of the thread). I have no earthly idea what this means but everything was working great until I did my updates just a couple hours ago.

Anyone know what's going on??

---

### Post by mörgæs on 2010-03-31
EDIT 2011-03-02:

The problem is solved for the **10.04.2** ISO:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917)


For **10.10**:
If the installation goes well, the bug will be fixed when you apply the latest updates. If installing gives trouble, post 176 later in this thread will tell you how to install.

---

### Post by dregin on 2010-04-04
I just got this when trying to boot into the live disc for i386 desktop 10.04 beta 1.

---

### Post by ngoc1414 on 2010-04-30
10.04 install fails at bootsplash:
I use LiveUSB to install Ubuntu 10.04 Final, on my pc, when bootsplash is running, Error messages:
> GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0) 
                                                                                 stdin: error 0 
 stdin: error 0 
 stdin: error 0 
 stdin: error 0 
 stdin: error 0 
But, in my father 's pc, no problem.
Is that bug ? How to fix ?
(I'm Vietnamese, so English level is very low, sorry :D)

---

### Post by mörgæs on 2010-04-30
Do you also get the error when booting from a CD?

---

### Post by Copernicus1234 on 2010-04-30
> **dregin said:**
> I just got this when trying to boot into the live disc for i386 desktop 10.04 beta 1.

I get it when booting the retail (release) version of 10.04... :(

I have filed a new bug report by booting into my Ubuntu 9.10 and running "ubuntu-bug linux" in a terminal, then using the "getpwuid_r(): failed due to unknown user id (0)" as a error message." as the topic for the bug.

---

### Post by mörgæs on 2010-04-30
> **Copernicus1234 said:**
> 
I have filed a new bug report by booting into my Ubuntu 9.10 and running "ubuntu-bug linux" in a terminal, then using the "getpwuid_r(): failed due to unknown user id (0)" as a error message." as the topic for the bug.

Good. Please link to the bug report so people with the same problem can add their findings in the same report rather than opening a new one.

---

### Post by Copernicus1234 on 2010-05-01
> **mörgæs said:**
> Good. Please link to the bug report so people with the same problem can add their findings in the same report rather than opening a new one.

Absolutely.

Its this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279"). I picked it when bug reporting so my system info would get added to their database. Post #5 in that thread is mine, with some info about duplicate bug reports I found for this bug.

---

### Post by anggitoruan on 2010-05-03
> **ngoc1414 said:**
> 10.04 install fails at bootsplash:
I use LiveUSB to install Ubuntu 10.04 Final, on my pc, when bootsplash is running, Error messages:

But, in my father 's pc, no problem.
Is that bug ? How to fix ?
(I'm Vietnamese, so English level is very low, sorry :D)


I have the EXACT problem...it works in my father's PC...but no luck w/ my PC...:(

---

### Post by dino99 on 2010-05-03
seen the report, you may try with unetbootin

seem to be an issue with some cd/dvd readers

---

### Post by Copernicus1234 on 2010-05-03
> **dino99 said:**
> seen the report, you may try with unetbootin

seem to be an issue with some cd/dvd readers

The same CD reader was used to install Ubuntu 9.04 and 9.10 so if its the CD, some kind of regression has occured. :(

---

### Post by James78 on 2010-05-08
This error occurs from time to time with me, and I don't even have any CD/DVD drives connected or installed, not ever. And I installed from a flash drive (using the iso image), not the CD/DVD drive...

---

### Post by Dict on 2010-05-08
I installed the Ubuntu 10.04 LTS Final Release from DVD. 

I met the same piece of code, before the user login. But I can successfully login system, AND I do not know whether the error affected the other programs.

When I use Lucid, encountered some strange and rare problems. For example, cannot recognize usb modem (huawei EC1260) , cannot install tomboy-image, etc.

Lucid made me very confused. I am thinking about going back to the Karmic (9.10). Karmic is OK.

---

### Post by Copernicus1234 on 2010-05-08
> **Dict said:**
> I installed the Ubuntu 10.04 LTS Final Release from DVD. 

I met the same piece of code, before the user login. But I can successfully login system, AND I do not know whether the error affected the other programs.

When I use Lucid, encountered some strange and rare problems. For example, cannot recognize usb modem (huawei EC1260) , cannot install tomboy-image, etc.

Lucid made me very confused. I am thinking about going back to the Karmic (9.10). Karmic is OK.

Yes, Lucid feels very unstable. But I know that some people experienced the same with Karmic, so naturally it all depends on what kind of bugs and glitches exists in each version and how it affects each user.

Since I cant install Lucid, I have started looking into other distributions, but we'll see if I take the plunge or not.

---

### Post by Catharsis on 2010-05-08
Does anyone know what graphics card they have?
```
lspci | grep VGA
```

I *think* I remember this being the error message for the intel driver on i8xx card. Try:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Copernicus1234 on 2010-05-08
> **Catharsis said:**
> Does anyone know what graphics card they have?
```
lspci | grep VGA
```

I *think* I remember this being the error message for the intel driver on i8xx card. Try:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Here's mine:

01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)

---

### Post by James78 on 2010-05-09
> **Catharsis said:**
> Does anyone know what graphics card they have?
```
lspci | grep VGA
```

I *think* I remember this being the error message for the intel driver on i8xx card. Try:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
I get this..
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

But I'm _pretty_ sure that that is not i8xx or whatever, soo ya.

---

### Post by coorior on 2010-05-09
.
Installed 10.04 the day (actually it was 3 o'clock at night in the country i stay) it was released. everything worked perfect, except some minor bugs. but later on it started to give me :   

GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

it's a known bug. many people ( thousands if not more) have encountered it.  i just hope they fix it soon ,, because my installation getting weirder every time i boot again.

---

### Post by James78 on 2010-05-09
Getting weirder? In what way? Slower, more messed up..?

---

### Post by morphmatrix on 2010-05-17
mine too, i regularly get that same error upon booting, a quick fix is by force reboot my system ctrl + alt + sysrq REISUB.  im using asus eee box b202 intel atom.

---

### Post by tylersontag on 2010-05-19
i get this same problem on my primary HDD install.

The most annoying aspect is i can't even access my ctrl-alt-fX terminals, i just get that message on the splashscreen and im stuck with it untill i cold boot...

Anyways, this is QUITE annoying as you might suspect, im running off a live copy of 10.04 and getting by... but its like living out of a suitcase, i just want to go home!  Any ideas?

---

### Post by mörgæs on 2010-05-20
It is a generic error and therefore difficult to diagnose. I have not heard of any cure (except staying with 9.10).

---

### Post by cocolocko on 2010-05-20
I have the same Problem, with a HP Pavilion DV4-1414LA Laptop and the latest F.54 BIOS. The Install Process stopps with the error Message "GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)"
It doesent work with the regular Ubuntu and Kubuntu 64bit Version CD.
I only have luck with the Ubuntu alternate CD and with the DVD it works great!

some solutions out there? :confused:

Greetings

---

### Post by joel2007 on 2010-05-23
This is the message I get after install *Lubuntu* 10.04
> process 205 glib warning failed due to unknown user id

---

### Post by James78 on 2010-06-14
I HATE this message. It's starting to occur more often for me. Seems to happen every other boot. Right now, it just happened 2 times in a row after I halted the system.. Seriously frustrating..

---

### Post by mörgæs on 2010-06-16
Have any of you guys tried a minimal Ubuntu? Less packages = less risk of having a faulty package. Though not a guarantee, it should lower the risk of encountering this error.

---

### Post by wieman01 on 2010-06-22
Having the same problem and the frequency increases... Very disturbing. 
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I could live with the occasional error message, but it's the number of occurrences lately which concern me.

---

### Post by GenLinux on 2010-06-22
Confirmed on HP Pavilion W5060 too :\

Really there's nothing we can do to fix it, giving a try to 9.10.

---

### Post by mörgæs on 2010-06-22
> **GenLinux said:**
> 

Really there's nothing we can do to fix it, giving a try to 9.10.
That will almost certainly fix the problem. 

I forgot the link to the minimal installation, in anyone wants to experiment in 10.04: 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by cIdde on 2010-06-25
Same problem here on an Acer Travelmate notebook (Kubuntu 10.04, 64-bit).

But one thing: I don't have to cold boot (i. e. switch off). The system is fully running (except for the x-server) and I can reboot by pressing (ctrl-alt-del). Plus, I can log on to the machine over the network.

But then, how do I restart the x-server? sudo /etc/init.d/kdm restart doesn't change anything. /etc/init.d/x11-common restart doesn't work either.

How would one restart the X-server with the new startup sceme?

---

### Post by MrBayliss on 2010-06-29
Just thought i'd give you a heads up guys. I was having this problem and also it was hanging when booting.

I simply swapped my CD drive with another and it worked absolutely fine. That's what worked for me, not saying for anyone else.

---

### Post by spamless on 2010-07-04
> **MrBayliss said:**
> Just thought i'd give you a heads up guys. I was having this problem and also it was hanging when booting.

I simply swapped my CD drive with another and it worked absolutely fine. That's what worked for me, not saying for anyone else.

I have the message on a notebook running Lucid for notebooks, where no CD drive even exists and where I installed from USB stick.  I also have the error message on an old laptop on which I installed Lucid.  I do not have any trouble booting, though.  The message is there behind the splash screen -- both on bootup and on shutdown.

The old laptop has crashed a few times, mainly when doing video-intensive things.  It freezes.  But that could be video or memory problems, I don't know. I have no trouble with the newer notebook, but the warning is annoying.

---

### Post by sordid on 2010-07-07
Same here on a small barebone.
I'm pretty fed with Ubuntu - I love many things about it but had way more problems with it in a year than I ever had since Windows 3.1 - time to format and install XP instead.

---

### Post by mörgæs on 2010-07-07
> **sordid said:**
> Same here on a small barebone.
I'm pretty fed with Ubuntu - I love many things about it but had way more problems with it in a year than I ever had since Windows 3.1 - time to format and install XP instead.

When you write Ubuntu, do you mean 10.04 or other versions as well?

---

### Post by UbuntyInstallationBug on 2010-07-09
Gateway MX6025 also produces same bug when trying to install Ubuntu.
But the Linux Mint installs in Compatibility mode only.


> **cheinze5719 said:**
> Currently running 10.04. Just did some updates and when it finished rebooting it just doesn't work right. Whenever I click on my user name to enter my password it freezes for 3-5 seconds then the screen reloads. If I do Ctrl+Alt+F7 I get this error(the title of the thread). I have no earthly idea what this means but everything was working great until I did my updates just a couple hours ago.

Anyone know what's going on??

---

### Post by DieselSnorter on 2010-07-10
I'm getting this error, not on boot though.  Mine boots up fine, but when it goes to screensaver after I walk away for a while.  Not ALL the time, just every so often.  I come back, the screen is black with the error, and I have to reboot to get any response.  I recently upgraded to 10.4 from 9.10.  It was fine for the most part until yesterday when I saw this for the first time.

---

### Post by AvgOrdinaryGuy on 2010-07-10
I've also been getting this error during boot of the live CD, on an A31P Thinkpad.  The Ubuntu logo appears on the screen for a very long time then blanks as if X is starting, then a black screen with this error message.  Requires a cold boot to clear it.

Tried three different optical drives, a CD-ROM, a DVD and a CD-RW/DVD.  Same result with all three.

However, I was able to boot the same CD on my Dell 8250 desktop machine.

Wonder if the problem could have something to do with the Thinkpads ATI-7800 graphics chip.  My desktop has Nvidia MX420.

EDIT:  Just ran MEMTEST and found that I had a bad stick of RAM in the Thinkpad.  Replaced that, and now the 10.4 LiveCD boots fine.

---

### Post by mörgæs on 2010-07-11
For those who have been running 10.04 for a while but only encountered the error recently: 

If an update has been buggy, there is a chance that a fix is already in the making. Wait a few days, boot the machine and try the following:


```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by 10up on 2010-07-17
I've just encountered this error recently, although I updated to 10.04 from 9.10 2 months ago.  Same error as the headline.  It appears after the load screen starts and runs for a few seconds.

Afterwards I can avoid a hard shutdown by pressing ctrl+alt+delete which reboots.

Is there nothing on the radar as far as a fix goes yet?  I'm really sick of hanging out in my Windows partition...

---

### Post by eneveu on 2010-07-17
> **10up said:**
> I've just encountered this error recently, although I updated to 10.04 from 9.10 2 months ago.  Same error as the headline.  It appears after the load screen starts and runs for a few seconds.

Afterwards I can avoid a hard shutdown by pressing ctrl+alt+delete which reboots.

Is there nothing on the radar as far as a fix goes yet?  I'm really sick of hanging out in my Windows partition...

Weird. I just got this error too... Did a hard reboot first (using the power button), got the error again, used ctrl + alt + delete and it worked. Maybe it's related to some recent package update?  BTW, I'm using Kubuntu Lucid.

---

### Post by x-shaney-x on 2010-07-20
I'm getting this also.
On both my Lucid install and on a fresh Maverick testing install.

I tend to have to do <alt><ctrl><del> to reboot and try again but sometimes the boot process will continue after a few seconds.
Completely random, happens maybe 1 in 3 or 4 boots.

---

### Post by jeremie on 2010-07-21
This issue appeared on an otherwise perfectly working 10.04 after doing some updates (about 2-3 weeks worth of updates). Impossible to boot. The screen is stuck on the ubuntu progress window.

---

### Post by Ub28 on 2010-07-21
I get the same error message if I tap the keyboard when Ubuntu is booting.

Rarely, I have to press CTRL ALT DELETE because Ubuntu gets "stuck", but then it boots fine.  I have no idea why this can happen?

The number at the end (in brackets) is not zero, but it can be any number, consisting of 3 digits.

---

### Post by x-shaney-x on 2010-07-21
There are several bugs regarding this error on launchpad.
It has basically been dismissed by the devs (the reports I've seen at least) who say it's nothing to do with plymouth and a bug should be reported against the application causing the bug.

How anyone is supposed to work out which application is responsible I don't know.

All I do know is that if I remove the splash line from grub, I don't get the error.
Put it back and the error returns.

---

### Post by Ub28 on 2010-07-21
I have no idea what's causing this problem and it happens early in bootup - you hit a key on the keyboard.

Correction to my last post: the number in brackets at the end IS a zero, but the 3-digit number appears on the left BEFORE the error message.

---

### Post by thol4u on 2010-07-22
In the past 5 weeks I'm using lucid, GLib Warning message appeared 4 times in the past week. I guess its something to do with new install/update?! But error message never occurs during boot up. Caplock light blinks during this message and I had to reboot.

Also from day 1, I'm getting random freeze with garbled screen with white lines. Sometimes also during boot up.

---

### Post by x-shaney-x on 2010-07-22
Incidentally, I noticed this same error on a fresh Mandriva 2010 Spring GNOME install.
I'm not sure it's related to gnome but I didn't see the error at all after testing the KDE version for a week.
Maybe related to GDM? 

And like lucid, if I disable splash the error goes away.

---

### Post by thedanyes on 2010-07-23
I'm running 10.04 with KDE (Kubuntu) and I get this issue intermittently during boot.  When it happens I have to reset the machine and boot again.  Hardware info: Intel H55 Micro-ATX motherboard (don't remember the model number atm).  Core i5 650.  Intel HD Graphics (on CPU).  I believe I've also encountered this problem when running a discrete graphics card (nVidia 9800 GT) if that helps.  I'm running full-disk encryption on an Intel X25-M SSD.

Actually, a totally un-related question but I've been trying to figure out how to get the grub boot menu to come up.  I've tried holding shift, or ctrl, or pressing keys at various times both before and after entering my HDD password, but can't get it to come up.  Any advice?

---

### Post by Catharsis on 2010-07-23
This is just a generic error message; it's about as specific as "something is wrong on your system". It's also almost always completely harmless; I get this at boot too  and my system works perfectly.

This is why the devs have dismissed these bug reports; it's impossible to do anything with only this information provided (since it doesn't tell them anything), so they prioritize bugs that actually have usable debugging information provided (since there are MANY more open bugs than devs able to fix them).

So, in your quests to solve your failed boots, this warning message is irrelevant. If your system isn't booting, then it's not due to this error, and you need to do more digging (I suggest kern.log and Xorg.0.log).

Happy bug squashing.

---

### Post by Joe Awsome on 2010-07-23
I get the same error message on a stable beta lubuntu live cd (32 bit). It ussually happens at process 221.
```
(process:221) GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```
I also get the same error when booting linux mint 9 lxde (it usually happens at process 220, but i just had it happen at process 224 when running compatibility mode. All this is done on an old HP Pavillion N3390 laptop. I don't know what the problem is but i know it's not with the integrated graphics, maybe this is a kernel problem (it doesn't just happen to ubuntu, but I suppose it a part of the is that many distros are based on ubuntu, EG: Mint Linux).

---

### Post by Joe Awsome on 2010-07-23
got the same error with lubuntu at process 226 instead of 221. This happened after changing a stick of ram (inferion 128mb 100Mhz for 64mb 100Mhz).

---

### Post by andre.tadeu on 2010-07-26
My PC with the following specs:

Pentium 4 3.40 GHz
Asus P5VD1-X Rev 303
2GB RAM

does not boot anymore after updating the initramfs and it started to show the same message. How ti fix the initramfs now?
I cannot load the kernel, it just goes to the initramfs /bin/sh (ash shell). I cannot manipulate packages from this shell.

---

### Post by drewsus on 2010-07-26
Im curious, has anyone here installed BURG? (the sexy graphical version of Grub2?)

What makes me wonder is that I have read elsewhere that "***sudo update-grub***" might fix this problem and then it got me thinking that this started happening some time after installing BURG. 

Im just about to reboot so I will see if the above command did anything and it should be readily apparent since I get this error pretty much every time I boot.

**[edit/update]**
So, whether it has anything to do with BURG has yet to be seen, but I have just done 3 restarts and 3 shutdowns followed of course by 3 boot ups and have yet to encounter this error again, which, as stated above, happened pretty much every time before. 

Only time will tell if this is a fix. Get trying it open source slaves! *cracks whip*

source:
[Clicky]("http://us.generation-nt.com/answer/10-4-boot-problem-glib-warning-help-197907291.html")

---

### Post by x-shaney-x on 2010-07-27
Never had burg on this install so doesn't seem related.
In my case, all boot errors/problems seem to have been down to ureadahead (maverick), after removing the package I don't get this message on boot anymore.

However, it does sometimes appear when resuming from suspend though since there is also a serious kernal warning after resume also, it's probably related to that.

I think what devs in the bug reports have been saying is right, the message in itself isn't the problem, it is a symptom of some other error/bug.

---

### Post by andre.tadeu on 2010-07-27
This error message IS UNRELATED to the real problem.

I can't update-grub from INITRAMFS shell, because it doesn't have sudo, update-grub and even it can't access the disk.

---

### Post by drewsus on 2010-07-27
> **andre.tadeu said:**
> This error message IS UNRELATED to the real problem.

I can't update-grub from INITRAMFS shell, because it doesn't have sudo, update-grub and even it can't access the disk.

Caps...
Could it not be mused that YOUR problem is UNRELATED to OTHER people's problem? 
And thus, what I mentioned above could be completely RELEVANT to fixing some people's issues as it has seemingly fixed mine?
Do not bark down possible solutions, ESPECIALLY with an issue that is spouting an error message UNRELATED to the actual error.

Now...
I installed BURG again and got the GLib-WARNING again, but ran "sudo update-grub" and it went away again, with BURG still working.

---

### Post by Catharsis on 2010-07-27
> **andre.tadeu said:**
> My PC with the following specs:

Pentium 4 3.40 GHz
Asus P5VD1-X Rev 303
2GB RAM

does not boot anymore after updating the initramfs and it started to show the same message. How ti fix the initramfs now?
I cannot load the kernel, it just goes to the initramfs /bin/sh (ash shell). I cannot manipulate packages from this shell.

Hold down Shift while booting to get to Grub, select the Recovery kernel, and then choose "root" at the bottom.

---

### Post by wieman01 on 2010-07-27
Relax, guys.

---

### Post by andre.tadeu on 2010-07-27
I am sorry for the Caps Lock.

I am following the bugs at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) and I had the same problem three times. I often could boot in the previous kernel holding "Shift" when the Linux starts. That time I couldn't because I didn't update the Linux Kernel and GDM also.

This bug always happened to me when I updated the system, however that time I updated applications and initramfs (maybe initramfs-tools).

---

### Post by Hajex on 2010-08-04
I got the same stupid msg ...

even I couldn't use liveCD for 10.04 and 9.10 to backup .

I tried 8.04 liveCD and it's working but I can't access ex4 home folder to backup data :s. 

guys ..I want some way to retrieve my data .. this problem make me crazy .

notice :  when I check hardisk with liveCD it gave me a msg 'bad sectors ' *_* .

plz any link to help in backup

---

### Post by Catharsis on 2010-08-04
> **Hajex said:**
> I got the same stupid msg ...

even I couldn't use liveCD for 10.04 and 9.10 to backup .

I tried 8.04 liveCD and it's working but I can't access ex4 home folder to backup data :s. 

guys ..I want some way to retrieve my data .. this problem make me crazy .

notice :  when I check hardisk with liveCD it gave me a msg 'bad sectors ' *_* .

plz any link to help in backup

You could try a Maverick Daily build. I also hear that Linux Mint is more stable than Ubuntu.

Either way, as I said before, this message is irrelevant. The real problem is most likely some kind of graphics bug. You might be able to boot into Recovery Mode and then into failsafex.

---

### Post by Hajex on 2010-08-05
> **Catharsis said:**
>  You might be able to boot into Recovery Mode and then into failsafex.

I tired to boot in Recovery Mode but I get into cycle of msg that never stop .

---

### Post by jrev on 2010-08-06
I am on lubuntu 10.04 on a PC eeepc Asus 900 and I have this steady problem at boot on my hard disk 2 
It happens at every boot and I cannot enter the grub menu to boot on recovery and the command line.
I am stuck on the window to enter my username and password and can only do one thing : reboot or quit.
Apparently my user name or password are not  recognized 
I changed all possible alternatives in the BIOS to have a full boot, without success.

I will solve my problem in reinstalling a Debian Lenny.
Thanks for your attention ;)

---

### Post by Samulus on 2010-08-06
All of my friends see this error message when booting including me, but it's harmless for us and we just boot past it. It only appears for about 2-3 seconds while booting too. We're all on Linux Mint 9 too.

---

### Post by hawthornso23 on 2010-08-06
This is a quite harmless message during boot that is present on many (possibly even most) systems, but which is usually hidden by the plymouth splash screen. Hit escape to make the plymouth splash screen go away and you may see it on your system too.

When something goes wrong and the machine doesn't properly boot for ANY reason, it is likely that this message will then be seen, decieving people into thinking it is the cause of their problem.

---

### Post by inameiname on 2010-08-06
I've also been getting this from time to time as well. 

It happens every now and then on a boot up, and is easily solved by a hard reset of my laptop (holding the power button until it shuts off) and then powering it up again. 

Recently though, I've seen it more after I added the kernel-ppa and installed the latest 2.6.35-14 linux kernel. It now pops up for a second every time I put my laptop in suspend and then resume, (close and open the lid), right before it asked me to enter my password again.

Guess nobody has a fix yet for it, and since it's not a huge issue, I'll just wait for an update to fix it. Hopefully.

---

### Post by pooriak on 2010-08-06
I'm getting this also.
I have no external dvd rom so I have to install ubuntu via usb.
my netbook is Eee PC 1201.
This error happens when it wants to start installation.
I am confused.
What can i do with this problem?

---

### Post by jrev on 2010-08-06
Just ignore it if it doesn't prevent you to use your computer ;)
In my case It was a steady problem that prevented me to boot the computer or get the grub menu

---

### Post by pooriak on 2010-08-06
It is not a problem that prevent me to use my netbook.
but I want to install Ubuntu on it, because a lot of my works are with Ubuntu. I can't do a lot of works with windows.

---

### Post by Catharsis on 2010-08-06
hawthornso23 is absolutely right. This message is *always* present, it's just masked by plymouth or X. 

The only reason you're not seeing it anymore is because is because the system boots on VT1 and then switches to VT7 to start X on. So if Plymouth doesn't start fast enough, you see the error on VT1. And when you suspend, the system switches back to VT1 before it suspends, which is why you see it again.

If you don't believe me, just hit Ctrl+Alt+F1. This is VT1, and your error message is at the top. Get back to your regular session with Ctrl+Alt+F7.

It's completely harmless. Really, you don't need to worry about this error message.

---

### Post by x-shaney-x on 2010-08-06
I believe it is harmless but the fact it's showing it when it shouldn't be indicates a problem.

Plus, it isn't very comforting for a new user to see an obscure warning message on boot.

---

### Post by inameiname on 2010-08-06
Very true. I've already gotten complaints about it from those newbies who I've installed Ubuntu on their computers. It sounds scary, but I just tell them it's harmless, and they seem okay with that. Just a nuisance more than anything.

---

### Post by wieman01 on 2010-08-07
I can only scratch my head... this bug has been known for months now. What's wrong with these developers? Don't they listen?

This problem still occurs every other time I boot or so.

---

### Post by Catharsis on 2010-08-07
> **wieman01 said:**
> I can only scratch my head... this bug has been known for months now. What's wrong with these developers? Don't they listen?

This problem still occurs every other time I boot or so.

This "bug" doesn't do anything. Why would they waste their time fixing it when they could fix real bugs that actually affect usability.

---

### Post by x-shaney-x on 2010-08-07
Probably because to someone who doesn't understand, something with the word WARNING on boot indicates there is something wrong or there is a bug and people will keep reporting it as a bug until it stops showing.

---

### Post by wieman01 on 2010-08-07
> **Catharsis said:**
> This "bug" doesn't do anything. Why would they waste their time fixing it when they could fix real bugs that actually affect usability.
Mmm... It's a bug, it's annoying people, and confuses newcomers. Plus it wastes time. What's the point of accelerating Ubuntu's boot process only to end up booting twice or sometimes even three times in a row.

No, a bug is a bug and it needs fixing. From a consumer's standpoint such a thing is simply unacceptable.

---

### Post by Catharsis on 2010-08-07
> **wieman01 said:**
> Mmm... It's a bug, it's annoying people, and confuses newcomers. Plus it wastes time. What's the point of accelerating Ubuntu's boot process only to end up booting twice or sometimes even three times in a row.

No, a bug is a bug and it needs fixing. From a consumer's standpoint such a thing is simply unacceptable.

I'm just trying to answer your question. If you want to do something you can nominate the bug report as a papercut I guess. Just remember that commenting on a forum isn't going to get it fixed.

---

### Post by wieman01 on 2010-08-08
> **Catharsis said:**
> I'm just trying to answer your question. If you want to do something you can nominate the bug report as a papercut I guess. Just remember that commenting on a forum isn't going to get it fixed.
That is true. Like I said it's been reported for a long time now, was just trying to say I don't understand why it has not been fixed yet. I worry about the bug reporting & fixing process rather than this bug itself. Something greater seems to be at odds with the community.

By the way, some of the complaints in the forums get heard. Not all, but some.

---

### Post by Catharsis on 2010-08-08
> **wieman01 said:**
> That is true. Like I said it's been reported for a long time now, was just trying to say I don't understand why it has not been fixed yet. I worry about the bug reporting & fixing process rather than this bug itself. Something greater seems to be at odds with the community.

By the way, some of the complaints in the forums get heard. Not all, but some.

I do agree with you there. It does seem like the devs look at their bug list and choose which ones they feel like fixing and ignore the rest. Which is kind of sad, but a reality.

I know JFo from the kernel team is reorganizing Kernel Triage, so that's been really fun. You can subscribe to the kernel-team list or check out their wiki for more info if anyone's interested; I think there's a Kernel Triage Summit sometime in September too.

Now if we can just convince the X.Org team to buckle down like the Kernel team has....

---

### Post by wieman01 on 2010-08-09
> **Catharsis said:**
> Now if we can just convince the X.Org team to buckle down like the Kernel team has....
:-) Way to go if you ask me!

---

### Post by Jasper Houtman on 2010-08-11
Same error, only with Lucid btw. Previous install worked fine. Ran fine after first install, but gave me that error after installing updates.

Not sure if thats the same as the bug reported on the first page.
Because thats from people who had the problem with the live cd and after first install. Do i need to make a new report because it did not break for me until after updates?

Anyone found a fix for it yet? Been looking all over, cannot find anything.
May just have to switch distro cause it' s annoying the hell out of me.
Always had Ubuntu but not going to keep it if I have to reboot several times every time I want to use my computer.

---

### Post by manu27000 on 2010-08-11
When you get the error, just press ALT button and then CONTROL button a few times . ( Dont press both together )  .. You can bypass the error and complete installation ... 

hope this helps ..
the best friend

---

### Post by john newbuntu on 2010-08-11
EDIT: I thought I had a workaround.  But it wasn't one after all.

---

### Post by Copernicus1234 on 2010-08-11
I posted in this thread on May 1:st and filed a bug report and tried to find solutions. Found none.

I ended up switching over to another Linux distribution during May. No problems at all since then. This problem could have to do with Plymouth in Ubuntu. It seems likely.

And there is still no solution, and the bug reports seems to be marked Incomplete or Invalid, so I dont think the Ubuntu team will fix this... they dont know what the real problem is, because the error message is very generic.

---

### Post by Alan F on 2010-08-11
I see the warning message at almost every boot for about 2 secs before the desktop appears.

John Newbuntu's 'fix' just gives me longer to read it!!

---

### Post by john newbuntu on 2010-08-11
Thanks for the feedback Alan.  That proves that my guess is wrong and that the error is before gdm starts.  I'll edit my workaround and not waste other peoples time.

---

### Post by inameiname on 2010-08-12
I get the same thing as Alan F. In addiition, ever since I installed the kernel 2.6.35, I get it on resume of my laptop when I life up my lid, before it pops up a box asking me to enter my user password.

---

### Post by Epic720 on 2010-08-15
Happening to me on installation with 10.04, and it's not just a nuisance bug, I can't complete installation because of this bug!

My setup:

AMD Phenom II X4
8GB DDR3 1600
MSi 760GM (760G chipset)
WD Caviar Green 1TB 

--------------------------

I boot live DVD;
Choose "Install Ubuntu 10.04;
Choose timezone and keyboard map;
Choose "Erase and use the entire disk";
Fill out personal info;
Click install;

Sits at 5% of "Creating ext4 file system for / in partition #1 SCSI3 (0,0,0) (sda).." while cycling through the wait info.

Then to a black screen that displays the error. I can still see the mouse but nothing works.

I used this disk just a few weeks ago to install on a similar hardware configuration (AMD X2 and 8GB ram) and it has been runnning perfect ever since.

---

### Post by Hajex on 2010-08-16
Is there any solution for this problem ??????
if I install 9.10 Koala ...will this solve the problem ?

It's so stupid for system like ubuntu to fall in this trap :'( 

I can't even login any more ..what's the hell?

---

### Post by mörgæs on 2010-08-16
Yes, it is unlikely that 9.10 has this problem. Just remember having wired internet access while installing.

---

### Post by drewsus on 2010-08-16
I know the issue may be different for some, but I hope people try
```
sudo update-grub2
```
Because the issue never came back for me after I did that.

---

### Post by inameiname on 2010-08-16
Curious about your fix, I tried it, and sadly only got this after 'sudo apt-get update-grub2':

E: Invalid operation update-grub2

---

### Post by drewsus on 2010-08-16
> **inameiname said:**
> Curious about your fix, I tried it, and sadly only got this after 'sudo apt-get update-grub2':

E: Invalid operation update-grub2

Oops, I should not have had 'apt-get' in there

Do instead: 
```
sudo update-grub2
```

---

### Post by inameiname on 2010-08-17
Oh ok, thanks. I did that, and so I guess I'll now wait and see for any changes. Thanks again.

---

### Post by manu27000 on 2010-08-18
[SIZE="4"]**[COLOR="Red"]I am wondering, why people are not listening to the WORK AROUND I mentioned.[/COLOR]**[/SIZE]

I HAD THE SAME PROBLEM ... BUT I SUCCESSFULLY INSTALLED UBUNTU.

Just press ALT button and then CONTROL button a few times . ( Dont press both together ) .. You can bypass the error and complete installation ... 

This is what I did and successfully continued the Installation process.

---

### Post by Hajex on 2010-08-18
manu27000 : I did exactly what you said but nothing happen at all . 
This message refer to many problems not to the same one . So each problem has its own solution.

---

### Post by x-shaney-x on 2010-08-18
@ manu27000
This error/warning also appears on installed systems.

---

### Post by inameiname on 2010-08-18
So I tried:

```

sudo update-grub2

```...and I get the same message.

Oddly, in addition to this, after inputting it into the terminal, upon a restart, my icon set was stuck on the basic Ubuntu one, not my custom one I use. Weird, but another reset put it back to normal. 

Regardless, it didn't work, so oh well. It continues to pop up every time I restart/resume from suspended mode on my laptop.

---

### Post by mörgæs on 2010-08-18
In case you guys like experimenting, you could take 10.10 (alpha) for a test and see if the problems are solved. 

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

If it works: Congratulations. 
If it does not work: Best is to switch to 10.04 again (or try 9.10, which most likely is free from the bug). Please don't post questions here regarding 10.10! It is a version in development, and don't expect support like in the supported :-) versions. 

(However, if you are an experienced Ubuntu user and want to take part in systematic testing of 10.10, you are welcome).



EDIT 2010-9-26: 10.10 is now in beta, and though the problem is not solved, it seems that it happens less than in 10.04. 

Second to using 9.10, a clean install of 10.10 with ext3 is probably the best recommendation at the time being.

---

### Post by x-shaney-x on 2010-08-18
Problem with that is a lot of people (me included) also get the glib warnings on maverick.
To those who try it and DO get the warning, it may well be related to a different problem to what they are having on lucid, causing more frustration or confusion.

---

### Post by thepocketdrummer on 2010-08-19
I believe this problem may be related to the EXT4 file system. 

I attempted the install again, but this time I chose manual instead of automatic when I got to the partition manager. From there, select EXT3 instead of EXT4, configure the rest as usual, and try the install again.

I hit this issue nonstop, and this is the only thing that fixed it for me.

---

### Post by legolas_w on 2010-08-24
Hi,

When I try to sleep my laptop I see this error and the laptop does not go to sleep. :((
Every time I need to shut it down and start it over again. Does anyone has this issue with the sleep as well?

Thanks.

---

### Post by BigSilly on 2010-08-28
Just seen this error on the missus' Dell laptop. It's been fine for months with no problems at all, so colour me confused. Has there been a fix or anything sorted for this? The missus always blames me personally for Ubuntu errors...:D

---

### Post by asusx on 2010-08-28
I get the same error. It comes up before the Ubuntu boot screen... Even though i get this warning  I can still boot and my Ubuntu is completely usable.

Specs:
Ubuntu 10.04 installed from live USB flash drive.
Intel core 2 duo 2.26ghz CPU
Nvidia 9600M GS videcard
Ubuntu is installed on an ext4 partition.

---

### Post by James78 on 2010-08-29
I believe I've figured something out. This occurs with me everytime the EXT4-fs requires recovery, upon which restarting the computer works.

To get around this, when my EXT4-fs requires recovery, I go into recovery mode, drop to root, and touch /forcefsck, although technically the problem is probably fixed when starting up recovery mode, because fsck runs and fixes the disk, but ya.

---

### Post by BigSilly on 2010-08-30
Reading through the thread, it seems there's a bit of a disparity between what people are saying the error is doing, and what the Ubuntu community say it's doing. 

For my part when I get this error, I cannot boot into the system. I get the bootsplash, then the screen goes black. The error message then pops up on screen and I can do nothing else. Booting into the OS is out of the question because at this point there is no way to input anything into the system. It's stuck. Luckily a quick tap of the power button sends the machine into shutdown without any problems, and a restart is usually fine. Anyone can see this is not an ideal solution, and shouldn't be happening on any Ubuntu installation. 

If it was a brief error message before the GDM appears (as some forumites seem to think it is), then it wouldn't be so bad and you could ignore it. But as it is, it halts the boot process completely leaving a user with no option other than having to manually reboot.

---

### Post by 007casper on 2010-09-02
I cant do safe boot.  I hold down shift button, and try to boot on safe mode.  It is like the keyboard is not working. If I do ctrl+alt+delete, it does reboot.  So, I know keyboard works.  

How can I boot in safe mode?  I tried to boot from flash disk, no luck-

---

### Post by wieman01 on 2010-09-06
Mmm... Strange. Problem has not occurred in a week or so. Did install a couple of updates last week. Don't know if it's related, but have not had a problem since.

---

### Post by x-shaney-x on 2010-09-06
Something that has sprung to mind.
I had this same issue on both maverick and lucid.
On my maverick install I removed ureadahead due to a bug that stopped plymouth appearing.
In that time I don't remember seeing the message appear.
Once the bug was fixed I reinstalled ureadahead and I get it again.
Not every boot but every so many.
As someone else mentioned, it does seem to happen after disk checks so I'm wondering if the bug itself is in ureadahead.

---

### Post by inameiname on 2010-09-07
Good deduction. You might be right about that. Ureadahead might be the culprit. 

I think it has something to do with Plymouth. Nobody noticed this before Plymouth came to exist and be standard on Ubuntu. And as I'm sure many of you know, Plymouth is new to Ubuntu since Lucid and it has a lot of bugs that are still working themselves out.

---

### Post by ivanovnegro on 2010-09-08
> **asusx said:**
> I get the same error. It comes up before the Ubuntu boot screen... Even though i get this warning  I can still boot and my Ubuntu is completely usable.

Specs:
Ubuntu 10.04 installed from live USB flash drive.
Intel core 2 duo 2.26ghz CPU
Nvidia 9600M GS videcard
Ubuntu is installed on an ext4 partition.

I can admit the same, the error appears but my system is usable but for how long Im asking myself?
Im little disappointed about the more and more issues in Lucid or in Ubuntu in general.

---

### Post by mikodo on 2010-09-08
> **x-shaney-x said:**
> Something that has sprung to mind.
I had this same issue on both maverick and lucid.
On my maverick install I removed ureadahead due to a bug that stopped plymouth appearing.
In that time I don't remember seeing the message appear.
Once the bug was fixed I reinstalled ureadahead and I get it again.
Not every boot but every so many.
As someone else mentioned, it does seem to happen after disk checks so I'm wondering if the bug itself is in ureadahead.

I had this warning twice on Lucid, the second today, after a self disk check also, when I had booted up earlier in the day. Hmm.....

---

### Post by DrJohn999 on 2010-09-11
On ASUS M3N78-EM + 2G RAM, with or without the HDD and DVD attached, this occurs every time I boot from a USB drive created with Lucid / Startup Disk Creator or from similar CDs. Tried various 10.04.1 desktop flavors including i386, AMD-64, and NB-Remix. 

The system boots just fine with 10.10 Alternate AMD-64 beta on USB (w/out the persistent storage option) so I imagine this problem is largely solved with Maverick (wait and see...).

Original problem was the M3N78 failed to boot its installed system (10.04 desktop + Mythbuntu) a few days ago; the failure was not the topic error but rather a blank screen with blinking cursor and 100%-on HDD light. Attempting to boot from USB to diagnose the possible HDD failure resulted in the GLib warning. 

Anyway, now I can proceed to get this one running again. If necessary to reinstall I'll have to step up to the beta for the next 6 weeks or so, tho.

---

### Post by hapihakr on 2010-09-15
This bug does not just occur during boot. I've had this occur while uploading files to Wuala with both the desktop client and web app client (I believe both are java apps.). The full text of my error message is:

[INDENT](process:324): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)[/INDENT]

And this is most definitely NOT a harmless error. It interrupted my uploads. I had to hard reboot and restart my uploads.

Anyone have any ideas on what to do about this, if anything?

---

### Post by x-shaney-x on 2010-09-15
I've noticed it pops up on resume from suspend in maverick too.

---

### Post by kabanta on 2010-09-22
This error started to appear a few weeks ago for me on bootup of 64bit 10.04, but it didn't seem to have any impact on actually using my machine.

In the last couple of hours, however, my system has been crashing with the error being displayed. The first time it happened, I wasn't sure what caused it. However, I can now replicate it consistently by clicking on a url link in an OpenOffice spreadsheet. 

As part of discovering/testing this, I also crashed the system (with same error) once by invoking a keyboard shortcut I use for starting google chrome (this could have been a few things: the system was still completing startup and loading of desktop -- and I invoked the keyboard shortcut twice because I wasn't sure if it had registered).

Not sure if any of that helps narrow this down.

---

### Post by jameshampshire on 2010-09-24
Bumping for a fix.

---

### Post by mörgæs on 2010-09-24
> **jameshampshire said:**
> Bumping for a fix.

This will not bring a solution closer, just annoy people. Please read the thread, after that you will know that it is a complicated matter.

---

### Post by crazymao on 2010-09-25
so as far as i know there is no fix to this problem correct? i heard that for some people it occurs "sometimes" at boot up and that the REISUB method fixes it "sometimes" but for me neither is true. i cant boot into ubuntu at all. is there a short term solution? is there a way to revert the updates or something? please help me, thank you :(:(:(

---

### Post by x-shaney-x on 2010-09-26
There is no fix because nobody seems to know exactly what is causing these messages to appear and it may well be the case that different things are causing the message for different people.

Though since I have only had this problem on system using plymouth (not only ubuntu) I still say it is related to that or ureadahead.

---

### Post by inameiname on 2010-09-27
I agree, [x-shaney-x]("http://ubuntuforums.org/member.php?u=818879"). This issue seems to have started with Lucid, and seems to correlate very well with the addition of Plymouth to Ubuntu, which first came to be in Lucid.

---

### Post by Joe Awsome on 2010-10-02
would unistalling plymouth and replacing it with the old one fix the bug? I need this bug gone, cuz after a friends computer w/ XP died i installed ubuntu, but it has this bug. i don't feel safe sending them the computer back with the bug still in it. I might just install Debian on it and give it back.

---

### Post by x-shaney-x on 2010-10-02
Do you mean replacing it with an old version of plymouth?
I doubt it since the problem has been there with every plymouth version.
Plus, I don't think it's plymouth itself, rather a combination of various boot related processes.

If you mean replace it with the old usplash then I'm not sure if that would work.

---

### Post by ekips on 2010-10-03
fwiw, I was having this problem when trying to sleep my new Asus U35F with 10.10.  I am now able to sleep and wake my laptop thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822).

I do see the error just before the laptop actually sleeps, so it doesn't fix the issue per se... but it fixes my sleep issues :)

---

### Post by beestie on 2010-10-04
I get this error too.

I tried the 10.04.1 64-bit live CD and it worked fine on my ThinkPad T410 (which has been [approved as ready]("http://webapps.ubuntu.com/certification/hardware/200912-4905/") for 32-bit 10.04). I had intended to overwrite the CD-RW with the 32-bit version, I just wanted to try the 64-bit. After doing that, I got the error at boot.

So, thinking it was a 32-bit problem, I burned the 64-bit again, and now I get the error there as well.

Here it is exactly:

> (process:386): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

I find it bizarre that it would work the first time but not after re-burning. I'm going to burn the 32-bit again, since 64-bit isn't recommended for daily use anyway. If I get the error again then I'm going to have to find an alternative.

Incidentally, I tried the 9.10 live CD, which I already had laying around, but that didn't work either (which is why I downloaded 10.04). Or I should say, I know that it booted because I heard the Ubuntu theme music play, but I couldn't see anything. Just a shiny blank screen. :(

EDIT: With 32-bit, the error begins with process:409.

EDIT 2: Same error with **K**ubuntu 10.10rc, 32-bit. process:404

No *ubuntu for me?

---

### Post by mike4ubuntu on 2010-10-05
I got this same error when booting the LiveCD version of Lucid 10.04.1 64 bit.

>  (process:410): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

with my new MSI 785GTM-E45 Motherboard.  I used the same DVD drive as with other motherboards without any problems with Lucid 10.04.1.  Any work-arounds?

---

### Post by mörgæs on 2010-10-06
There are quite a few ideas in this thread. Have you tried any of them?

---

### Post by john's on 2010-10-06
Hi all. I don't normally add to this because I know so little. I have exactly the same issue only I don't think we are barking far enough down the tree...or BIOS maybe so forgive my madness but I feel its part of the same?

Has anyone took a look at their MBR lately? In the UK you may find your PC has an unknown MBR. I've had no success in resolving this issue, my lack of knowing and a lack of google info don't help I have looked and asked for some time now, two years or more! 

It is on all windows and linux machines (ALL FLAVOURS!) I've looked at, old PCs and new ones. 
It needs sorted because unknown MBR at 0 is not good I feel and I DON'T TRUST UK BB/GOV or windows but whys it on linux and in every flavour and is it just the in the UK?

Recently I've been involved helping fix a broken network with many windows pcs, all had the unknown MBR and they were all compromised, it will also say its an ms dos or a win 95 partition on linux but you try reading it or changing it and see what you get! 

The windows network guy said its just because? Unknown MBR not an issue, the Plum. 

A little paranoid, maybe, paranoid about the unknown? Definitely, living in the UK nanny state coz I know well just how sly that lot are!

Also feel free to point out if this is just dumb and why but if you know a fix please say, critics go easy my bite is worse than my bark ;)

I'm on mint 9 at the moment "its really good!" and yes it also has the Glib warning and it needs a 32bit win-part to install on but it still has the one meg unknown MBR at 0............please fix it :)

---

### Post by beestie on 2010-10-09
Why would that matter for booting the live CD, though?

---

### Post by cheway on 2010-10-09
Just to chip in, I see this issue on several of my OSs...

Ubuntu Lucid and Mint 9 on my main desktop (standard PC, nvidia card).
Mint 9, Lubuntu, and Ubuntu Netbook on my carPC (atom ion jobby)

Could it be nvidia related?

---

### Post by peertje888 on 2010-10-09
Just a moment ago I experienced this on my friend's pc; I tried to boot the system with a usb pen with 10.04 desktop. 

When I edited the boot command line (hitting e in the boot screen) and disabled quiet and splash option it ended up nagging about a fd0 while there is no Floppy drive in the system... Disabling this in the BIOS was the solution!

---

### Post by beestie on 2010-10-09
I'm writing this from the 10.10rc 64-bit live DVD, after trying both the 10.04 & 10.10 live CD in both 32- and 64-bit and getting this error with all four. This is the first live DVD I've tried, and like I said before, my first attempt with a CD worked until I overwrote it, so I'm wondering what would happen if I overwrote this with a different live DVD. At any rate, this is working as the first burn on this DVD+RW, so I recommend that people try the DVD if possible.

EDIT: I got the error when I suspended the machine, but it came out of suspend OK.

---

### Post by john's on 2010-10-10
peertje888

I have done the same as I don't have an fd0, funny it still wants to hoy 79 blocks of an uknown OS into the mix, calling its self A:! and I still have this unknown section in my MBR...BB? Al just pretend its not there an IT will just gan away. Plums 2 thier MBR @ 0SHITE is the botha man. Please prove this wrong and fix IT thanks. :lolflag:

---

### Post by wieman01 on 2010-10-21
I upgrades to 10.10 a few days ago, but the bug persists. I was hoping an upgrade would fix it...

---

### Post by ivanovnegro on 2010-10-21
> **wieman01 said:**
> I upgrades to 10.10 a few days ago, but the bug persists. I was hoping an upgrade would fix it...

Can confirm that.

---

### Post by inameiname on 2010-10-21
Oddly, ever since I installed Maverick on 10/10/10, I haven't noticed the issue.

FYI, I did a fresh install of Maverick. So maybe it's been solved. That or one of my PPAs and non-official repos fixed the issue, idk.

---

### Post by kooldino on 2010-10-21
I'm getting this on my Linux Mint 9 KDE box at startup, and then it freezes:

> (process:340): Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

---

### Post by ivanovnegro on 2010-10-22
> **kooldino said:**
> I'm getting this on my Linux Mint 9 KDE box at startup, and then it freezes:

I am using Mint 10 now (Gnome), its the same here with the message but without freezes.
I upgraded to 10 RC with the hope to fix it but nothing, maybe because it was an upgrade and not a fresh install.

---

### Post by x-shaney-x on 2010-10-22
Also still getting it here on a fresh kubuntu install.

---

### Post by BkkBonanza on 2010-10-22
After upgrading to Maveriack, I get this error msg about 50% of boots. It causes me to have to login twice - which is really annoying. I've searched thru log files and found no indications of what causes it. It's pretty annoying that every time I upgrade Ubuntu I get new broken functionality. They really should spend more time on stability and less on re-writing the OS every 6 months, because every 6 months my system breaks again.

---

### Post by mörgæs on 2010-10-22
So, in general (I know there are exceptions) it seems like a fresh install works better than an upgrade. 

If anyone has first tried an online upgrade to 10.10 and after that a clean install (on same hardware), please post your results.

---

### Post by wieman01 on 2010-10-22
> **mörgæs said:**
> So, in general (I know there are exceptions) it seems like a fresh install works better than an upgrade. 

If anyone has first tried an online upgrade to 10.10 and after that a clean install (on same hardware), please post your results.
I am not sure this is really true. You could create a poll and ask people to confirm that.

---

### Post by ibuclaw on 2010-10-22
We have a bi-yearly poll somewhere on these forums...

edit: [http://ubuntuforums.org/showthread.php?t=1595311](http://ubuntuforums.org/showthread.php?t=1595311)

---

### Post by wieman01 on 2010-10-22
> **ibuclaw said:**
> We have a bi-yearly poll somewhere on these forums...

edit: [http://ubuntuforums.org/showthread.php?t=1595311](http://ubuntuforums.org/showthread.php?t=1595311)
Thanks, mate. That's useful.

---

### Post by dhinuksha on 2010-10-28
well, I'm having the same error. but it's a fresh installation of Ubuntu Maverick 10.10 :(

---

### Post by Sven6210 on 2010-11-02
When booting my partners EeePC with a new installation of Ubuntu 10.10 desktop edition I had the same problem. I got the error message before I got the boot screen with the Ubuntu logo.

What I did:
Pressing CTRL + ALT + DEL and Ubuntu closed down and the netbook rebootet automatically. The result was the same error message at the same stage, nothing happened after that.

Then I switched the netbook off and removed the battery for 10 seconds. Then I restarted the netbook and it booted fully and without the error message.


This happened to me today and three days ago. Is there anything I can do?

---

### Post by catav on 2010-11-02
> **Sven6210 said:**
> When booting my partners EeePC with a new installation of Ubuntu 10.10 desktop edition I had the same problem. I got the error message before I got the boot screen with the Ubuntu logo.

What I did:
Pressing CTRL + ALT + DEL and Ubuntu closed down and the netbook rebootet automatically. The result was the same error message at the same stage, nothing happened after that.

Then I switched the netbook off and removed the battery for 10 seconds. Then I restarted the netbook and it booted fully and without the error message.


This happened to me today and three days ago. Is there anything I can do?
I have same error on my EeePC 1000HE. I installed UNR 10.10 as a fresh installation. Time to time error message come and PC freeze.

---

### Post by ivanovnegro on 2010-11-02
This issue definitely became too annoying for me.
Now I tried this for me, I changed my second OS Mint to Ubuntu 10.10, I made a fresh install and until now I did not experience the error. What happened, its gone now??? The rest here still have the same problem with fresh installs.
As I changed to Ubuntu now, Im pleased of Maverick in some ways but at the other side I dont know, there are too many bugs, now I experienced Flash problems, I know Flash is always a problem and it exists yet here in the forums a thread about this.
I need really a good suggestion or I have to change this user friendly OS to another one.
Ubuntu seems to be too buggy in a way, on the other side I like Ubuntu very much.

---

### Post by inameiname on 2010-11-02
I still haven't had the issue since I installed 10.10. It was a fresh install by the way when 10.10 was release a month ago. So for me, it's gone.

---

### Post by jimstar79 on 2010-11-04
i got the message last night, once. 

I was reading this thread and came across:

sudo upgrade grub2 

command.

I did this and have not seen the Glib-warning since. 

Maybe that did the trick?

PS: please correct the above command if it is wrong or simply could have nothing to do with the problem.

---

### Post by wieman01 on 2010-11-04
> **jimstar79 said:**
> i got the message last night, once. 

I was reading this thread and came across:

sudo upgrade grub2 

command.

I did this and have not seen the Glib-warning since. 

Maybe that did the trick?

PS: please correct the above command if it is wrong or simply could have nothing to do with the problem.
No, this won't fix your problem. Report back when the error occurs again, it won't be long. I have tried this too.

---

### Post by Iesos on 2010-11-08
Hi,

I have the same problem. Is there any solution yet? has it been deduced from where the problem comes?

Some say it is only during boot. Not true for me.
Some say it is only on live media. Not true for me.
Some say it is because of ext4. This could be true, for me.

Does anyone have this problem on ext3 or other fs?

---

### Post by heinkel_111 on 2010-11-08
I'm running 10.04 with KDE (Kubuntu) and I get this issue intermittently during boot. When it happens I have to reset the machine and boot again.

I have read some 9 pages of this thread and noticed that some users are able to "boot past it" and calls this harmless and not a bug. My experience is that the boot process stop and I am not able to move around it, got to do the power-off, power-on maneuver. 

If this is not a bug and not worthy of the attention of the developers (there are pages and pages of complaints about it here, on launchpad and elsewhere) then...our system is going out the windows? 

At some point, it starts becoming a serious alternative paying for someone to ignore your problems :confused:

---

### Post by Aslanded on 2010-11-09
I have been running Mint 9 for about 2 weeks, and in that time I had no problems at all. Once I tried to hibernate the system but it wouldnt come back to life (and this is what its always done for me on various pcs) so I didnt use it again, but everything else worked perfectly.  About a week or so later I've gone to boot up the laptop (HP Compaq 8510p) and it gives me:

fsck from util-linux-ng 2.17.2
/dev/sda5: clean, big number files, big number blocks

this fills the screen and flashes, then every so often a very quick flash of a blue square in the middle of the screen, but if it has a message its too fast to read.

So I tried to boot in the recovery mode and it said something about booting 37  times and checking disc before it hangs with the cursor blinking and no keys able to do anything.  So then I got the cd out that I installed the system off, and it doesnt work either! I get to the point where the dots for the logo start changing, then I get "stdin: error 0".  So I believe it was the forced checking of the hard drive (which always annoys me and never finds a problem) or it must have happened when the OS powered down unexpectedly because the laptop battery is no good and it died.  I have an ATI graphics card.  Is there any way changing a resolution setting in windows could have affected the boot into linux?

Looks like I'm stuck with XP for now..

---

### Post by mörgæs on 2010-11-10
Hi, welcome to the forum.

Your problem does not seem to be related to the getpwuid_r()-message, so it is best to open a new thread.

---

### Post by a-user on 2010-11-10
i also get this message during boot. but it always got past of it. it still bothered me much. i managed to get rid of that message by disabling plymouth (removed the splash option from kernel boot parameters).

edit: ubuntu 10.10 64 bit here

---

### Post by balikka on 2010-11-11
same problem...
running Ubuntu 10.10 64 bit on Sony Y-series laptop

edit:
using ext4
I'm going to try ext3 and some of the other releases but not before finishing my master's thesis in few days.

---

### Post by mörgæs on 2010-11-11
then same answer: 
Try a few of the latest Ubuntu releases (and especially both ext3 and 4) and tell us the results, then maybe someone has an idea. 

The statement 'it does not work' is not much of a foundation for helping you.

---

### Post by a-user on 2010-11-11
happens idependently of using ext3 or ext4.
in my case it seems to be related to either the battery checking message during boot up (which takes over 7 seconds to show "ok") or the start of gdm.

but i am not 100% sure

edit: i think this all happend after i installed the proprietary nvidia drivers with jockey, shortly after fresh install. but could be a coincidence.

---

### Post by Hippytaff on 2010-11-11
Just for completion I get this with Lubuntu on two seperate pc's 
 
Still works fine though:-)

---

### Post by snek on 2010-11-11
I am having this problem as well.
I only see it when my laptop has gone into suspend and I try to bring it back. The screen is black then with only this message. On few occasions the laptop will not show GDM to login again. 
[URL="http://www.pastey.net/142729"]
My lshw output on pastey[/URL]

---

### Post by Kaikias on 2010-11-11
I have the exact same problem as Snek.

> I only see it when my laptop has gone into suspend and I try to bring it back. 
> The screen is black then with only this message. 

This happened after I did a fresh install of Ubuntu 10.10 a couple of hours ago.

---

### Post by snek on 2010-11-12
Forgot to mention the following data:

Linux snek-laptop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Ubuntu 10.10 x86_64

Exta repositories:
```

-rw-r--r-- 1 root root  142 2010-10-28 22:08 chromium-daily-ppa-maverick.list
-rw-r--r-- 1 root root  142 2010-10-28 22:08 chromium-daily-ppa-maverick.list.save
-rw-r--r-- 1 root root   50 2010-10-28 22:08 dropbox.list
-rw-r--r-- 1 root root   50 2010-10-28 22:08 dropbox.list.save
-rw-r--r-- 1 root root  414 2010-10-28 22:08 opera.list
-rw-r--r-- 1 root root  414 2010-10-28 22:08 opera.list.save
-rw-r--r-- 1 root root  144 2010-10-28 22:08 sevenmachines-flash-maverick.list
-rw-r--r-- 1 root root  144 2010-10-28 22:08 sevenmachines-flash-maverick.list.save
-rw-r--r-- 1 root root  154 2010-10-28 22:08 ubuntu-mozilla-daily-ppa-maverick.list
-rw-r--r-- 1 root root  136 2010-10-28 22:08 ubuntu-wine-ppa-maverick.list
-rw-r--r-- 1 root root  136 2010-10-28 22:08 ubuntu-wine-ppa-maverick.list.save
-rw-r--r-- 1 root root  152 2010-10-28 22:08 ubuntu-x-swat-x-updates-maverick.list
-rw-r--r-- 1 root root  152 2010-10-28 22:08 ubuntu-x-swat-x-updates-maverick.list.save
-rw-r--r-- 1 root root  136 2010-10-28 22:08 xorg-edgers-ppa-maverick.list
-rw-r--r-- 1 root root  136 2010-10-28 22:08 xorg-edgers-ppa-maverick.list.save
-rw-r--r-- 1 root root   58 2010-10-28 22:08 zend.list
-rw-r--r-- 1 root root   58 2010-10-28 22:08 zend.list.save


```

---

### Post by nasp on 2010-11-14
I get the same issue on boot on fresh Ubuntu 10.10 64 bit Dell Latitude e4200

---

### Post by wieman01 on 2010-11-14
_**ISSUE RESOVLED?**_

It might be a conincidence, however, after I had manually upgraded to kernel 2.6.36-020636rc8 I have not experienced this problem it appears.

Keep you posted, but so far it's working fine.

---

### Post by namerg on 2010-11-14
[FONT=Arial][SIZE=2]I have a Dell Inspiron 580 which according to Ubuntu is a Certified Hardware[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Specifications:[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=2][FONT=Times New Roman][SIZE=2][FONT=Arial]Board: Dell Inc. 0C2KJT A00[/FONT][/SIZE]
[LEFT][SIZE=2][SIZE=2][SIZE=2][FONT=Arial]Bus Clock: 133 megahertz[/FONT][/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][/LEFT]
[SIZE=2][FONT=Arial]BIOS: Dell Inc. A06 07/06/2010[/FONT][/SIZE]
[LEFT][/SIZE][/SIZE][/FONT][/SIZE][/FONT][FONT=Times New Roman][SIZE=2][FONT=Times New Roman][SIZE=2][FONT=Arial]3.20 gigahertz Intel Core i3 550[/FONT][/SIZE][/FONT][/SIZE][/FONT][FONT=Times New Roman][SIZE=2][FONT=Times New Roman]
[SIZE=2][FONT=Arial]32 kilobyte primary memory cache[/FONT][/SIZE]
[SIZE=2][FONT=Arial]512 kilobyte secondary memory cache[/FONT][/SIZE]
[SIZE=2][FONT=Arial]4096 kilobyte tertiary memory cache[/FONT][/SIZE]
[SIZE=2][FONT=Arial]64-bit ready[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Multi-core (2 total)[/FONT][/SIZE][/LEFT]
[SIZE=2][FONT=Arial]Hyper-threaded (4 total)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]1 TB Hard Drive[/FONT][/SIZE]
[SIZE=2][FONT=Arial]4GB RAM[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]I have used x86 and AMD64 versions of Ubuntu 10.10 and still not booting at all neither the Live CD and there was a point that tried to go through it but then I saw the message:[/FONT][/SIZE]
[SIZE=2][FONT=Arial](process: 355): GLib-WARNING **: getpwwid_r(): failed due to unknown user id (0)[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]My main goal to get this computer is to set up iSCSI connectivity[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]Thanks for your help,[/FONT][/SIZE]
[SIZE=2][FONT=Arial]G[/FONT][/SIZE]
[SIZE=2][FONT=Arial]:([/FONT][/SIZE]
[/FONT][/SIZE][/FONT]

---

### Post by rplater on 2010-11-17
I get this same error when attempting to do a clean install. Can't even get Ubuntu 10.10 live running.

---

### Post by mörgæs on 2010-11-17
Good news:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917)

This fixes the (irrelevant) error message itself, so it will be easier to diagnose the real problem.


Please report how the system is behaving after applying the bug fix.

---

### Post by wieman01 on 2010-11-17
> **mörgæs said:**
> Good news:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917)

This fixes the (irrelevant) error message itself, so it will be easier to diagnose the real problem.


Please report how the system is behaving after applying the bug fix.
Would you be able to post step-by-step instructions here? The bug report is quite confusing and the solution is obvious to everyone.

---

### Post by inameiname on 2010-11-18
You shouldn't have to do anything. From that link this is what it said:

> 
                 This bug was fixed in the package plymouth - 0.8.2-2ubuntu5.1
 ---------------
plymouth (0.8.2-2ubuntu5.1) maverick-proposed; urgency=low
   * Generate a dummy NSS stack in the initrd to suppress a glib warning
    generated by the label control (LP: [#649917]("https://bugs.launchpad.net/bugs/649917")).
 -- Evan Broder <email address hidden>   Fri, 29 Oct 2010 06:39:20 -0700

        


Seems, just updating to the latest version of plymouth fixes things.

---

### Post by a-user on 2010-11-18
> **inameiname said:**
> 
Seems, just updating to the latest version of plymouth fixes things.
right. i got the fix with an update two days ago.

---

### Post by ivanovnegro on 2010-11-18
Sounds good.
At the end there is a solution, so, Im not having this problem on Maverick fresh install for a long time now. And I updated also my plymouth.

---

### Post by wieman01 on 2010-11-18
> **inameiname said:**
> You shouldn't have to do anything. From that link this is what it said:



Seems, just updating to the latest version of plymouth fixes things.
Cool, mate, thank you. Have not received this error for a while now. I am cautiously positive. :-)

---

### Post by inameiname on 2010-11-19
Yep. I'm glad they FINALLY fixed it. I mean I know it wasn't a huge issue for most folks, but it certainly has been a headache for some for a while now. So far so good for me. Though, I hadn't noticed it since installing Maverick, not just in the past few days, when the 'fix' to 'plymouth' was updated.

---

### Post by Wizard of Wiring on 2010-11-26
I am a long time Debian user finally getting around to installing Linux for something other than a server.  I decided to check out Ubuntu since it has been getting a lot of buzz.  First impressions are everything and I was looking forward to see what all of the buzz over the Ubuntu gui is about.  After spending a couple hours downloading the iso, I was finally ready to boot my fresh copy of the installation cd.

I popped the cd in with excitement.  After hanging on a splash screen with red/white dots for several minutes I received the error mentioned in this thread.  My eyes rolled thinking back to experiences with older versions of getting things to work in linux as I started Googling out the solution.

Turns out there is no solution.  This error message is simply masking the actual error message which means the problem could be any major piece of hardware:  dvd-rom, mainboard, video card, sound card, etc.  Maybe it could even be a bad cd burn.

The most ironic part of this thread is the fact that it was created months ago.  The "please be patient" posts are quite comical as if people have months to wait around for a solution.

This kind of flaky crap is THE REASON I use Debian because Debian is stable.  Once again the rule of thumb holds true... if it ain't in Debian, it ain't working right yet.

Time to put the Debian 5 cd in...

---

### Post by mörgæs on 2010-11-27
It is not clear whether you are asking for advice or just complaining. If advice is the matter:


The problem is that the regular ISO still has the error, though a bug fix is available.

You could install a minimal Ubuntu from this ISO
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

After that you boot the machine and install the full system with

```
sudo apt-get install ubuntu-desktop
```and finally

```
sudo apt-get clean
```having wired internet access throughout the process.

This way your system will be free from this bug from the beginning.


The method also works for other Buntus, for example you could run

```
sudo apt-get install lubuntu-desktop
``` for installing Lubuntu.



Edit 2011-2-21: 
10.04.2 is out now, which solves the problem for the 10.04 family:
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/) 

If you encounter the problem while installing 10.10, the method mentioned here is the way to go.

---

### Post by Wizard of Wiring on 2010-11-27
> **mörgæs said:**
> It is not clear whether you are asking for advice or just complaining. If advice is the matter:


The problem is that the regular ISO still has the error, though a bug fix is available.

You could install a minimal Ubuntu from this ISO
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

After that you boot the machine and install the full system with

```
sudo apt-get install ubuntu-desktop
```and finally

```
sudo apt-get clean
```having wired internet access throughout the process.


This way your system will be free from this bug from the beginning.

I was complaining.  Since I last posted I can state with 100% certainty the problem I experienced is related to a dvd-rom.  I was converting an existing older server running Debian into a desktop.  I downloaded Ubuntu yesterday and the Ubuntu iso for whatever reason would not boot.

The press alt then ctrl suggestion mentioned earlier in this thread did not work.  What did work was opening up the case and replacing the dvd-rom with a different dvd-rom.

Because I wanted to eliminate the possibility of a failing dvd-rom I wasn't aware of, I put the original dvd-rom back in the case and popped in a Debian 5 iso which installed just fine.  The dvd-rom in question also booted an Ultimate Boot CD iso.  Maybe there is some freak error going on with the dvd-rom in question where it decides to stop working with an Ubuntu iso in it.

Using a different dvd-rom I was able to install Ubuntu without further incident.  I did not have an ethernet cable plugged in during install and the update after a standard install is ~182mb... brutal.  Since I primarily use shell I can't comment on differences between a vanilla gnome gui and Ubuntu.  I will have to read up on the gui differences.

After installation the error is still present as other people have commented but it is an annoyance that does not affect anything.  During installation it was a show stopper which was the source of the complaint.  It's aggravating opening up a case to replace a working dvd-rom just to satisfy the Ubuntu installation iso.

---

### Post by Mudmanc4 on 2010-11-28
Well it's good to know this is being taken care of . The community is awesome  !!!!  

 I just wonder how they will handle the 50 disks I just bought last week for resale/ distribution lol

---

### Post by inTrouble on 2010-12-30
I am glad you all solved this problem. However, I have an older windows machine that quit on me and I tried to boot with an Ubuntu 10.10 Live CD. I did it before and had NO problems. Now I am getting this error message. So, is it software or hardware related? I think it's hardware related because I can't repair/ reinstall Windows and it won't let me boot Ubuntu with a Live CD. I get to the splash screen and then it craps out. Now what? Any ideas? :confused:

---

### Post by cjhowe on 2010-12-31
> **peertje888 said:**
> Just a moment ago I experienced this on my friend's pc; I tried to boot the system with a usb pen with 10.04 desktop. 

When I edited the boot command line (hitting e in the boot screen) and disabled quiet and splash option it ended up nagging about a fd0 while there is no Floppy drive in the system... Disabling this in the BIOS was the solution!

FWIW,

There are at least 3 separate problems being described in this thread.

1. Those with a fresh install - this is a blocking issue
2. Those with an existing install - just the error, not a blocking issue
3. Those with an existing install - this is a blocking issue.

The solution from peertje888 solves the first one.  Which as the problem I was having on a fresh Ubuntu 10.10 install.

---

### Post by bjnueva8623 on 2010-12-31
I've been dual booting 10.10(with Windows7) for about a month. Today is the first time I've encountered a serious problem. 

This morning, nothing functioned properly after clicking on a program. The computer seemed to be "frozen", although the mouse was working fine. 

I decided to reboot, but then encountered an even bigger problem. It failed to boot and got this message:

> **no init found. try passing init= bootarg**

I searched the forums and found a solution, I think. The problem now is that it requires a Live CD session and I keep getting this:

> **GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)**

In case it matters, I didn't install 10.10 from an ISO, I just upgraded from 10.04. Anyone know a solution?

---

### Post by mörgæs on 2011-01-01
> **inTrouble said:**
> I am glad you all solved this problem. However, I have an older windows machine that quit on me and I tried to boot with an Ubuntu 10.10 Live CD. I did it before and had NO problems. Now I am getting this error message. So, is it software or hardware related? I think it's hardware related because I can't repair/ reinstall Windows and it won't let me boot Ubuntu with a Live CD. I get to the splash screen and then it craps out. Now what? Any ideas? :confused:

As a first step, I would run memtest from the Ubuntu live CD menu (if you get this far). If memtest does not show errors, you could try to feed it a selection of live CD's, both Ubuntu and others, to narrow down the problem. 

If the machine supports booting from USB, this will also be good in diagnosing the error.

---

### Post by mörgæs on 2011-01-01
> **bjnueva8623 said:**
> I've been dual booting 10.10(with Windows7) for about a month. Today is the first time I've encountered a serious problem. 

This morning, nothing functioned properly after clicking on a program. The computer seemed to be "frozen", although the mouse was working fine. 

I decided to reboot, but then encountered an even bigger problem. It failed to boot and got this message:


I searched the forums and found a solution, I think. The problem now is that it requires a Live CD session and I keep getting this:



In case it matters, I didn't install 10.10 from an ISO, I just upgraded from 10.04. Anyone know a solution?


Can you solve the problem while booting from an older live CD, for example 9.10 or 10.04?

---

### Post by GrdLock02 on 2011-01-01
I didn't read through all 19 pages of this thread, but I just thought I'd add that I too have experienced this problem.

I've been playing with different distros to find what I like on my new netbook. I've seen this error on BRAND NEW installations of Ubuntu 10.10 x64 and x86, Lubuntu 10.10 x86, Mint 9 LXDE x86, and Mint 10 Gnome x86.

The error is there every time I boot my machine, but it doesn't seem to affect anything. Once the UI boots, everything runs just fine.

---

### Post by krishna sumanth on 2011-01-01
me too having same prob do you have any sol for it

---

### Post by mörgæs on 2011-01-01
Hi, welcome to the forum. 

If anyone should be able to help you, you need to provide as much information as you possibly can:

Which releases of Ubuntu have you tried? 
Are all updates applied?
Which hardware?
When does the error appear? 
What exactly is the problem, besides the message being shown?
And so on and so on... 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Writing a good question takes time! 



But first of all, please read at least the latest half of the thread. It is very likely that you will find useful information here.

---

### Post by mucho_maze on 2011-01-16
> **MrBayliss said:**
> Just thought i'd give you a heads up guys. I was having this problem and also it was hanging when booting.

I simply swapped my CD drive with another and it worked absolutely fine. That's what worked for me, not saying for anyone else.

The same here on Thinkpad t41 Ubuntu 10.04 32 bit. Switched from external USB drive to the internal drive and then it worked flawlessly...

Tried the USB boot first, but failed to boot...

---

### Post by fstephens on 2011-01-25
Just a tip that may help someone. I kept getting this error trying to install from different media, even though 10.10 ran as Live CD once without problem.

Owner bought 1GB RAM and installed it, so I tried again with an external USB DVD. After about 6 failed attempts to install Ubuntu, 10.10, 10.04, even 8.04 with different CD's, both factory and copies from ISO, I found that the new RAM was not fully seated! Installation would get to partitioning and hang.
No problem after seating RAM module properly.

Not sure if this was related to the initial error (as in this forum thread).

---

### Post by mörgæs on 2011-02-20
10.04.2 is released now, which solves the problem for the 10.04 family. 
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by llogg on 2011-02-25
I'm running Mint 10 on a Lenovo desktop and started seeing this message when awakening from a suspended session.  Resuming the session seems to be a lot slower than before, but it does reach the login screen and then runs normally.  If this was fixed with a plymouth upgrade in ubuntu, does anyone know if the mint version of plymouth contains the fix?
The current version of plymouth on my Mint system is 0.8.2-2-1mint8-ubuntu5.  The plymouth version that contained the fix was 0.8.2-2ubuntu5.1, which makes me think the Mint version is based on the "ubuntu5" and not the "ubuntu5.1" release and needs to be updated.  If there is no Mint-specific release that contains the fix, does anyone know if forcing an install of 0.8.2-2ubuntu5.1 would cause more harm than good?  Thanks in advance.

---

### Post by timbofield on 2011-03-13
How I fixed this. I got a ethernet cable and connected directly to my modem. I then booted in recovery mode, then selected the option to update packages. I'm no longer getting this error now.

---

### Post by mbembi on 2011-03-19
try,

$ sudo dpkg-reconfigure [plymouth]("https://bugs.launchpad.net/ubuntu/+source/plymouth")

when still problem from single mode try to upgrade with newest kernel generic (now is  2.6.32-30) and then reconfigure again your plymouth.

---

### Post by bouncinglime on 2011-03-21
Many thanks! I'd updated from 10.04 to 10.10 and got the error on the next boot. Reconfiguring plymouth seems to have fixed it. ^_^

---

### Post by flutte on 2011-04-13
Hi,

I started to get this error during the boot of an industry-PC from a  USB-stick, when I was fiddling with the reboot= command-line to the  kernel in Ubuntu 10.10.

It turned out, that the reboot= option actually affected the boot as  well for some reason. In my case, the PC reports "00:02.0 VGA compatible  controller: Intel Corporation 945GME Express Integrated Graphics  Controller (rev 03)" and "00:02.1 Display controller: Intel Corporation  Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller  (rev 03)".

For me, booting without any reboot= option worked, as did reboot=pci, but not reboot=bios.

/Fredrik Lundström
Sr Software Designer, Prevas AB

---

### Post by Spyderkid on 2011-04-13
I've had that problem in the past the only way I found to bypass it is use a Live USB instead.

If you can't use USB on your computer then your screwed :)

---

### Post by mörgæs on 2011-04-13
> **Spyderkid said:**
> 
If you can't use USB on your computer then your screwed :)

Please don't write this nonsense, even if it has a smiley in the end. There are **many** ways of solving the problem, as you can see in this thread.

---

### Post by black_cat on 2011-07-31
[SOLVED]
 That's warning show up because old version of* Unetbootin. *Use last version of *Unetbootin* if you want to install Ubuntu 10.10 or higher.

---

### Post by inameiname on 2011-08-02
> **black_cat said:**
> [SOLVED]
 That's warning show up because old version of* Unetbootin. *Use last version of *Unetbootin* if you want to install Ubuntu 10.10 or higher.

Glad you got it working, but its not solely because of Unetbootin. I wonder how that solved it for you, as I don't know why Unetbootin would affect boots. But hey, if that worked, awesome. ;) I've never had Unetbootin installed and had this problem in the past. Fortunately, it just fixed itself after updating to Natty. Haven't noticed it since.

---

