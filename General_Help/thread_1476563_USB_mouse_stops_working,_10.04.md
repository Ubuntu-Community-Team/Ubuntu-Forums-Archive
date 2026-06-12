---
title: "USB mouse stops working, 10.04"
date: 2010-05-07
forum: General Help
---

### Post by sithlordkyle on 2010-05-07
I have read no fixes anywhere, oddly.  This problem happened in 9.10 and seems to be back in 10.04.  The fix on Ubuntu-Geek, which was re-posted various places, does not work either.

However, I do know this is not a hardware issue... or think.  I have a dual-boot with Windows 7 and it is not affected by this.  Also, if I install anything 9.04 or earlier, this does not happen.

Oddly, my netbook had 9.10 and now 10.04 but not this issue.

Sadly I feel I must try other distros as this appears to be a Ubuntu specific error.

Anyone else have any more data to add to this collection?  Or, magically, a fix?

---

### Post by sithlordkyle on 2010-05-08
Oddly enough, I have not tried a 32-bit version, but I assume it's the same problem.

---

### Post by TheNerdAL on 2010-05-08
Do you have another USB mouse that you have access to? It could be the mouse.

---

### Post by sithlordkyle on 2010-05-08
I've tried four separate mice, all work on other computers and the same box when booted into Windows.  Not a mouse issue.  This is an issue with Ubuntu itself.

---

### Post by wickstopher on 2010-05-23
I can confirm this problem on 32-bit Ubuntu as well.  It was intermittent after the initial installation, kept having to sudo shutdown -r from a terminal I would pull up via keyboard shortcut.  Then, I went 10 straight days of uptime with no problem.  I had to restart to do a BIOS upgrade for my motherboard, and the problem is now back and worse than ever.  It'll happen in the middle of working on something, or if I step away for a few minutes and come back it'll inevitably be frozen up.  No problems whatsoever on my Windows partition of the same machine.  At first I thought that maybe my power supply or motherboard was giving up the ghost, but like I said, I've had no problems in Windows.

---

### Post by wickstopher on 2010-05-25
bump.  Anybody out there have any insight on this issue?  I'm getting sick of using windows/restarting every time my mouse locks up.

---

### Post by sniperleader on 2010-05-27
I am having this same issue. New to ubuntu. PS2 Keyboard and mice work fine. But their old, and would rather use the USB ones. Anyone have any luck fixing this?:confused:

---

### Post by jmail524 on 2010-06-06
I am also having this issue, but it is not limited to my mouse and keyboard.  I seem to lose communication with all of my USB devices (Flash Drives & Printers).  The problem is temporarily remedied by either restarting the computer or unplugging and re-plugging in the USB devices.

---

### Post by Rytron on 2010-06-14
I've had problems with my PS2 Mouse, USB Mouse & PS2 Keyboard. I have never had this problem before in Ubuntu! :confused:

---

### Post by rabinnh on 2010-06-16
I have a Logitech USB wireless keyboard/mouse.  After boot, the keyboard works, but the mouse cursor is frozen.

What's really weird is if you wait 3 or 4 minutes, the mouse starts to work and everything is fine.

I triple boot into a Hackintosh and Windows, and I have no problems with using the Logitech kb/mouse with the other OSes.  

Ubuntu is my primary OS, and this machine has been used for 8.04->8.10->9.04->9.10->10.04 without any issues until 10.04.

Definitely a bug.

---

### Post by bondo101 on 2010-06-16
I had the same problem when i first started with 9.10 I had to use the front usb ports of my machine. It did't recognize the rear ones. This is with a new mobo. It still wont recognize wireless mouse or key board. Now the back ports work with usb with no problems. I kept leaving the machine on all the time. 
No suspend or nothing just the screensaver. still works fine after of almost 2 mos of constant use. theres a command line fix that might work, but it's for wireless net cards , someone posted it. I gave up on 10.04 works then doesn't work too glitchey.

---

### Post by Timmer1240 on 2010-06-16
I was having my cursor freeze up with a usb mouse I had an older mouse that just plugs into a serial port its been fine ever since!

---

### Post by Rytron on 2010-06-18
Try this:
```
sudo aptitude purge irqbalance
```

---

### Post by standards on 2010-06-20
i just switched from a ps/2 mouse to a USB mouse and started experiencing intermittent freezes. 

i went into synaptic, searched "mouse" via description and name, and reinstalled everything that seemed to apply- particularly anything xorg. i also installed "mdetect".

so far so good.

---

### Post by lilyselden on 2010-06-27
> **standards said:**
> i just switched from a ps/2 mouse to a USB mouse and started experiencing intermittent freezes. 

i went into synaptic, searched "mouse" via description and name, and reinstalled everything that seemed to apply- particularly anything xorg. i also installed "mdetect".

so far so good.

(Apologies in advance for this long post.)


I am having this problem with a fresh (1 day old) install of 10.04, and a USB (not wireless) mouse on my laptop. Everything installed okay, and the mouse worked okay the first couple of reboots, but now I literally can't work the mouse to do anything when I go into Ubuntu. (It works fine in the Vista partition; I'm in Vista as I type this.)

 My problem is further compounded by the fact that my laptop's touchpad keys don't work right anymore (a hardware problem that LONG predates this Ubuntu installation; it was a never a big concern because I always had mice to work with. (And the mouse worked fine in 9.04.)

I would like to try the solution in the post above (reinstalling everything related to the mouse) but since I can no longer move around the desktop, I can't---unless I figure out how to do it from the Ubuntu recovery mode, or using the keyboard ONLY to open terminal, etc.

Not sure how to do this. I tried researching keyboard shortcuts to opening terminal, but I mostly get tips on what you can do if you're already in terminal, etc. As I mentioned, I know I could access the terminal in recovery mode but I'm not sure what packages to "apt get install" for the mouse (don't know what they're specifically called, etc.) 

Can anyone point me to a link or a post that explains the proper way to install packages in recovery mode (it's been a really long time since I went in there) and what packages I should install? (Or let me know if I'm going about this all wrong?)


Any suggestion or advice is appreciated.


Lily


(a slightly experienced newbie)

---

### Post by Rytron on 2010-06-28
Hi lilyselden. Can you use the touchpad? Try to launch a terminal and input: sudo aptitude purge irqbalance

---

### Post by lilyselden on 2010-06-28
> **Rytron said:**
> Hi lilyselden. Can you use the touchpad? Try to launch a terminal and input: sudo aptitude purge irqbalance


No, unfortunately, the touchpad buttons are of no use because of an old hardware problem unrelated to this issue.

(I did just boot into Ubuntu about an hour ago, and the mouse was working perfectly for about 3 minutes or so, then it failed again...it's done that before, too.) I could try to log in and enter that command in terminal before my "mouse time" expires, or----can I enter that into the recovery terminal also?


(Also, thanks for responding. :p)


Update:  I was able to log into the desktop and run the command you provided before my mouse quit on me. (It still did, though.) 
I was reading an old post on this forum the other day that suggested using only equipment that is known to work with Linux; I will search for info on hardware that is known to work, and post again.

---

### Post by stobbsm on 2010-07-07
Has anybody solved this problem yet?

I'm getting tired of logging in, logging out, then back in again to get this to work.

Just did a fresh install, and the problem seems to be with an update.  Any idea which update it may be so I can re-install again and avoid installing it?

---

### Post by stobbsm on 2010-07-08
Just installed debian squeeze (through updating from lenny) and I'm still experiencing the same problem, with one little twist.

When I am not using compiz, I can move the windows until I click on something inside the window. Example: using gnome's calculator, I move the window, clicked 6 + 6 = (12 in case your curious) then was unable to move the window anymore.  Once I closed that window (alt+f4) I was able to do the same thing.

It seems that something is going on in metacity?

---

### Post by RS232C on 2010-07-09
I'm thinking it has to do with a firefox script or something associated. The reason being, is if I'm in firefox, which I'm in almost all the time, it will lock up periodically, sometimes within a 5 minute timespan if I'm playing something like desktop defender or a game that I'm using the mouse on a lot. However I have stayed off the web on my one system (the other system doesn't lock up ever, still ubuntu 10.04, but it's a amd x2 5000+ not a amd 2400+ and different mobo.) and not gone into firefox on the system that locks up, and it hasn't locked up in 3 days yet.  once again if I cntrl-alt-del, go into hibernate and reboot to the same state it frees the mouse up and returns me to whatever I was doing, but it will lock up again in awhile after doing that. When I first loaded ubuntu, I didn't have this problem at all, and I've been using it now for about 2 months.  Also I might add I've tried the above fixes, and none of them worked for me. redoeing grub, aptitude purge irqbalance, etc.

---

### Post by lidex on 2010-07-09
> **Rytron said:**
> Try this:
```
sudo aptitude purge irqbalance
```

That's not in a default install, so probably not the issue.

---

### Post by lidex on 2010-07-09
Try this in a terminal:
```
sudo apt-get install --reinstall xserver-xorg-input-mouse mdetect xbase-clients
```
Also try different usb port. Are those having issues plugged in directly or to a hub?

---

### Post by RS232C on 2010-07-09
they are plugged in directly for me, and I have tried different USB ports. I'll try that in a second, but today, a second ago, I stayed out of the system since my last post....just tried it, my mouse worked fine then hit firefox...as soon as FF loaded...mouse froze.  ok, I installed mdetect,xorg etc. we'll see if that fixes it. I'll go play a game of desktop defender or something. I should also perhaps mention, I have noticed this system has been bogging down on games like desktop defender in facebook. This could be a flash issue?

---

### Post by RS232C on 2010-07-10
ok...tried: sudo apt-get install --reinstall xserver-xorg-input-mouse mdetect xbase-clients  but it just froze a few minutes ago.....it installed mdetect and the others, but obviously no go. :-( the errors I get are unable to enumerate usb port blah blah.....not sure if that helps or not.

---

### Post by lidex on 2010-07-10
Check dmesg when this occurs, maybe kernel log also. Does this occur with different kernels and/or without firefox running. Try to duplicate conditions except for browser - use a different one - and see if the same.

---

### Post by RS232C on 2010-07-10
dmesg does produce some interesting information. good call. Btw, I have been doing different configurations to isolate the problem. just now, it has happened without firefox or any browser being loaded actually. so that can be ruled out. here is the info from dmesg, that I found interesting:  ```
[214069.307396] usb usb2: root hub lost power or was reset
[214069.307442] usb usb3: root hub lost power or was reset 
[214069.307483] usb usb4: root hub lost power or was reset 
[214069.307524] usb usb5: root hub lost power or was reset 
[214069.307543] usb usb1: root hub lost power or was reset 
[214069.307596] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
[214069.307605] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64  ~    
[214100.304045] usb 2-1: USB disconnect, address 22   
[214100.544038] usb 2-1: new low speed USB device using uhci_hcd and address 23    
[214100.722266] usb 2-1: configuration #1 chosen from 1 choice  
[214100.738647] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input272    
[214100.739108] generic-usb 0003:046D:C00E.0053: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-1/input0    
[261315.536050] usb 2-1: USB disconnect, address 23    
[261316.024040] usb 2-1: new low speed USB device using uhci_hcd and address 24    
[261331.768029] usb 2-1: device descriptor read/64, error -110 
[261347.640027] usb 2-1: device descriptor read/64, error -110 
[261347.856019] usb 2-1: new low speed USB device using uhci_hcd and address 25    
[261363.512102] usb 2-1: device descriptor read/64, error -110  
[261379.384076] usb 2-1: device descriptor read/64, error -110  
[261379.600020] usb 2-1: new low speed USB device using uhci_hcd and address 26    
[261390.140023] usb 2-1: device not accepting address 26, error -110 
[261390.252034] usb 2-1: new low speed USB device using uhci_hcd and address 27    
[261400.804026] usb 2-1: device not accepting address 27, error -110  
[261400.804243] hub 2-0:1.0: unable to enumerate USB device on port 1     
```   I presume some of this is from me hibernating, but prior to that it seems the usb devices are being powered down or reset. (which explains of course why the led light goes out and it stops responding.

---

### Post by RS232C on 2010-07-10
blah, I tried to put some formatting in that so it didn;t run all together, but it didn;t work out so well.

---

### Post by rCXer on 2010-07-10
Try using the code and /code tags

---

### Post by lidex on 2010-07-10
Not to give a formatting lesson, or anything, but your tags should look like this:
[.quote] generic text blah blah blah [./quote] - minus the periods. It's in the toolbar.

---

### Post by RS232C on 2010-07-12
hey it's all good, give me formatting lessons, if I don't know then I deserve to be schooled, and then I'll know. works for me. I'll try to edit and reformat it with the code /code tags.  code /code put it in a nice little code window that was scrollable......cool, but not quite what I wanted. I'm not getting hard returns, seems to be the problem. I used quote /quote, but once again still no hard returns or newlines, whatever we are calling them. hmm...wonder if &#x000D; will work...no...it didn't :/ ok...how about the html break? 
...ya...ya...thats the ticket....ok now that that works...perhaps I'll revist the code /code tag.....course this isn;t code, it's error output...but still it is a cool code window. shweet daddy likes....ok, now back to our mouse dying problem.

---

### Post by ottabaub on 2010-07-12
My Logitech nano worked fine with 8.04, 9.10 and 10.04 when I upgraded from 9.10 in May. I recently bought a Asus netbook that runs Windows 7. Yesterday I unplugged my nano receiver from my laptop (that was turned off) and plugged it into the netbook. Worked fine. This morning I plugged the nano back into my laptop and it doesn't work anymore. I tried new batteries. No joy. I plugged it into a desktop PC running Windows XP. Worked fine. Back into my laptop - still doesn't work.

Having said all that, I don't think the nano is the problem. I tried a wired USB mouse and it doesn't work either.

I tried all the suggestions in this post and none have worked. My laptop has 2 USB ports and neither works. I had a look at the dmesg output and there must be some internal ports because by looking through the output I determined that the external USB ports are 3 & 4. I have a 4-port USB hub plugged into 3. (This is not the problem because with or without the hub, my mouse doesn't work. I did, however, find some errors regarding port 4.
[    1.564220] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.684111] usb 4-1: device descriptor read/64, error -71
[    1.932944] usb 4-1: device descriptor read/64, error -71
[    2.288079] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    2.732893] usb 4-1: device descriptor read/64, error -71
[    2.956176] usb 4-1: device descriptor read/64, error -71
[    3.172076] usb 4-1: new full speed USB device using uhci_hcd and address 4
[    4.112468] usb 4-1: device not accepting address 4, error -71
[    4.224094] usb 4-1: new full speed USB device using uhci_hcd and address 5
[    4.632066] usb 4-1: device not accepting address 5, error -71
[    4.632096] hub 4-0:1.0: unable to enumerate USB device on port 1
[   42.048076] usb 4-1: new full speed USB device using uhci_hcd and address 6
[   42.168244] usb 4-1: device descriptor read/64, error -71
[   42.392078] usb 4-1: device descriptor read/64, error -71
[   42.608096] usb 4-1: new full speed USB device using uhci_hcd and address 7
[   42.728093] usb 4-1: device descriptor read/64, error -71
[   42.952096] usb 4-1: device descriptor read/64, error -71
[   43.168096] usb 4-1: new full speed USB device using uhci_hcd and address 8
[   43.745277] usb 4-1: device not accepting address 8, error -71
[   44.205116] usb 4-1: new full speed USB device using uhci_hcd and address 9
[   44.616091] usb 4-1: device not accepting address 9, error -71
[   44.616122] hub 4-0:1.0: unable to enumerate USB device on port 1

I appears as though the system is trying one address after another and the USB dongle is not responding. I guess I need to find out what this error -71 is. Anybody have any ideas?

Addendum: ~3 hours later
Okay, here's a weird one. I have not found out how to fix this problem. It appears to be some kind of bug not necessarily related to Ubuntu. Here's what's weird. I have a 4-port, port powered hub. I plugged it in, plugged my USB wireless mouse dongle in and now it works. It still doesn't work if I plug it directly into either laptop USB port, though. So now I'm even more stumpted that before.

This reminds me of a HP scanner problem and Windows XP I had a few years ago. Although HP specifically recommended not using the scanner with a hub, the only way I could get it to work was to use it with a hub. Go figure.

---

### Post by t.ebentheuer on 2010-07-12
Im another one having the same problem, on  both Ubuntu 10.04 and Xubuntu 10.04.  Mouse works fine for a few minutes then suddenly wont respond.  Keyboard works fine.  Im using 9.10 now since it doesnt have the problem.  I want to get it fixed but it doesnt help that im a total linux noob!

---

### Post by mdmullins on 2010-07-13
I am having the same issue and a quick search of Google reveals this as a persistent and ubiquitous problem.

Someone in another forum (or was it this one?) suggested that it is not actually the usb devices freezing, but rather the entire system locking up, which gives the illusion that the mouse/keyboard have locked. I don't know if this is true or not, but it makes sense.

It also seems to be unrelated to hardware as a lot of different configurations seem to be popping up. I am using a fairly new Gateway, AMD triple core processor with 4 gigs of ram.

I understand that Linux is largely a community driven phenomenon and that we need to depend on one another to solve the problems as they come up, but with something as critical as this, I'm wondering if there's not someone directly associated with the distribution making this one a priority.

---

### Post by RS232C on 2010-07-14
> but rather the entire system locking up, which gives the illusion that the mouse/keyboard have locked. I don't know if this is true or not, but it makes sense.  that doesnt fly with me, or at least my situation, nor yours. as you've stated above, and with me, the keyboard still works, and indeed I hit cntrl-alt-del and alt-tab to hibernate mode, which saves its state, and reboots with the image...and it comes back fine and works again...right now since the last time in fact its been good for a few days now. If the whole system locked up then obviously saving its state wouldnt work. Nope this, at least with me is a USB issue. and it seems to be powering down periodically.

---

### Post by mdmullins on 2010-07-14
Is this maybe the answer?:

[http://www.nvnews.net/vbulletin/showthread.php?t=142656](http://www.nvnews.net/vbulletin/showthread.php?t=142656)

Could use a true techie in here to help out.

---

### Post by mdmullins on 2010-07-14
The more I work with this the more I'm convinced this is a kernel issue and not linked to any one distro. The exact same thing happened when I was using the liveCD for pclinuxos. 

Here is a thread in Arch linux from 2009 that sounds eerily familiar.

[http://bbs.archlinux.org/viewtopic.php?pid=703024](http://bbs.archlinux.org/viewtopic.php?pid=703024)

Am I off base here? Is it just a buggy kernel?

---

### Post by lidex on 2010-07-14
> **mdmullins said:**
> Is this maybe the answer?:

[http://www.nvnews.net/vbulletin/showthread.php?t=142656](http://www.nvnews.net/vbulletin/showthread.php?t=142656)

Could use a true techie in here to help out.
Maybe for users with nvidia graphics. Not sure that's the culprit though. Anyway, the latest drivers have the patch applied:
> 195.36.31 and 256.35 are both pre-patched

---

### Post by Royle Lindsey on 2010-07-14
Hi..
The USB mouse I've plugged in stops working after maybe 10 minutes (the time varies). The light goes off and just seems like the slot has given up the ghost. Plugging into the other slot doesn't help, the mouse is dead until I reboot..Can anyone please help me..Thanks..

---

### Post by mdmullins on 2010-07-14
Well I've downgraded to 2.6.31-11, and so far so good. I've seen this over and over again throughout distros so I thought I would try it. Not sure what functionality I'm trading off for the older kernel, but the system was all but unusable before. Anything is better that having to restart the machine every ten minutes -- that's Redmond crap.

Has anyone else had success with downgrading?

Simply: I believe 2.6.32 just has some kinks that need to be worked out.

---

### Post by ottabaub on 2010-07-14
> **mdmullins said:**
> Well I've downgraded to 2.6.31-11, and so far so good. I've seen this over and over again throughout distros so I thought I would try it. Not sure what functionality I'm trading off for the older kernel, but the system was all but unusable before. Anything is better that having to restart the machine every ten minutes -- that's Redmond crap.

Has anyone else had success with downgrading?

Simply: I believe 2.6.32 just has some kinks that need to be worked out.

I'm on my 3rd kernel since upgrading from 9.10 so I can't try a degradation to 2.6.31. I did try 2.6.32-21 and 2.6.32-22 and I have the same problem. However they used to work just fine. I upgraded to 2.6.32-23 last week sometime (I think). My mouse worked okay until Monday - 2 days ago. I don't know what changed. I don't think it's a kernel issue. And, with the dongle plugged into my 4-port hub, my mouse works again. The hub is not self powered and gets it's power from my laptop so it's not a voltage drop issue. It's bizarre.

---

### Post by mdmullins on 2010-07-14
Does everyone here have Flash installed? I finally uninstalled Flash with the original 2.6.32 kernel and haven't had a problem since. (Ten hours and counting...)

For me at least, now that I think about it, Firefox was always up and running whenever the mouse would lock.

Hopefully the world is going to html5 anyway. Flash really bites.

---

### Post by mdmullins on 2010-07-14
As a side note has anyone tried **upgrading** to 2.6.3**3** with Flash installed? Is this even possible at this time? I'd be curious if there wasn't a way to make Flash and Linux at least comfortable bedfellows. 

(This is of course assuming that the problem is Flash: which it seems to be for me.)

---

### Post by lakelovers on 2010-07-14
Here's how I fixed my mouse problem: After start up, the mouse is frozen. I disconnect the mouse and reconnect, same usb, and the cursor moves free and normal. It's not a clean fix but works for me. Does this action give a tip to anybody on what the primary problem is?

---

### Post by mdmullins on 2010-07-14
> **lakelovers said:**
> Here's how I fixed my mouse problem: After start up, the mouse is frozen. I disconnect the mouse and reconnect, same usb, and the cursor moves free and normal. It's not a clean fix but works for me. Does this action give a tip to anybody on what the primary problem is?


For me, and for many others from what I can tell, the freeze doesn't happen at boot. It's 5...10...20 minutes into a session and then the mouse freezes. And from what I've heard -- and my personal experience as well -- nothing revives the mouse at that point expect a hard reboot. So if you can unplug it and plug it back in as a fix then you're having a different, and thankfully easy, problem. :)

Again, if what I'm experiencing is the same as most people, I have a fix. When I uninstalled Flash, the freezes cease to happen. It's been something along the lines of 24 hours now without a glitch.

Would like to know if someone can confirm that Firefox/Flash are the cause.

---

### Post by ottabaub on 2010-07-15
> **mdmullins said:**
> For me, and for many others from what I can tell, the freeze doesn't happen at boot. It's 5...10...20 minutes into a session and then the mouse freezes. And from what I've heard -- and my personal experience as well -- nothing revives the mouse at that point expect a hard reboot. So if you can unplug it and plug it back in as a fix then you're having a different, and thankfully easy, problem. :)

Again, if what I'm experiencing is the same as most people, I have a fix. When I uninstalled Flash, the freezes cease to happen. It's been something along the lines of 24 hours now without a glitch.

Would like to know if someone can confirm that Firefox/Flash are the cause.

Firefox/Flash is definitely not the issue for me. Whether I plug the wireless mouse dongle in before I power up or after the desktop has loaded, the mouse doesn't work. I wouldn't say it's *frozen*. It simply doesn't work - unless I plug it into my hub. Firefox may or may not be running. It doesn't make any difference.

---

### Post by rCXer on 2010-07-16
This issue simply vanished for me yesterday.  I have no idea why...

---

### Post by lidex on 2010-07-17
Try updating your libusb from lucid proposed. This post gives details:
[http://ubuntuforums.org/showpost.php?p=9594127&postcount=60]("http://ubuntuforums.org/showpost.php?p=9594127&postcount=60")

---

### Post by polytropos on 2010-07-17
I have a similar problem, but it is primarily that the mouse is glitchey.  When I'm using Firefox the mouse will frequently work fine for 3-5 second spans and then freeze for a few seconds.  Sometimes, but not always, the mouse will eventually freeze entirely.  This doesn't happen when I'm using other programs, so I suspect that Firefox is to blame.  The mousepad on the laptop never glitches like this - it is only the mouse connected by USB.  I had this issue in earlier versions of Ubuntu as well.

Is there a setting in Firefox to tweak that will solve this issue?

---

### Post by lidex on 2010-07-17
> **polytropos said:**
> I have a similar problem, but it is primarily that the mouse is glitchey.  When I'm using Firefox the mouse will frequently work fine for 3-5 second spans and then freeze for a few seconds.  Sometimes, but not always, the mouse will eventually freeze entirely.  This doesn't happen when I'm using other programs, so I suspect that Firefox is to blame.  The mousepad on the laptop never glitches like this - it is only the mouse connected by USB.  I had this issue in earlier versions of Ubuntu as well.

Is there a setting in Firefox to tweak that will solve this issue?

For that, take a look at lovinglinux's tutorials:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by polytropos on 2010-07-17
Thanks for pointing out that excellent tutorial, lidex, but I couldn't find anything there about mouse issues.

Any other thoughts?

---

### Post by ottabaub on 2010-07-18
> **lidex said:**
> Try updating your libusb from lucid proposed. This post gives details:
[http://ubuntuforums.org/showpost.php?p=9594127&postcount=60]("http://ubuntuforums.org/showpost.php?p=9594127&postcount=60")

I tried the lucid proposed thing but, as it turns out, I'm using 2:0.1.12-14ubuntu02, the latest version of libusb, already. Maybe that's the problem. Who knows?

---

### Post by lidex on 2010-07-18
*ottabaub*,
Did you update your repos first?
```
sudo apt-get update
sudo apt-get upgrade
```
You were already using proposed repo?
Backports may have a different version as well.

---

### Post by ottabaub on 2010-07-18
> **lidex said:**
> Did you update your repos first?
```
sudo apt-get update
sudo apt-get upgrade
```
You were already using proposed repo?
Backports may have a different version as well.

I assume you're responding to me. If so, how is that related? When I entered libusb in SPM it showed the installed version and the numbers were the same. I found that curious since I know it didn't come from lucid proposed which I wasn't using. But isn't it possible this version is no longer "proposed"?

---

### Post by lidex on 2010-07-18
> **ottabaub said:**
> I assume you're responding to me. If so, how is that related? When I entered libusb in SPM it showed the installed version and the numbers were the same. I found that curious since I know it didn't come from lucid proposed which I wasn't using. But isn't it possible this version is no longer "proposed"?

Certainly, that's what (one thing) I'm trying to figure out.
I don't have lucid on this box.

---

### Post by Metaluim on 2010-09-18
My USB mouse is also intermittently freezing, this happened after a kernel update I believe. Is there a solution for this yet?

---

### Post by youbuntu on 2010-09-22
You flipping well better fix this; pathetic! :D

---

### Post by retched on 2010-09-25
I am having the same mouse freezing problem.

I do not use Firefox, I use Opera.  I am using 9.10 now, and I have flash installed, 64bit Ubuntu and a wired USB optical mouse I also am using nVidia Xserver graphics ver 180.

This is a dual boot machine, and I can go weeks without experiencing a freeze.. And I use the machine 12+ hours a day.  The only reason I ever reboot is

a)  Updates require it
   or
b)  Mouse Freezes.

I have been dealing with it because it wasn't too much of a problem for me, I simply re-booted.

But today, I started gaming.  When the game has control of the full screen, I have no way to exit the game to report back to the Ubuntu GUI to reboot.  I HAVE to yank the plug.

So, I run my business off this machine, and while all is backed up, I feel awkward about upgrading to ubuntu 10 at this point.

Has there been any breakthroughs?

---

### Post by pkrakesh on 2010-10-22
I also encountered the same problem. The easy way to fix it, is to change the Visual Effects to 'None' instead of the default 'Normal'. But the problem seems to be reappears when I tried to work with Blender. Blender is installed and when it opens the system suddenly stops responding.

---

### Post by Rytron on 2010-10-22
> **pkrakesh said:**
> I also encountered the same problem. The easy way to fix it, is to change the Visual Effects to 'None' instead of the default 'Normal'. But the problem seems to be reappears when I tried to work with Blender. Blender is installed and when it opens the system suddenly stops responding.

Hi pkrakesh.

Thanks for the tips.

---

### Post by coffee412 on 2010-12-07
I just did an install tonite on a HP tower AMD Processor- 64bit install CD. No updates applied yet. 

USB mouse locks up. Changed mice to another USB one and it locks too. Rest of system is responsive.

Im hoping running an update and its a kernel thing. But I will keep searching the forum here and see what other stuff comes up. 

If anyone knows any news on this (since this thread is getting bit old) I sure would love to hear. Hoping an update fixes it.

Might have to bring out a ps/2 mouse to my customer.

coffee

---

### Post by Rytron on 2010-12-08
> **coffee412 said:**
> I just did an install tonite on a HP tower AMD Processor- 64bit install CD. No updates applied yet. 

USB mouse locks up. Changed mice to another USB one and it locks too. Rest of system is responsive.

Im hoping running an update and its a kernel thing. But I will keep searching the forum here and see what other stuff comes up. 

If anyone knows any news on this (since this thread is getting bit old) I sure would love to hear. Hoping an update fixes it.

Might have to bring out a ps/2 mouse to my customer.

coffee

I've found ps/2 mice to freeze a lot since I moved to Ubuntu 10.10. I only use a USB mouse and never have a problem. Have you done this:
```
sudo aptitude purge irqbalance
```

---

### Post by coffee412 on 2010-12-08
> **Rytron said:**
> I've found ps/2 mice to freeze a lot since I moved to Ubuntu 10.10. I only use a USB mouse and never have a problem. Have you done this:
```
sudo aptitude purge irqbalance
```

I have not performed that yet. But I did see it in the thread. Wondering if thats a one time fix or something to perform whenever you boot. 

My other option was bringing out a ps/2 mouse to the customer but looks like that would not be an option either from your post. 

I will try that and post back if it works for me. My other option is reinstalling  with karmic koala. 

Ill give it a shot. Thanks!

coffee

---

### Post by lidex on 2010-12-08
I'm shocked at how many people seem to have this problem vs. how many bug reports have been filed. The only relevant thing I found in Launchpad is here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627862](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627862)
(or show me yours)

If your problem is not solved, file a bug report or subscribe to and comment on another. Bugs don't get fixed in the forums.

---

### Post by coffee412 on 2010-12-08
> **lidex said:**
> I'm shocked at how many people seem to have this problem vs. how many bug reports have been filed. The only relevant thing I found in Launchpad is here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627862](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627862)
(or show me yours)

If your problem is not solved, file a bug report or subscribe to and comment on another. Bugs don't get fixed in the forums.

I commented to the above link to launchpad. I have tried all the fixes but nothing seems to work for a fix. I will keep working at it the best I can and see what I can come up with. Might roll back to karmic koala and see if the same problem persists.

Thanks for your post



WAIT.

I have it. I am actually pissed off at myself for not catching this. I have not tested it but Im pretty sure this is the problem.

From logs:
Clocksource tsc unstable (delta = -175079518 ns)

This has been a problem before with a system that experienced total lockups. I had to change the clocksource and it would run right after that. Im pretty sure when I go out to site tomorrow this is going to work.

For anyone following along it would be rude to not post the fix of course.
1. Find your available clocksources:

cat /sys/devices/system/clocksource/clocksource0/available_clocksource 
acpi_pm pit jiffies tsc

2. Find your current clocksource:
cat /sys/devices/system/clocksource/clocksource0/current_clocksource

acpi_pm 

3. Choose another clocksource 
jiffies

4. Edit /etc/default/grub file and add: acpi=<new clock source>
Save and exit.
5. Run "update-grub" to recompile grub

6. reboot

---

### Post by coffee412 on 2010-12-09
Dell Dimention Tower. 1 gig of ram 100 gig drive. Nothing special. Nvidia graphics card. 

The problem was indeed acpi timer. Unfortunately, there is only one option so I cannot change it to jiffies or tcm, hep ect.. So, Basically, Ubuntu will not run correctly on the computer. I did try and disable acpi but then I had the same exact problem as before - mouse lockup. 

But we know the problem now. Its just a piece of junk computer I guess. Even my cheap gigabyte board in my computer offers a few timer setups (jiffies,tc,hep). 

cat dell dimention > /dev/null

Replacing computer with an HP that I have lying around. Runs fine.

---

### Post by tealex on 2012-01-09
i have the same problem 
mouse suddenly freezes 
and in /var/log/messages 
USB disconnect, address XX

me help reinstall compiz

```

sudo apt-get purge compiz*
cd $HOME && rm -rf .compiz/ .config/compiz/

```

---

### Post by nothingspecial on 2012-01-10
This thread is old.

Please make a new one.

Closed.

---

