---
title: "Help with wireless connection!"
date: 2010-05-09
forum: General Help
---

### Post by LUCIDementia on 2010-05-09
I am a long time Windows user and hater. I am brand new to Ubuntu and am having a really hard time trying to get my wireless card working. I've already read several other threads, but I am so incredibly confused now that I think it's time I ask for help.

I don't know much about computers, so if you ask for me to put in a command prompt I'll just give you the entire output because I never know what I should be looking for.

And if you need some hardware specs, please tell me how to find it. Again, in Windows I've never had to worry about that so I've never learned how.

For now I can say that I am on a[COLOR=DarkRed] Dell Vostro 1500[/COLOR] and under "Wireless Networks" it says "disconnected". Please help!

~lucid

---

### Post by LUCIDementia on 2010-05-10
No one is willing to help?

I've tried every tutorial I can find that is even close to my problem but for all I know I'm just making things worse. I don't know anything about programming so you guys are really my only hope.

---

### Post by fwin on 2010-05-10
Hi there, I am not a linux expert but I've had some issues with my wireless connections a few times, so let's see if I can help.

-First of all do you see available connections when you click on the wireless network connection icon?

- if not, have you tried to enable wireless connections by right clicking on the icon and then choosing "enable wireless"

-also does your laptop have a switch to turn on the network adapter, if it does, did you turn it on?

---

### Post by Shakz on 2010-05-10
> **fwin said:**
> 
-also does your laptop have a switch to turn on the network adapter, if it does, did you turn it on?

I hate those stupid buttons. I am sure they have a use...but I have not found it myself. 

That might be your problem though Lucid. 

For me I had an issue witht he driver. It worked when I booted up on the CD but afterwards it wouldnt work when I actually loaded ubuntu. I have a dell also (XPS 15 somethingoranother)

I had to go to System > Administration > Software Sources
There at the bottom I had to click the Cdrom wtih Ubuntu at the bottom. 

After that it does a reload. 

Then go to System > Administration > Hardware Drivers 

It should search your system. If you have the same wireless card as me a broadcom wireless card will come up as an option. Active it...reboot after it installs (sometimes this isnt needed) and you should be able to left click on the wireless icon/select your network. 

Hope this helps you....

---

### Post by LUCIDementia on 2010-05-10
I can see available wireless networks thanks to one of the several tutorials I went through, but so far I am still unable to connect.

I know that my wireless card, **[COLOR=DarkRed]Broadcom BCM4312 (rev 01)[/COLOR]**, is not supported by Linux so I need to use that wrapper program. I installed it, and one driver, but so far still no luck.

I also tried something that involved unzipping a file. Honestly I can't get any more specific than that. It looked promising but I'm pretty sure if failed. At least I assume so, cause all that mumbo-jumbo on the Terminal didn't look promising and the wireless doesn't work.

I'm happy to give any information you need, and I apologize if it takes me a while to respond but until I have wireless up and running this is going to be a difficult process.

Thanks everyone! I fully suspect that Ubuntu will live up to its reputation if I can get through this first step :)

~lucid

---

### Post by LUCIDementia on 2010-05-10
> **fwin said:**
> -also does your laptop have a switch to turn on the network adapter, if it does, did you turn it on?

I found a switch for the wireless. It doesn't have an off position because it resets to the same place after I pull it. But I pulled it anyway and nothing happened.
Then I tried pushing the tiny button next to it with a pen, which I can only guess is to reset the wireless card but that didn't do anything either. My only guess is that Ubuntu doesn't recognize that part of my hardware. Thanks anyways, fwin. I wish it was something that simple.

-lucid

---

### Post by fwin on 2010-05-10
When I had a similar problem, I was also able to see available networks but i could not connect to anything and then I tried this:

[http://www.katonda.com/expert-speaks...buntu/917/2010]("http://www.katonda.com/expert-speaks/troubleshooting-wi-fi-issues-ubuntu/917/2010")


after that i restarted my computer and i was able to connect to the network, try it and let us know what happens.

---

### Post by fwin on 2010-05-10
Is this how you set up your hardware (if not, you may want to try it):

[http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm4312](http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm4312)

Here is another link that may be useful: 

[http://ubuntuforums.org/showthread.php?t=1056446](http://ubuntuforums.org/showthread.php?t=1056446)

and this one too:

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

### Post by LUCIDementia on 2010-05-10
I can't be sure if what I tried worked. There is a response to everything I put in but I don't know if it's good or not.  So, basic question:
When it gives you multiple lines to put in as commands, do you paste it all in at once? I tried typing them out manually but I don't know how to make it go down a line without entering the line I already typed.
Anyways, it says it installed a driver but my Hardware Drivers hasn't detected anything new. If the end result is getting "Broadcom STA wireless driver" then I already have it. But if that isn't working then I don't know what else to try.

I'm starting not to trust the website. How realistic is it for someone who doesn't know programing to use this OS? Maybe I should have stuck with windows after all

---

### Post by eltonw on 2010-05-10
A *search* in the **NETWORKING** forum brought up this link:
[http://ubuntuforums.org/showpost.php...22&postcount=4](http://ubuntuforums.org/showpost.php...22&postcount=4)

Perhaps this is your solution.

HTH...

---

### Post by fwin on 2010-05-10
Have to tried to go to: system-->administration-->"Hardware drivers" and activate the driver shown in that window?

---

### Post by LUCIDementia on 2010-05-10
> **eltonw said:**
> A *search* in the **NETWORKING** forum brought up this link:
[http://ubuntuforums.org/showpost.php...22&postcount=4](http://ubuntuforums.org/showpost.php...22&postcount=4)

Not sure what you saw when you copied that link but when I click it I see a link to every main page of the Ubuntu forum.

I've tried every tutorial I've come across, but every step along the way things pop up that I cannot understand, so I really don't know what impact I'm having on my computer.
Is there some command that we can run to understand my computer more and get a better diagnosis as to why I can detect internet but not use it?  All this stabbing in the dark has me so frustrated I feel like smashing my laptop with the first heavy thing I can get my hands on.
More specifically, the lamp.

Or, if anyone in the LaCrosse, Wisconsin area wants to make some money I would gladly pay $20/hour for someone to do this for me. I'm so sick of this computer jargon I could die.

---

### Post by LUCIDementia on 2010-05-10
> **fwin said:**
> Have to tried to go to: system-->administration-->"Hardware drivers" and activate the driver shown in that window?
Yep.  I have a Broadcom STA wireless driver and it is active. Getting that is what allowed me to start seeing networks, but still not able to use them.

---

### Post by fwin on 2010-05-10
if you want to pay someone to help you with this, it may be easier, better and cheaper if you purchase some professional ubuntu support from the official website:

[http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)

[https://forms.canonical.com/sales/](https://forms.canonical.com/sales/)

i think $60  can get you support for 1 year, that is better than paying 20 dollars/hr

---

### Post by fwin on 2010-05-10
Did you try this:

> **fwin said:**
> When I had a similar problem, I was also able to see available networks but i could not connect to anything and then I tried this:

[http://www.katonda.com/expert-speaks...buntu/917/2010]("http://www.katonda.com/expert-speaks/troubleshooting-wi-fi-issues-ubuntu/917/2010")


after that i restarted my computer and i was able to connect to the network, try it and let us know what happens.

---

### Post by bredman on 2010-05-11
In general, the best method to use BCM43xx wireless is to use the program b43-fwcutter which loads the official Broadcom firmware into your hardware. Have you tried this?

See [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43), especially the following part

**Ubuntu/Debian**

 In recent versions of Ubuntu and  Debian, installing the b43-fwcutter package will handle everything for  you: 

 []("http://wireless.kernel.org/en/users/Drivers/b43#")    sudo apt-get install b43-fwcutter


You will be asked  to automatically fetch and install the firmware into the right  location.

---

### Post by brethren on 2010-05-11
so you've activated the hardware driver and you can now see available wireless networks, right. what happens when you select your network from the dropdown list and enter your wireless password?

---

### Post by LUCIDementia on 2010-05-11
> **bredman said:**
> In general, the best method to use BCM43xx wireless is to use the program b43-fwcutter which loads the official Broadcom firmware into your hardware. Have you tried this?

See [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43), especially the following part

I tried the command you sent, and it all seemed to run just fine but it didn't solve the problem. I'm not even sure if my card is supported. The link states that 14e4:4315 is supported 2.6.32 and later, whatever that means. But it also states that 801.11a part of the 4312 chip is not supported, and I have Broadcom Corporation BCM4312 802.11b/g.

Or, after I install is there something else I need to do to activate it?

---

### Post by LUCIDementia on 2010-05-11
> **fwin said:**
> When I had a similar problem, I was also able to see available networks but i could not connect to anything and then I tried this:

[http://www.katonda.com/expert-speaks...buntu/917/2010]("http://www.katonda.com/expert-speaks/troubleshooting-wi-fi-issues-ubuntu/917/2010")


after that i restarted my computer and i was able to connect to the network, try it and let us know what happens.

I have tried this, but not successfully. I found the package it told me to download, so I did, but then it says to open the files sequentially in a listed order, but my package only had one ".deb" file that didn't match any of the ones listed.

I was tempted just to open it and see what happens, but it says to copy to something like a USB drive, but didn't say why. Since I don't have one and don't know how important this step is it makes me wary.
And to top things off, the site states "strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/karmic/aptitude") or [synaptic]("http://packages.ubuntu.com/karmic/synaptic") to  download and install packages, instead of doing so manually via this  website."  Since I have no idea what that means, the downloaded file is still sitting in my folder untouched.

EDIT: I feel like I'm running out of options so I went ahead and opened the file. Turns out I was wary for nothing because it just extracted and installed. But, after a restart, I'm still right where I was :-/

---

### Post by LUCIDementia on 2010-05-11
> **brethren said:**
> so you've activated the hardware driver and you can now see available wireless networks, right. what happens when you select your network from the dropdown list and enter your wireless password?

The icon spins for about 20-30 seconds, then I get a notification saying"

**Wireless network**
Disconnected

There's no password on this network so that step isn't part of the process.

---

### Post by fwin on 2010-05-12
> **LUCIDementia said:**
> The icon spins for about 20-30 seconds, then I get a notification saying"

**Wireless network**
Disconnected

There's no password on this network so that step isn't part of the process.


I think the signal is very weak and that's why you can't connect to the network.

1. do you have a router or this is just some open random signal from your neighborhood?

2. are there any other stronger connections?

3. How are you able to connect to the internet to post comments in this forum?. 

4. what version of ubuntu do you have ?

If you are connected to the internet (with a wired network I assume) with your ubuntu machine, you may want to try to install the packages from the link i sent you, by using "synaptic package manager" that is under system->administration->synaptic package manager. Then again look for the packages shown in this link:

[http://www.katonda.com/expert-speaks...buntu/917/2010]("http://www.katonda.com/expert-speaks/troubleshooting-wi-fi-issues-ubuntu/917/2010")

Select them (the ones for your version of ubuntu) and then apply changes.

You should install all of them not just one. Anyway it would be easier if you do it using synaptic.

---

### Post by LUCIDementia on 2010-05-12
I am currently wired directly into my modem, which also means I'm sitting right next to the router. The computer shows it having full bars while several other available wireless networks have less.  Plus, the connection worked just fine until I installed Ubuntu.

I'm not entirely sure what version I have, but I just downloaded and installed it last Friday so I'm almost positive that I have the latest version.

I have never been on synaptic package manager, so maybe this holds the key to unlocking my wireless internet. (Figuratively of course...my wireless isn't password protected) On the link you sent I didn't see any indication of different versions for different versions of Ubuntu, but the following are installed/active/whatever the green box means.

linux-image-2.6.31-19-generic     Installed version:   2.6.31-19.56
linux-image-2.6.32-21-generic     Installed version:   2.6.32-21.32
linux-image-2.6.32-22-generic     Installed version:   2.6.32-22.33
linux-image-generic                        Installed version:   2.6.32.22.23

Any possibility this is being caused because I have more than one of these? Or is that normal?
Or maybe I should just try to install every single one that starts the same way..?

---

### Post by fwin on 2010-05-12
To find out what version of ubuntu you are using go to:  system->about ubuntu. Then let me know what version you're using.
 
After that go to synaptic and copy and paste the following (let me know which one has a green box):

1. first copy and paste this one  and chek if it is installed:

linux-backports-modules-karmic-generic

2. then this one:

linux-backports-modules-wireless-karmic-generic

3. then this one:

linux-image-2.6.31-19-generic (never mind you did this one already)

4. and finally this one:

linux-backports-modules-2.6.31-19-generic


If you notice the first two have the word "karmic" which corresponds to version 9.10, if you have version 10.04 then you are not going to see them in synaptic so replace "karmic" with "lucid" and see if they show up.

 If the last one does not show up then try only the first three words and then synaptic will fill out the rest and you will see what version is available or installed. 

Let me know which ones are/aren't  shown as installed and what version they are.

Good luck!

---

### Post by fwin on 2010-05-12
> **LUCIDementia said:**
> 
linux-image-2.6.31-19-generic     Installed version:   2.6.31-19.56
linux-image-2.6.32-21-generic     Installed version:   2.6.32-21.32
linux-image-2.6.32-22-generic     Installed version:   2.6.32-22.33
linux-image-generic                        Installed version:   2.6.32.22.23

Any possibility this is being caused because I have more than one of these? Or is that normal?
Or maybe I should just try to install every single one that starts the same way..?


I don't think this is being caused because you have all of them installed, when i do this in synaptic it also shows me a lot of version installed. 

Don't try to install every single one that starts the same way, lets just proceed as explained in my previous post. I'm not an expert so I wouldn't know what would happen if you do that.

---

### Post by LUCIDementia on 2010-05-12
Okay, I followed the steps that you gave but thought that I could figure it out by installing some on my own. Turns out I moved too fast. Anyways, here's what I found out:

I am running Ubuntu 10.04

1.  I didn't find anything for **linux-backports-modules-karmic-generic **, but one with "alsa-lucid" and another with "headers-lucid" instead of "karmic" like you said.

2.  Again, I didn't find** linux-backports-modules-wireless-karmic-generic** because of my version but one with "lucid" instead of "karmic" and another with "lucid" and a "pae" at the very end of everything"

3.  Already taken care of.

4.  I also didn't find anything for linux-backports-modules-2.6.31-19-generic, but I got close. Mine was identicle except for 2.3.**32-21**  or **32.33** and either an "alsa" or a "wireless" before the numbers.

Since I obviously tried to install the wrong package (I searched for karmic) I thought I would just install these packages to see if it would work, so I checked all these boxes including the corresponding ones ending in "pae" or with the addition of the word "header". The installation failed, failed the recovery, then gave me this message:

E: /var/cache/apt/archives/linux-backports-modules-wireless-2.6.32-22-generic-pae_2.6.32-22.13_i386.deb: trying to overwrite '/lib/udev/compat_firmware_22.sh', which is also in package linux-backports-modules-wireless-2.6.32-22-generic 0

I tried restarting to see if that would help but when it booted up it said my graphics card wasn't going to function properly and I should run in low graphics mode. I restarted again and still have the crash report at the top of my screen :(

---

### Post by fwin on 2010-05-12
I think I know how to solve this. When it asks you to run in low graphics mode there should be another option called "recovery mode" or "fix broken packages" Choose that one and  it will fix this mess, I hope!. 

**Before you do any of that please back up your data (pictrures, music, etc..), just in case you need to reinstall ubuntu**. 

Once you fix this we will continue with the wireless connection, what do you think?.

---

### Post by LUCIDementia on 2010-05-12
> **fwin said:**
> I think I know how to solve this. When it asks you to run in low graphics mode there should be another option called "recovery mode" or "fix broken packages" Choose that one and  it will fix this mess, I hope!. 

One of the options was restart, which I did and it brought me to my desktop almost instantly. And as for backing up, I only installed this on Friday and haven't even put my information on here yet, so right now anything can happen and it wouldn't really bother me. I just want it to work.

---

### Post by fwin on 2010-05-12
When you restart you computer, do you see a black screen ("grub") that shows you the version of ubuntu that you're using? If you see it, there should be another option called recovery mode or something like that. If you still want to fix the problem with the graphics card choose the recovery mode option and that will take you to a menu where you can choose "fix broken packages" or something like that, choose that and hit enter and it will try to fix it.

Now, back to the wireless problem. 

*For case 4 i would install the one ending with numbers .[B]32-21

[/B]*For case 2install the one with "lucid" only, forget about the "pae" one.

*For case 1 I honestly don't know what to tell you, there should be one with "lucid" like this: 
linux-backports-modules-**lucid**-generic

Are you sure there isn't anything like this in synaptic?

---

### Post by LUCIDementia on 2010-05-15
I feel like this whole situation is hopeless. I keep trying combinations of these drivers, but without knowing what any of them do or mean I really don't know if I'm getting any closer. I guess the ones with different numbers are compatible to activate at the same time but other things are not. I wish I at least knew what pae was

Also, there is no other way to contact customer support other than email. Which I have done twice, but still have not heard back and it's been about a week now (since you first told me about it)

Is there *any *other way? I'm desperate and beyond the point of believing that I could possibly learn what all of this means just by tinkering with it.

---

### Post by fwin on 2010-05-16
I don't really know what else to do. Lets see if this works, try the following commands in a terminal:

first find what interface  you have by using this command:

**iwconfig**

then replace the question marks on the following commands with the name of your interface.


**sudo ifconfig ? down**


and then:


**sudo ifconfig ? up**

and then try to connect to the wireless network again.

---

### Post by LUCIDementia on 2010-05-16
> **fwin said:**
> then replace the question marks on the following commands with the name of your interface
What is an interface and how do I find out the name of mine?

---

### Post by fwin on 2010-05-18
Here is the output of iwconfig in my computer and the interface for the wireless network is in my case ra0

lo        no wireless extensions.

eth0      no wireless extensions.

**ra0 **      xxxxx Wireless  ESSID:"xxxxxxxxxxx"  Nickname:"xxxxxxxxxxxxx"
          Mode:Managed  Frequency=2.412 GHz  Access Point: xxxxxxx  
          Bit Rate=18 Mb/s   RTS thrff   Fragment thrff
          Link Quality=77/100  Signal level:-84 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So i would do the following:

**sudo ifconfig ra0 down**

then

**sudo ifconfig ra0 up**

---

