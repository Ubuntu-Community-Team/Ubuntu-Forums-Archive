---
title: "Occasional blank screen on start up"
date: 2010-04-18
forum: General Help
---

### Post by MorrisseyJ on 2010-04-18
I am having some problems when booting in Ubuntu. Occasionally, when i boot my machine, it stalls at a blank screen before the login screen comes up.

When this happens i select, or have the Grub auto select, Ubuntu. The Ubuntu logo then shows against a black screen. The logo then disappears and i am left with a black screen i.e. the login screen does not come up. 

If this happens i manually power down and try again. After i manually power down i notice that at the grub loader there is no count down for the auto-select for Ubuntu/Windows.

Usually, after powering down and trying again i manage to get into Ubuntu. The problem seems to occur quite randomly and i would be lying if i could tell you the percentage of boot ups that have a problem. 

My feeling however is that the problem is becoming more frequent and today i had to manually power down and reboot four times in a row. Notably, some of the times after powering down the grub had the countdown running. I am worried that one day the whole thing will just stop working.

I am pretty new to Ubuntu and Linux but i see that both the web and forums are filled with stuff on blank screens in Ubuntu. I have found what looks like a solution here ([http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html](http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html)) but i am not sure if the problem here is the same as mine - i think this link is referring to a case where the screen is always blank. I have also found the following ([http://georgia.ubuntuforums.org/showthread.php?p=8903558](http://georgia.ubuntuforums.org/showthread.php?p=8903558)) but i don't really understand the solution and again worry that the problem is not the same as mine.

Finally i found this post ([http://georgia.ubuntuforums.org/showthread.php?p=8903558](http://georgia.ubuntuforums.org/showthread.php?p=8903558)) which remains unsolved. This seems most clearly to describe the problem that i am having.

If any of the above links solve my problem it would be great if someone could tell me which one - possibly with some clearer details on the steps to follow. If my case is the same as that unsolved post then any ideas on a solution, or suitable steps to find a solution, would be appreciated.

---

### Post by quixote on 2010-04-19
The symptoms you describe sound like the system is have trouble with the graphics driver.  No graphics means the graphical user interface (relates to X Windows, xorg, and lots of related stuff) won't load and, presto, you're staring at a blank screen.

The links (the second and the third seem to be the same one) talk about different solutions to graphics driver problems.  fglrx, if I remember right, is a driver commonly used for ATI graphics (??), or was it Nvidia?  Anyway, the point is, we need to figure out what your situation is, because the commands to use depend on that.

1) Your computer, 2) Graphics processor, 3) which version of Ubuntu you're running.

If you don't know #2, you can run "lshw" (without quotes) in a terminal, and plow through the output.  The graphics info is near the beginning.

---

### Post by MorrisseyJ on 2010-04-19
Hi, thanks for looking at this. Here is the info you wanted:

1)Asus A6RP - entertainment notebook

2)
> *-pci
          description: Host bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:9000(size=4096) memory:fe100000-fe1fffff memory:bdf00000-ddefffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:c0000000-cfffffff(prefetchable) ioport:9800(size=256) memory:fe1f0000-fe1fffff memory:fe1c0000-fe1dffff(prefetchable)3) Ubuntu 9.10

So it looks like i am using an ATI graphics driver. Does that suggest that i should use the  fglrx fix?

All help is much appreciated.

---

### Post by quixote on 2010-04-19
Yup.  You're using an ATI Radeon Xpress 200.  And, yes, the instructions about fglrx at the linux.dipin link might be useful.  I'd also search these forums for "karmic ATI Radeon Xpress 200 Asus" and see what comes up.  Karmic introduced a lot of changes, so instructions earlier than last fall sometimes don't work as expected.

Since you don't have a Dell, I wouldn't lean too heavily on pages about Dell machines.  This sort of thing is quite hardware dependent, and those instructions may not apply.

---

### Post by MorrisseyJ on 2010-04-20
So i tried the instructions from ([http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html](http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html)). Things didn't go quite as i think they should have and with my limited knowldge hubris set in...

So i chose recovery mode from the Grub menu.

Then there was no option to: [COLOR=#000000]Select recovery mode from the boot menu.[/COLOR]

So i selected "resume normal boot from the menu". 

This unexpectedly (for me at least) took me to a prompt screen. At this i logged in with my username and password. 

Then i tried the command:

[COLOR=#990000]# sudo apt-get remove xorg-driver-fglrx[/COLOR]

This gave me an output which said that [COLOR=#990000]xorg-driver-fglrx[/COLOR] was not installed and so was not removed.

Assuming/hoping that this meant that i was already past the first step i tried:

[COLOR=#990000]# sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR]

This didn't seem to do much and just gave me a new prompt line.

So i exited and rebooted, and Ubuntu came up. 

I am not sure if i have done something horrendous that will only be revealed to me in the future. That said if what i have done works and i see no more blank screens over the next week i'll come back and mark this thread as solved, posting the link with amended instructions.

If i have done something terrible that i should know about a heads up would be great.

p.s. in my first post on this thread i wrote:
> Finally i found this post ([http://georgia.ubuntuforums.org/show....php?p=8903558]("http://georgia.ubuntuforums.org/showthread.php?p=8903558")) which remains unsolved. This seems most clearly to describe the problem that i am having. That link was wrong, it was meant to be: [http://ubuntuforums.org/showthread.php?t=1430137](http://ubuntuforums.org/showthread.php?t=1430137)

---

### Post by quixote on 2010-04-21
Hey, whatever works! :D

Presumably, with an ATI card, you need fglrx?  Not at all sure on this.  So the fact that deleting it improved things suggests you had the wrong one, or it was corrupted, or something.  Or maybe the phigh command fixed important things.  I believe when you get no error messages with that one, it worked.  Unix / linux command line is very low on reassurance.

What may happen if you don't have the best driver for your card is that the graphics performance will be deficient in some way.  Compiz won't work, or you get fewer colors or resolution than you could.  If it works for you, though, that doesn't matter.  This isn't one of those things that gradually degrades the system.  If it wasn't going to work, it's obvious up front with a blank screen.

---

### Post by MorrisseyJ on 2010-04-21
[COLOR=Black]Yes, from all over the internet it seems like the "sudo [/COLOR][COLOR=#990000][COLOR=Black]dpkg-reconfigure -phigh xserver-xorg" command is very useful.

From what i was able to read ([https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)) 9.10 now has an open source driver which runs some ATI cards out of the box. So you have no need for the proprietary fglrx driver. They say that you can use fglrx as its a little faster, but on other pages i see that they suggest going for the open source option as support is no longer available from ATI. 

[/COLOR][/COLOR]> This guide will show you how to use the Free, Open Source driver for many ATI graphics cards called "radeon" or "ati". It will provide 2D and 3D acceleration in your video hardware. This driver is not as fast as the closed-source, proprietary "fglrx" driver from AMD/ATI Inc. for some cards, but has better dual-head support, and supports some older chipsets that fglrx does not.([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver))

Since i am using an ATI Radeon Xpress 200M card i think that Ubuntu just went out of the box with its open source driver. This explains why i didn't have fglrx installed. Hopefully the praiseworthy [COLOR=Black]"sudo [/COLOR][COLOR=#990000][COLOR=Black]dpkg-reconfigure -phigh xserver-xorg" command [/COLOR][/COLOR]has fixed my problems.

With all this in mind i think that Compiz is behaving strangely. I say 'i think' its behaving strangely because i only just pulled it down and started playing with it last night - what trying to fix a graphics issue will teach you. 

Even if i can't get compiz to work I feel like i am happy to have small things not working if they are because of proprietary issues, as opposed to Ubuntu not working. In the case of the latter i am now a convert with the only thing still giving me issues being my microphone volume. 

Anyway, thanks for the input. I'll mark this as solved if, in a couple of days i have no more problems.

---

### Post by klemes on 2010-04-21
For a solution about your card regarding Compiz have a look here:

[http://wiki.compiz.org/Hardware/ATI](http://wiki.compiz.org/Hardware/ATI)

---

### Post by Mic[RSA] on 2010-04-21
Hi, I'm new here :) Also new to ubuntu/linux. Been using it for less than a week, and have had a nice learning curve thus far. But now! HORROR! My laptop gave me a blank screen (with a strange dark line a 3rd of the way up :confused: )

I have read some posts in this topic, but I'm wondering if the author and I have the same problem. Firstly, I got this screen this morning after restarting my system to see if the nVidia driver worked. But before that I also downloaded and installed a few other things: Netbeans and some other application, can't remember its name right now. But back to the driver, do you think it is the nVidia driver that is causing it or is it the laptop (DELL but hasn't given me any hassle since I installed ubuntu and has actually never run better [No over heating :D])

If this is the source of the blank screen, should I also follow these instructions [from the first post]("http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html")?

Thank you in advance :)

---

### Post by Mic[RSA] on 2010-04-21
Tried the commands listed [here]("http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html")

> 1. Select recovery mode from the boot menu.
2. Select login as root from the menu in recovery mode.
3. Type this at the prompt
# sudo apt-get remove xorg-driver-fglrx
# sudo dpkg-reconfigure -phigh xserver-xorg
4. Exit
# exit
5. Now select Resume normal boot from the menu.

It doesn't work :(

But:
The code: > # sudo dpkg-reconfigure -phigh xserver-xorg gave me a reply that no such code exists...

---

### Post by klemes on 2010-04-21
Your problem cannot be solved with the above because although yours seems to be also a graphics card setup problem you have an NVIDIA card but the other user had an ATI card.
You do not describe how you installed the proprietary nvidia grahics(did you downloaded any packages from nvidia-website,did you installed using apt-get/aptitude/Synaptic?also what exactly type of card and the name of the driver would also be good to know before you do anything else).
If you want to quickly access your desktop environment edit the xorg.conf file and edit the line that says Driver from "nvidia" to just "nv".This way you will disable the proprietary driver and use the open source driver instaed which obviously was working for you and we proceed from then on.
To edit your xorg.conf file login in a terminal(CTRL+Alt+F2) and type :
sudo nano /etc/X11/xorg.conf
In the improbable event that there is not an xorg.conf file in the above location report back and I will tell what we can do to overcome this.....

---

### Post by MorrisseyJ on 2010-04-21
Mic [RSA]: You might want to have a look at the dell relevant link:

[http://georgia.ubuntuforums.org/showthread.php?p=8903558](http://georgia.ubuntuforums.org/showthread.php?p=8903558)

Otherwise Klemes is right, different hardware means the solution won't be the same.

That said, lots of people have reported success with the "# sudo dpkg-reconfigure -phigh xserver-xorg" 			 		command. I think that it resets something. 

Note that when i ran it, it ran from the recovery mode and not simply from the terminal. You should be able to access recovery mode from the GRUB menu. 

One more thing when running this command - which you won't be able to paste into the command line in recovery mode - remember to put a space before "-phigh" and before "xserver-xorg".

Otherwise, being new to Linux i don't know what to suggest. Hopefully klemes can help.

Klemes: Thanks for the link about compiz stuff, much appreciated.

p.s. no problems yet with starting to a blank screen

---

### Post by Mic[RSA] on 2010-04-21
> One more thing when running this command - which you won't be able to paste into the command line in recovery mode - remember to put a space before "-phigh" and before "xserver-xorg".

when at first it didn't register the command I did go back and look at the spacing and repeated it. Still didn't work


@klemes: How will I access my desktop if I get the blank screen :/ Or am I just misinterpreting you?
Also, I can't remember exactly how I did it. But it wasn't via synaptic but another program... also a system program.

---

### Post by MorrisseyJ on 2010-04-21
Ok, i am not sure about this but maybe something in here will help:

[http://ubuntuforums.org/archive/index.php/t-322379.html](http://ubuntuforums.org/archive/index.php/t-322379.html)

> johnnyw
December 20th, 2006, 06:52 PM

First of all thanks for being so quick and nice with your answer :-D.

a)Some guys from other forums told me to try with these :

1-sudo dpkg-reconfigure xserver-xorg

and got as an answer:

broken or not fully installed

2-sudo /usr/bin/system-config-display

and got as an answer: 

command does not exist
> aysiu
December 20th, 2006, 06:54 PM

Then definitely try this command first: sudo aptitude update && sudo aptitude install ubuntu-desktop That will make sure you have all the necessary components installed.

 

Maybe your xorg hasn't installed. Possibly you need to do the sudo aptitude update and sudo aptitude install ubuntu-desktop. 

I have to admit though that i don't really know what i am talking about here so google any of the commands before you run them.

---

### Post by Mic[RSA] on 2010-04-21
will do

I should start in recovery mode right? from there I should insert these commands into the root?

---

### Post by klemes on 2010-04-21
> **'Mic[RSA] said:**
> when at first it didn't register the command I did go back and look at the spacing and repeated it. Still didn't work


@klemes: How will I access my desktop if I get the blank screen :/ Or am I just misinterpreting you?
Also, I can't remember exactly how I did it. But it wasn't via synaptic but another program... also a system program.


Look from what I gathered you installed the restricted drivers through Hardware Restricted Drivers program and for some reason that did not work.
To edit your xorg.conf boot you simply boot in recovery mode OR as I told you log into a terminal by pressing CTRL+Alt+F2 ,if you are able to access one,and you should be if it's only a nvidia driver's error,which it only seems to be.So based on this assumption IF you are able to edit your xorg.conf the way I told you in the previous post you can switch drivers and get your precious desktop back...That's all...

---

### Post by Mic[RSA] on 2010-04-21
So far, so good, I changed the nvidia to nv after I successfully remembered my user name. Now... how do I exit the prompt :redface:

---

### Post by klemes on 2010-04-21
```
sudo reboot
```in order to reboot .
You can also try CTRL+D to continue booting but maybe better reboot the computer.:guitar:

I assume you closed and saved your xorg.conf file from the nano editor......

In case you did not and that is what you are asking for and I 've missed it:

CTRL+X followed by 'y' at the question if it should save the file and then ENTER.

P.S.>You must have figured how to save the xorg.conf  yourself but still it's better to write that too in case you missed that.....

---

### Post by Mic[RSA] on 2010-04-21
No I mean, I'm in nano /etc/X11/xorg.conf and I want to save the change... Do I even make sense :?

---

### Post by Mic[RSA] on 2010-04-21
> **klemes said:**
> 
CTRL+X followed by 'y' at the question if it should save the file and then ENTER.

P.S.>You must have figured how to save the xorg.conf  yourself but still it's better to write that too in case you missed that.....

Thanks :)

P.S. are you insulting my problem solving capabilities! :P

P.P.S. IT WORKS!! *fists in air*

---

### Post by MorrisseyJ on 2010-04-21
Glad to hear that it all worked out. Enjoy.

---

### Post by MorrisseyJ on 2010-04-26
Problem appears to be solved. 

My guess is that it w[COLOR=Black]as the "[/COLOR][COLOR=#990000][COLOR=Black]# sudo dpkg-reconfigure -phigh xserver-xorg" [/COLOR][COLOR=Black]command run from recovery mode.[/COLOR]
[/COLOR]

---

