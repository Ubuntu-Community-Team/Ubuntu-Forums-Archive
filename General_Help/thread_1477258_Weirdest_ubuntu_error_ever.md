---
title: "Weirdest ubuntu error ever"
date: 2010-05-08
forum: General Help
---

### Post by denied on 2010-05-08
Im not sure how i should start this topic, but this is by far the most alienated error i've had since using linux for the first time back in 98. Its so weird that it will sound that im on drugs, but i've dealt with this issue a few times before but now its gone overboard.

To keep it a bit realistic lets go right into it. Is there some function of ubuntu that stops your screen after 7-30 seconds of not using the mouse or keyboard? Im talking version that go back 3 years ago up to today 10.04 that im using today? I've checked my power options, screensaver options (idle after 5 minutes with password check) and none of them have a setting of MAX 30 seconds.

To give you and example: get a stopwatch out (or a clock) for how long does this :lolflag: wave at you? If i stop typing now (since i see it on the right of this reply box) it takes me 10 seconds for it to stop (second time it takes 26 seconds, third time it takes 14 seconds, fourth time 27 seconds, fifth time 6 seconds). Where am i going? Well this is the same with a download eg. downloading the image of ubuntu on aprox 650mb. With my 10/10 line i avarage about 1100kb/sec, so what happens after 26 seconds, 14 seconds, 10 second, 27 seconds, the same as it happens with the waving lol smiley. The download "halts", going from 1100k down to (it always differs) 20-1kb/sec. Normally if i go out for a smoke (5-7 minutes) i can just forget about the download since it would be all dead stuck on some low kb and not even resume downloading.

Before i could keep the connection "alive" by having some torrent client ownloading/seeding some files but that just doesnt do it today. Btw the clock also halts, its like the whole screen stops and all the activity on the computer except the fan that i can still hear. This is getting seriously annoying since i've been experiencing this for a while now but its only now in 10.04 i can notice this difference that a torrent client wont help. What stuns me even more is the cycle between the "halts". It differs all from 6-7 seconds up to 30 (even sometimes over a minute).

I know urge you for help, im not novice in linux but im no expert either, i know what you will first say. Its a 64bit system (but please dont move it to that forum since its the same for 32bit system, it has nothing to do with this if u ask me). The second part:

```
@DOMiNi:~$ uname -a
Linux DOMiNi 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

```
@DOMiNi:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76XT [Mobility Radeon HD 2600 XT]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
08:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
08:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
09:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

```

Those are the starters i think for now, what more is needed to once and for all sort this issue out? I hope someone will take the time and dig into this since this is seriously harming my total switch from windows to linux and its a big step for me since i work with graphics and motion video.

Thank you all and have a good weekend. (now it stopped again just 2 seconds after i pressed space...my god!)

---

### Post by Seal Daemon on 2010-05-08
Can you please attach the log files ?

---

### Post by denied on 2010-05-08
> **Seal Daemon said:**
> Can you please attach the log files ?

the syslog or what log files are you talking about ? dmesg ?

Here is the pastebin link to **dmesg** [http://pastebin.com/jzcyL00y](http://pastebin.com/jzcyL00y)


EDIT2:
I've uploaded the video of my error to youtube so you can check it out more visual what im talking about.
[http://www.youtube.com/watch?v=of9XGx4Vk-Q](http://www.youtube.com/watch?v=of9XGx4Vk-Q)

---

### Post by Ordes on 2010-05-08
Does it just freeze and comes back again. Or you have to boot up your sys again.

I have seen this behaviour couple of times. But not on a ubuntu machine. The reason was always overheat, and a halt enforced by the mobo. 

Do you use a desktop, and placed it inside a closed PC_table. Which is one of the worst things as the heat cannot disappear easily. Take it out and see if there is a change.
To test if overheating is the reason or not, you can also try to put a big fan beside your PC. And see if there are any changes in the behaviour.

---

### Post by mscout2004 on 2010-05-08
poll your temp sensor on your CPU and Graphics Card to see if they register hotter then normal

---

### Post by denied on 2010-05-09
> **Ordes said:**
> Does it just freeze and comes back again. Or you have to boot up your sys again.

I have seen this behaviour couple of times. But not on a ubuntu machine. The reason was always overheat, and a halt enforced by the mobo. 

Do you use a desktop, and placed it inside a closed PC_table. Which is one of the worst things as the heat cannot disappear easily. Take it out and see if there is a change.
To test if overheating is the reason or not, you can also try to put a big fan beside your PC. And see if there are any changes in the behaviour.

No as soon as i move my mouse or type something on my keyboard everything works fine. As long as i keep doing this the computer will work without any error. As soon as i dont use the mouse or keyboard (given 5-30 seconds) the screen and/or system will "stop" and wont do anything in the background until i move my mouse/keyboard again.

It doesnt actually halt, it just stops doing things like download, installing (from apt-get to software center) and so on.

About the over heating, im almost 98% sure its not that since its a laptop (i cleaned the fans not to long ago) and under the laptop i have 2 extra fans that cool the system down. More to say this is not somethings that happens just after using the computer for 10-48h, this happens ALL the time, just after boot if i dont use the mouse/keyboard. Thats why its so god damn weird, its like if im not activly using the computer, it wont do anything.

---

### Post by Ordes on 2010-05-09
ah ok.. ,misunderstood u the first time..

basiclly as soon as you are not active with your pc, every other task / background task (copying, downloading, etc) stops too..

yeah.. this has nothing to do with over-heating..

however.. its the first time i hear about such odd behaviour.. 

which laptop u using? perhaps its a driver, etc conflict..?

---

### Post by denied on 2010-05-09
> **Ordes said:**
> ah ok.. ,misunderstood u the first time..

basiclly as soon as you are not active with your pc, every other task / background task (copying, downloading, etc) stops too..

yeah.. this has nothing to do with over-heating..

however.. its the first time i hear about such odd behaviour.. 

which laptop u using? perhaps its a driver, etc conflict..?

Yeps now you got me right =) Did you see the video i put on youtube, its a bit more visual than just text =)

I've had this behaviour for a while now to be honest, but before i was able to "remove it" by having some torrent activity (at least for the network part not to disconnect/go down to 2kb/sec) but now that doesnt even work.

Im using Fujitsu Siemens Amilo Xi 2550 its a really nice laptop but running in linux it just not working as it should. Im not at home atm but will be in 8h when i end work incase you want some stats check out their webpage. I've been trying to translate from german and russian sites about ppl installing ubuntu on this laptop but i havent seen anyone with the same issue as me. What worries me is mostly not the issue, its the time framing when it happens. Like sometimes it takes it 6 seconds to "freez" sometimes it takes it 28 seconds, and sometimes it might even go over a minute before it starts acting weird. And this is just right after a startup. And i cant see any errors in my logs to show me what this damned alienated stuff is.

While running windows i dont have any issues at all, so you might be right about the driver issue, im just not sure what or where =) ?

---

### Post by ibuclaw on 2010-05-09
/var/log/messages is a better place to get computer logs from.

And I'm noting you are using the ATi fglrx driver. I've never used an ATi ard before with Linux, but just curious, is there any choice of drivers you can have in the Hardware Drivers menu?

(edit):
Can you also pastebin /var/log/Xorg.0.log
and have a look at this bug report to see if the workaround helps the issue for you:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

Regards

---

### Post by uweklosa on 2010-05-09
This reminds me of a very old problem with /dev/random and /dev/urandom. If one did not type or move the mouse there was not enough entropy and some software stopped working. Several years ago I had a web server with this problem. The solution was to replace /dev/random with /dev/urandom. 
Might be something like that.

Uwe

---

### Post by denied on 2010-05-09
> **ibuclaw said:**
> /var/log/messages is a better place to get computer logs from.

And I'm noting you are using the ATi fglrx driver. I've never used an ATi ard before with Linux, but just curious, is there any choice of drivers you can have in the Hardware Drivers menu?

(edit):
Can you also pastebin /var/log/Xorg.0.log
and have a look at this bug report to see if the workaround helps the issue for you:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

Regards

Thanks for replying ibuclaw, im not sure if there is any other driver in there. I know that im using the properitairy driver (or how you spell it =) to run compiz a bit slow but functional. So there is at least one more driver i can try if i remove the fglrx but i dont remember what it was. I will let you know when i do this when i get home.

The launchpad report you are directing me to is actually affecing me as well. In one hit you hopefully managed to remove two of my issues =) I have been looking to sort that error out as well but never found that link you just gave me! Amazing stuff! I hope all this will work! 

> **uweklosa said:**
> This reminds me of a very old problem with /dev/random and /dev/urandom. If one did not type or move the mouse there was not enough entropy and some software stopped working. Several years ago I had a web server with this problem. The solution was to replace /dev/random with /dev/urandom. 
Might be something like that.


Uwe you are also giving me great hope for my return home and try this. It sure sounds like the same error i have, though you say some software, but in my case its all software =) Still there is hope and im eagerly running home today to try all your advices out. If i can fix this i can focus on the essentials...finaly! But lets not get to happy already =)

Cheers to you both and i'll get back to this post as soon as i get home :popcorn:

---

### Post by xinix on 2010-05-09
For what it's worth. I had a similar problem once due to a failing video card.  It drove me crazy initially I was convinced that it was the proprietary drivers that were causing this.  Later it turned out that the card had gone bad and could only handle 2d stuff.  As soon as I enabled 3d acceleration I got symptoms that were similar to the ones you described.

---

### Post by ibuclaw on 2010-05-09
> **denied said:**
> Thanks for replying ibuclaw, im not sure if there is any other driver in there. I know that im using the properitairy driver (or how you spell it =) to run compiz a bit slow but functional. So there is at least one more driver i can try if i remove the fglrx but i dont remember what it was. I will let you know when i do this when i get home.

The launchpad report you are directing me to is actually affecing me as well. In one hit you hopefully managed to remove two of my issues =) I have been looking to sort that error out as well but never found that link you just gave me! Amazing stuff! I hope all this will work! 

The 2D driver is 'radeonhd' - you can set this in /etc/X11/xorg.conf (it should exist).

> **denied said:**
> 
Uwe you are also giving me great hope for my return home and try this. It sure sounds like the same error i have, though you say some software, but in my case its all software =) Still there is hope and im eagerly running home today to try all your advices out. If i can fix this i can focus on the essentials...finaly! But lets not get to happy already =)

Cheers to you both and i'll get back to this post as soon as i get home :popcorn:

I seriously doubt lack of entropy has anything to do with your graphics card issue. :)
If you were having issues with Seahorse taking somewhere between 30 seconds, to 30 minutes to generate a 4096 bit DSA key pair though...

---

### Post by Sandertje on 2010-05-09
Just a suggestion, but you could try to boot to a terminal (CTRL-ALT-F1), and then get some random large file with apt-get or wget. If your system clogs up even then you can be pretty sure it doesnt have much to do with the ATI driver. If it doesnt clog, voila, it's probably something graphics-related ;-).

---

### Post by maury on 2010-05-09
You might try this. Run the system using some Live CD's. If all run well you can be reasonably sure the problem is not hardware related. Then run from the CD of the version that is giving the problem ans see what happens. You can maybe zero in on the problem. good luck.

---

### Post by denied on 2010-05-09
Okey its gonna be a few edits, here we go first:

Removed the fglrx driver to run on the default one from the installation (forgot how to check which one =) removed all visual effects, rebooted and still same problem. Now im going to reinstall the fglrx drivers and apply the ppa posted in here to see if that has something to do with this.

**Sandertje**: everything "gets stuck" my friend, this was actually what annoyed me most, i wanted to install the game Urban Terror (think its 650mb) and it got stuck in apt-get, downloading and installing, if i would go out for a smoke (5 mins). So like i said before, it doesnt matter what i do, if i do NOT use the computer it will get stuck in whatever its doing.

EDIT2: Okey we have success and i think we can narrow this issue down a bit. Re-applied the fglrx driver (from the hardware drivers) tried it out with no visual effects and still the same. Then i went to the url you gave me **ibuclaw** and installed Alf Gaida's PPM and believe it or not. I can now not use the computer for over 1 minute!!! This has NEVER happened before. I did two runs on my LOL smile and both went over 1 minute of not using the computer before it hangs. First run was 1.18 and second was 1.48, for me this is a HUGE progress since last time it could be all between 6-30 seconds for a sure "hang".

So i reckon we can narrow this down to a GFX card/driver issue? It also fixed the minimize/unminimize lag that ppl where talking about there and that i've had a taste for myself as well. Im really glad i brought this up, even though its not perfect, this means we are going somewhere and apparently Alf made something that kinda fixed my issue.

EDIT3: here is my Xorg.0.log: [http://pastebin.com/37AvqLrZ](http://pastebin.com/37AvqLrZ)

---

### Post by ibuclaw on 2010-05-09
> **denied said:**
> 
EDIT2: Okey we have success and i think we can narrow this issue down a bit. Re-applied the fglrx driver (from the hardware drivers) tried it out with no visual effects and still the same. Then i went to the url you gave me **ibuclaw** and installed Alf Gaida's PPM and believe it or not. I can now not use the computer for over 1 minute!!! This has NEVER happened before. I did two runs on my LOL smile and both went over 1 minute of not using the computer before it hangs. First run was 1.18 and second was 1.48, for me this is a HUGE progress since last time it could be all between 6-30 seconds for a sure "hang".

So i reckon we can narrow this down to a GFX card/driver issue? It also fixed the minimize/unminimize lag that ppl where talking about there and that i've had a taste for myself as well. Im really glad i brought this up, even though its not perfect, this means we are going somewhere and apparently Alf made something that kinda fixed my issue.


From the success you've had by installing a patched Xserver, your problem is most likely somewhere middle-ground between Xorg and the fglrx driver, and the way they communicate to each other.


There nothing of interest I can see in the Xorg.log file, which more than likely means X isn't seeing any errors / thinks everything running fine.


Whilst I'm happy that you have found some sort of resolution, I think this is probably as much as I can do to help you here. What you can do to progress forwards with this issue is to raise a bug:
```
ubuntu-bug fglrx-installer
```
Explaining your issue in detail, and what you have done that has  helped.


Regards
Iain

I think I'll be testing that package you installed too on my system (using an intel gfx driver). And help the patch get pushed along into the main repositories. :)

---

### Post by denied on 2010-05-09
> **ibuclaw said:**
> 
Whilst I'm happy that you have found some sort of resolution, I think this is probably as much as I can do to help you here. What you can do to progress forwards with this issue is to raise a bug:
Explaining your issue in detail, and what you have done that has  helped.

I think I'll be testing that package you installed too on my system (using an intel gfx driver). And help the patch get pushed along into the main repositories. :)

Iain, you cant imagine the feeling i have right now =) Im so happy linux is running as smooth as it did back in the days on my old computers. Its a relive of pain having to always having the same errors and slow computing issues on this lappy whiles windows is having almost zero issues. I really love linux but this damned forsaken issue has put me down to completely change over to linux or rather ubuntu. While im still not 100% sorted out im thinking of making the change for sure now. I've never experienced ubuntu as fast as im doing now and its a sure pleasure i must say.

I hope u can pull it trough to put this into the main repo cuz im sure there is a lot of ppl out there confused about their ati and the problem it might be causing. For the ease of everyone it should be there since i still havent read anyone that has experienced something bad out of that PPM =)

Thanks again for your help and support!
/Martin

I'll be sure to forward my issue to the bug reporting you directed me to.

---

### Post by lunatico on 2010-05-09
denied,

While it is amazing that you have done good progress with Alf's PPA, there is still one thing that concerns me, you mentioned that your "fix" used to be to keep your network connection doing something.
Was this a wireless connections? Are you using super strong encryption? Have you tried turning your network connection completely off and testing to see if it hangs then?
It's just a suggestion.

I'm also using Alf's PPA, and by slow window effect where fixed, but I'm still annoyed at the amount of RAM my xorg process uses.

Best of luck and please don't give up on linux!

---

### Post by denied on 2010-05-09
lunatico, i used to "fix" this issue before by having a wine installation of uTorrent running a few torrents (seeding and downloading) so that the internet (i think it was the whole system though) would not shut down on me. This was keeping it all "alive" but now (or actually recently i think since last ubuntu release) this hasnt worked.

I have no wireless connection and its all done on ethernet. I havent actually tried turning the network off, there is something in your words there. Im actually going to try it now to see if it has any effects. Though i still think i need to try the PPM a bit further to see how long the times are between the hangups. I've only done two tests so far with internet enabled. But i'll give it a try now.

Iain, here is my bugreport if its needed for further investigation:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/577962](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/577962)

EDIT: i wont lose hope in linux any time soon, i know it takes some "hacking" to get it right where u want it and i've converted my 50 year old mom to use linux on her lappy instead of windows, so i can see linux going a far way in the future. Im not a skilled user, but i know how to setup pretty good systems for the average users =) While i had my last year in India i converted 4 ppl to switch totally to ubuntu, and i was still running windows due to my profession (graphics artist and visual jockey) still they went on the train and today they are very happy with ubuntu =)



EDIT: The test now is at all VERY amazing! so i've had the first two test, 1.18 was it ? and 1.48, so i ran the tests again, i havent rebooted the system yet, so lets call it third test, the smiley lol animation stopped animating after 58 seconds, fourth test after 1.27 minutes, and the fifth test.....ran over 3 minutes then i went bored =) So im not sure if its worth doing this test without the network. Its a bit late here and im a bit lazy to do them over again =) Maybe tomorrow if u still think the network might affect my issue after this edit. Let me know in that case and i run it for you.

I must say im loving this PPM more and more =)

---

### Post by lunatico on 2010-05-09
> **denied said:**
> I have no wireless connection and its all done on ethernet. I havent actually tried turning the network off, there is something in your words there.[/url]

I'm just saying... you need to rule every option out. Let us know how it goes.

---

### Post by denied on 2010-05-09
> **lunatico said:**
> I'm just saying... you need to rule every option out. Let us know how it goes.

Okey for the sake of it i'll do them =) So how do you want me to do them?
sudo eth0 down or just remove the ethernet cable ?

---

### Post by lunatico on 2010-05-09
> **denied said:**
> Okey for the sake of it i'll do them =) So how do you want me to do them?
sudo eth0 down or just remove the ethernet cable ?

easy way, just remove the cable.

---

### Post by denied on 2010-05-09
Wow this is really stunning!

Here we go, 5 tests where made with no network cable plugged here are the timings:

0.35 minutes, 1.24 min, 1.26 min, 0.34 min, 0.35 min

Stunningly it shows that its less time of "not using" the computer when its not connected to the internet. Wow man why is this!? is it some kind of wake on lan or what that function was. Im really confused now, since im NOT downloading anything, all i have open is firefox, Ailurus (dont think that would matter) and a terminal. Man this is worth to further investigate in a proper manner.

Im stunned....

---

### Post by lunatico on 2010-05-09
> **denied said:**
> Wow this is really stunning!
Oh God...

> **denied said:**
> 
Stunningly it shows that its less time of "not using" the computer when its not connected to the internet.

So you mean it's worst if you're not connected? If you're not connected it takes less time to lock up?

At least we know that the network has something to do... some how...

---

### Post by lunatico on 2010-05-09
and if you run a live cd and don't connect to the internet?

---

### Post by denied on 2010-05-09
> **lunatico said:**
> 
So you mean it's worst if you're not connected? If you're not connected it takes less time to lock up?

At least we know that the network has something to do... some how...

Well i can almost say 95% for sure it has something to do with the network as well. It feels like if its receiving some signals of the net it will work better and "not hang" for longer time.

Im having a few hours off work tomorrow, if i get up early i'll do some serious testing, at least 10 of them with and without network to see what this all is about. Its strange if its like this, im getting more confused by the hour now =)

But yes, what you are saying atm is true.

---

### Post by denied on 2010-05-09
> **lunatico said:**
> and if you run a live cd and don't connect to the internet?

I'll have to test that as well tomorrow as its soon bed time for me. Im almost excited to test all this as im very dull it has a big difference if network or no network in there...

---

### Post by XtofR on 2010-05-30
Hi,

Any progress on this issue?
I have the exact same problem an behaviour here on my Fujitsu Siemens AMILO Xi 2550.

I'm running ubuntu karmic 32bit still though, so I can confirm that the problem exists even there.
Also I can't install the ppa patch mentioned before since it is for lucid only.

Any help on this issue would be greatly appreciated.

---

### Post by ibuclaw on 2010-05-30
I wonder if changing powerstates may invoke behaviours against the bug.

```
/usr/lib/fglrx/bin/aticonfig --list-powerstates
```
Will list all powerstates for your card
```
/usr/lib/fglrx/bin/aticonfig --set-powerstate=1
```
Will set it.

1 = Battery Friendly Powerstate, so you may want to try switching it to it's highest value.

Regards

---

### Post by XtofR on 2010-05-30
Hi,

I seem to not have the aticonfig in as you wrote:
/usr/lib/fglrx/bin/aticonfig

In /usr/lib/fglrx/ is only:
-rw-r--r--   1 root root  34488 2010-05-06 23:35 libdri.so.xlibmesa
-rw-r--r--   1 root root 403800 2009-10-14 00:08 libGL.so.1.2.xlibmesa
-rw-r--r--   1 root root 338512 2010-05-06 23:35 libglx.so.xlibmesa

And actually my aticonfig is located in:
/usr/bin/aticonfig

Also my version of aticonfig does not support the list-powerstates or set-powerstate options:
aticonfig: unrecognized option '--list-powerstates'
aticonfig: parsing the command-line failed.

However there IS a reference to the "set-powerstate" command under miscellaneous options which is kind of weird I think:
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.

I installed the proprietary drivers via ubuntu Administration/Hardware drivers dialog.
Below are the packages and versions I'm using on my system.
Please note I'm running karmic still as mentioned in previous post.
Could there be a problem of missmatching packages here? Or are you refering to lucid packages?

xorg-driver-fglrx        2:8.660-0ubuntu4
fglrx-amdcccle            2:8.660-0ubuntu4
fglrx-modaliases        2:8.660-0ubuntu4
xserver-xorg-video-radeon    1:6.12.99+git20090929.7968e1fb-0ubuntu1

---

### Post by ibuclaw on 2010-05-30
> **XtofR said:**
> Hi,

I seem to not have the aticonfig in as you wrote:
/usr/lib/fglrx/bin/aticonfig

In /usr/lib/fglrx/ is only:
-rw-r--r--   1 root root  34488 2010-05-06 23:35 libdri.so.xlibmesa
-rw-r--r--   1 root root 403800 2009-10-14 00:08 libGL.so.1.2.xlibmesa
-rw-r--r--   1 root root 338512 2010-05-06 23:35 libglx.so.xlibmesa

And actually my aticonfig is located in:
/usr/bin/aticonfig


Oh, so you are not running lucid then?


> **XtofR said:**
> 
Also my version of aticonfig does not support the list-powerstates or set-powerstate options:
aticonfig: unrecognized option '--list-powerstates'
aticonfig: parsing the command-line failed.


I have never ran the application myself (I don't even own an ATi card) - I was just quoting off [http://wiki.cchtml.com/index.php/Configuring#Changes_taking_effect_immediately](http://wiki.cchtml.com/index.php/Configuring#Changes_taking_effect_immediately)

You could try this instead (is said to work also).
```
aticonfig --lsp
```

Regards

---

### Post by cryptotheslow on 2010-05-30
Just throwing in a thought that came into mind reading through this and watching that YouTube vid.

Could it be a problem to do with the processor rate being scaled down when "idle"? Maybe rather than stepping down to say half-speed, for some reason it is incorrectly scaling down to or very close to zero?

Maybe worth adding the CPU Frequency Scaling Monitor to your panel and seeing if the freezes coincide with a step down. You can also use that applet to change between scaling modes - I think the "Performance" option stops any kind of scaling from happening but wouldn't be terribly friendly for battery life on a laptop I don't think.

As I said - just a thought. :)

---

### Post by XtofR on 2010-05-30
I must have totally wrong version of aticonfig.
The --lsp option also is unrecognizable:
aticonfig: unrecognized option '--lsp'
aticonfig: parsing the command-line failed.

I will test the cpu scaling suggestion tomorrow.
I do indeed use the "ondemand" option currently so there is cpu scaling for sure.

Thanks you all so far. I will return with results as soon as I have them.

Regards

---

### Post by arigator on 2011-10-20
Sorry for my very first post on this forum being a necro post but I stumbled upon this thread while searching a solution for another problem regarding the Fujitsu Siemens Amilo Xi 2550 Laptop.
But just in case, you still suffer the problem or someone different finds this thread.

The problem that everything freezes on the Fujitsu Siemens Amilo Xi 2550 seems to happen on every Linux distribution, but it can be solved by a simple measure:

when you boot your PC and are in the grub where you can choose between your distribution/kernel/Microsoft Windows version you want to start, you have to press "e" in order to change the starting parameters and have to add "clocksource=jiffies" at the end (then press F10 or CTRL+X in order to start).
Then for one session (until the next reboot) the problem would be gone (which you can test by starting music or a youtube video in the browser and then not moving your mouse or touching the keyboard for more than the 10 seconds you mentioned).

If you want to solve the problem of freezing permanently, then you have to modify the file /etc/default/grub and add "clocksource=jiffies" GRUB_CMDLINE_LINUX_DEFAULT="..."
Then it should look like this:
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=jiffies"
GRUB_CMDLINE_LINUX=""

After this you have to write "update-grub" in a terminal and enter. The problem should be solved now.

---

### Post by oldos2er on 2011-10-20
Back to sleep. Please don't bump old threads.

---

