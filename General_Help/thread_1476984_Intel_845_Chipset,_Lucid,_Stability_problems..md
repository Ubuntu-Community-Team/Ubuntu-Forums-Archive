---
title: "Intel 845 Chipset, Lucid, Stability problems."
date: 2010-05-08
forum: General Help
---

### Post by linuxrockz on 2010-05-08
Hi everyone,

I am facing some serious problems randomly with lucid.

1. Sometimes when I try to shutdown my computer the display becomes filled with pixels of different colors as shown in the image (The problem is very random so I was not able to take a photo, I tried to recreate the effect using GIMP). Then the display turns off (Analog power saving mode) But my system never turns off.

2. While working on my computer the display sometimes goes kaput and blinks as in the second image. It stops responding completely I am not even able to go to terminal (Ctrl + Alt + F1). Leaving me with no option but to use the reset button. Causing me to loose all the work in progress.

3. Firefox responds very slowly upon closing it takes 5-6 seconds for the window to close.

Lucid Works like a charm on my laptop though.

Please help me I am in a fix. 
I don't want to go back to karmic or use the vesa driver.
Please tell me if there is any way out.

PS:- KMS is also disabled in my system. Enabling it didn't improve stability.
and here is the output of my videocard (lshw)

[I]*-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d8000000-dfffffff(prefetchable) memory:e0100000-e017ffff[/I]


Thanks in advance.

---

### Post by linuxrockz on 2010-05-08
Hi just wanted to inform that I faced the problem twice after posting the thread. 
Both times during startup just after the plymouth screen.  :mad:

It is getting on my nerves.
Please help.

---

### Post by linuxrockz on 2010-05-08
Well now my computer wont boot to gui and I need my computer now for my studies. I would have gladly waited for some more time but I can't wait any more. So am installing karmic :-( ](*,)

I am sorry and I sincerely hope that in a few months these issues would be fixed. Will try lucid again after 3-4 months.

---

### Post by elianthony on 2010-05-11
I'm experiencing these issues with the graphics as well. Has anyone figured this out?

---

### Post by mikewhatever on 2010-05-11
Nobody ever reads the release notes. ](*,)

---

### Post by RJQ on 2010-05-11
For now is a no go with this card, is been there for a while and seems is not going to go, the fix is now expected from upstream in the xorg people but it is very unlikely to happen. (because the fix could mess up apparently new software running well in different hardware) now it can be a little polished and make the system more stable (I am using arch  with newer kernel now with more stability but the crashes still present).

and in fact the release notes tells this problem. you can follow the numerous bugs in launchpad or if you guys want a stable workable computer return to the previous ubuntu that was working in your machines. unfortunately that is the truth for now. good luck.:(

---

### Post by Metallinut on 2010-05-24
What a letdown. Imaging my story:

My father-in-law is a lifelong Windows user. He finally got a virus so bad that I told him we'd have to rebuild. I used my own Ubuntu (karmic) to grab files off of his HDD, for which he was extremely grateful. I told him I would rebuild his machine with Ubuntu. It would take some time to get used to, but it would be much safer from malware/spyware/viruses. I told him how great Ubuntu is. Then I rebuild his system with lucid. Turns out he's got an Intel 845. He's been asking when his computer will be ready. I had to tell him there's a bug in Ubuntu with his graphics card, and is unusable. Total Ubuntu fail.

There's no shortage of people who will tell you Ubuntu is ready for prime-time...but this kind of bug is enormous! Completely unacceptable.

Meanwhile, I'd like to downgrade his PC back to karmic. Can I do that? Or do I need to rebuild it?

---

### Post by RJQ on 2010-05-25
In my machine with the 845 card karmic was even worst, (but usable whit a downgraded xorg driver, very slow and choppy display though), but when I need to do serious business I have to go back to 8.04, still has some life and I am not installing more software in it. for playing with newer programs I am on chakra which also crash but not as much as lucid, now they are making a lot of sound with the testing of xorg 1.8, I hope to test it soon but I am not keeping any hope on it. this is a 7+ year old computer, I guess support for this old hardware are not part of the goals in the linux world and that thus sad is comprehensible.

P.D. remember that this is a xorg/linux wide issue and not purely Ubuntu. with a compatible hardware this is an unbeatable system.

---

### Post by vkrmsv on 2010-09-04
Hi

I am having exactly the same problem that was reported in the first post on this thread. Since it has been a few months since the last post here, I was wondering if there are any updates in this regard.

Thanks!

---

### Post by lathanial on 2010-09-23
Possible Fix - disable Open Office Quick Start if you are using it

I have the 845 chipset and was having the same problems as described above  - intermittent lock up with white vertical bars flashing - I couldn't go to terminal mode but I could reboot with REISUB. In addition, quite often when I used the gui to shut down the box it wouldn't do it - everything seemed to work ok but it would not shutdown and didn't give an error. I would go to terminal and issue "shutdown -h now" to power down. Occasional when I received and update notice I would click OK to do the updates but noting would happen. I couldn't get the updates until I rebooted. To make a long story even longer, I discovered a post in the forums talking about Open Office Quick Starter (I'm using OO 3.2) causing problems shutting down with the gui. The next time it wouldn't shut down with gui I exited the Quick Starter and tried again and it worked. The same with the update window not responding - exited Quick Starter and tried again and update worked as normal. I quit using Quick Starter and my system no longer crashes. Before I quit using Quick Starter I would crash about 3 to 5 times in an 8 hour period - some days a lot more. Since disabling Quick Starter I've been running over two weeks with no crashes. As an aside, I've confirmed the gui shutdown and update problem on a system with an Nvidia card but that machine has never crashed.

I hope someone can check this out as I only have the one machine with 845 chipset running Lucid.

lathanial

---

### Post by sijar on 2010-10-31
[@lathanial]("http://ubuntuforums.org/member.php?u=345124")
This isn't just startup problem is guess :(,
Since the OS has crashed several times in the midst of using other applications such as using netbeans, Firefox and totem player.

If this is a issue with Xorg/Linux issue when fix is going to be made?

---

### Post by DougE410 on 2010-11-06
I have a gateway desktop with the same onboard video card. I was experiencing a crash or two a day with lucid; not bad enough for me to reconsider my choice to use ubuntu as my OS, but annoying none the less ........... it usually chose to crash at the most inopportune moment. lol 

I upgraded to Maverick last night and my system hasn't crashed since (knock on wood). Maybe they fixed the issue with this upgrade?

I suppose I could test things out by switching to a screen saver with lots of graphics and see if it immediately crashes, but I think I'll let sleeping dogs lie, as it were.

---

### Post by sijar on 2010-11-29
[SIZE=2]Hi Ubuntian,


          I have somehow managed to resolve this issue. _Its guaranteed to work on this hardware:_
$ lspci -nn | grep VGA[/SIZE]  [SIZE=2][COLOR=#000000]
00:02.0 VGA compatible controller [0300]: Intel Corporation **82845G/GL**[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)[/COLOR][/SIZE][SIZE=2]

Here's what I did.
[/SIZE]  
[LIST=1]
[*][SIZE=2]**Install a fresh Ubuntu Lucid Lynx(10.04).**[/SIZE]
[*][SIZE=2]**Re-enable KMS**:- 
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u[/SIZE]
[*][SIZE=2]**Generate the xorg.conf file:- **Lucid Lynx/Jaunty/Karmic doesn't have Xorg file. It tries to auto-detect everything as thats why it screws up. Following are the steps to create a Xorg file. Once this is placed Lucid will use it. In order to generate xorg.conf you need to switch to one virtual console using the key combination **CTRL + ALT + F1**. Now execute the following commands:
 user@ubuntu ~#** sudo service gdm stop**
 This command will stop the X.
 Now we need to generate the xorg.conf file:
 user@ubuntu ~# **sudo Xorg -configure**
 This has generated the file in ~/xorg.conf.new.
 We need to make the X using it so we have to put this file inside /etc/X11/
 user@ubuntu ~# **sudo mv ~/xorg.conf.new /etc/X11/xorg.conf**
 After moving this file to the proper location you can start the X again and see what happens:[/SIZE]
[*][SIZE=2]**Disable DRI:- **
Add Option "DRI" "off" in the following into /etc/X11/xorg.conf: 
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
**Option          "DRI" "off"**
EndSection[/SIZE]
[*][SIZE=2]**Reboot.**[/SIZE]
[/LIST]
[SIZE=2]Its been a week and it hasn't crashed since. Although tux-race is a title slow however because hardware acceleration is off.

**This link ([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)) has been particularly helpful. **
------------------------------------------------- 
*"I should make it a habit to read the author" ;). *[/SIZE]

---

### Post by sijar on 2011-01-19
Hi everyone, I got some good news on the Ubuntu 10.4 Xfreeze bugs, :KS 

I would strongly recommend to migrate to **Ubuntu 10.10 Maverick Meerkat**, I think they have solved the Xorg related bugs.
  Once I install Ubuntu 10.10 Maverick Meerkat, I have never faced any Xfreeze issues. :D

---

### Post by jayw on 2011-03-17
Hi, I know this is a bit older post -sorry - but I'm just wondering if anyone can give me an update on the stability of the Intel 82845 chip in 10.10 Meerkat. I've had a rough go of 10.04, I'm sorta winning the battle but it's a tenuous thing and I don't think I've cleared up the issue 100% in Lucid. 
 
The patches from Ubuntu helped, so did nomodeset, but I am pretty sure I can still crash the video at will by clicking on the screensavers.
 
I'm thinking about Xubuntu too. I have 2GB memory on a Compaq Evo D510 8-yr-old PC but the box is otherwise great. I do also get the CPU spikes sometimes running Gnome and this is prompting me to think Xubuntu. Leaner is better so long as I still have all the apps. Besides I'm not gonna get blazing graphics with the 82845 anyway. But right now I get jittery video and what I'd call mediocre graphics performance.
 
I'm thinking Xubuntu 10.10, clear up the video intermittent blackouts AND maybe lose the CPU spiking too.
 
Thoughts? I appreciate it.

---

### Post by lithopsian on 2011-03-17
Should be better in 10.10.  Mostly down to newer Xorg and drivers for your card.  Should be version 2.12 in Maverick, although I found the 2.9.0 driver in Karmic was stable.

---

