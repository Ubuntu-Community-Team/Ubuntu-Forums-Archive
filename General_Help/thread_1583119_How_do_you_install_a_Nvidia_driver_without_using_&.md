---
title: "How do you install a Nvidia driver without using &quot;Hardware Drivers&quot; option?"
date: 2010-09-27
forum: General Help
---

### Post by Pulpish on 2010-09-27
Hello, I want to install the driver manually since its not "Hardware Drivers" list when I choose to install. I just want step by step help. Last time I tried doing it I was dual booted under Vista and I killed my Ubuntu partition somehow. I formatted today and I'm under Ubuntu so I really don't want to screw up again haha! :D I downloaded the drivers and its sitting in "Downloads" waiting for a reply! :D Thanks. Oh and the reason I screwed up was cuz another forum told me I had to uninstall some other graphic driver that was there by default and I couldn't get a GUI back and didn't know how to reinstall it :S I am a Linux noob, not familiar with the command terminal.

---

### Post by oldos2er on 2010-09-27
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by Cavsfan on 2010-09-27
See this post and then there is some more stuff you need to do, so look at the thread.
You need to setup a script that will execute when a new kernel is installed. I got a new kernel this morning and mine went flawlessly!

_[http://ubuntuforums.org/showpost.php?p=9817226&postcount=7](http://ubuntuforums.org/showpost.php?p=9817226&postcount=7)_

---

### Post by Pulpish on 2010-09-27
> **Cavsfan said:**
> See this post and then there is some more stuff you need to do, so look at the thread.
You need to setup a script that will execute when a new kernel is installed. I got a new kernel this morning and mine went flawlessly!

_[http://ubuntuforums.org/showpost.php?p=9817226&postcount=7](http://ubuntuforums.org/showpost.php?p=9817226&postcount=7)_

Thanks thats exactly what I'm trying to do! I'm just afraid to mess up though :/
Is the kernel part necessary? lol

---

### Post by Cavsfan on 2010-09-27
A while after I installed version 256.53 (185 is the latest in the repos), 
it somehow went to 260.19.06 and that is even higher than nVidia's download for Linux!
It went to that version with an update to Ubuntu!

---

### Post by Pulpish on 2010-09-27
> **Cavsfan said:**
> A while after I installed version 256.53 (185 is the latest in the repos), 
it somehow went to 260.19.06 and that is even higher than nVidia's download for Linux!
It went to that version with an update to Ubuntu!

Oh cool :O then i'll go ahead and figure it out xD ^_^.. did you also go after installing the driver because pictures and videos werent too clear?

---

### Post by Cavsfan on 2010-09-27
> **Pulpish said:**
> Thanks thats exactly what I'm trying to do! I'm just afraid to mess up though :/
Is the kernel part necessary? lol

Yes, mine took care of itself. When the kernel was installed today 2.6.32-25-generic, the kernel was compiled via the script I was told to add.
It said it got an error, but when I looked at the error log, all was fine.
And it is amazing the graphics with the latest driver.

---

### Post by Cavsfan on 2010-09-27
> **Pulpish said:**
> Oh cool :O then i'll go ahead and figure it out xD ^_^.. did you also go after installing the driver because pictures and videos werent too clear?

Post #15 on that thread points to the script you need to add. And it is smoking!

---

### Post by Pulpish on 2010-09-27
> **Cavsfan said:**
> Yes, mine took care of itself. When the kernel was installed today 2.6.32-25-generic, the kernel was compiled via the script I was told to add.
It said it got an error, but when I looked at the error log, all was fine.
And it is amazing the graphics with the latest driver.

Alright, well i'm following the instructions from the link you sent me, where can I find the script though? :S
Edit: my bad just saw your post :P
Edit2: the link showed only your post I was confused haha

---

### Post by Cavsfan on 2010-09-27
> **Pulpish said:**
> Alright, well i'm following the instructions from the link you sent me, where can I find the script though? :S

See the post above yours...

---

### Post by philinux on 2010-09-27
> **Pulpish said:**
> Alright, well i'm following the instructions from the link you sent me, where can I find the script though? :S
Edit: my bad just saw your post :P
Edit2: the link showed only your post I was confused haha

You never mentioned which graphics card you have.

---

### Post by Pulpish on 2010-09-27
> **Cavsfan said:**
> See the post above yours...

Getting this error while trying to install:
ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Pulpish on 2010-09-27
> **philinux said:**
> You never mentioned which graphics card you have.

Lol i have Nvidia 9600M GT

---

### Post by philinux on 2010-09-27
> **Pulpish said:**
> Lol i have Nvidia 9600M GT

That should get installed/show up in Hardware drivers then.

Have you updated your system?

```
sudo apt-get update && sudo apt-get upgrade
```

Then check Hardware Drivers.

---

### Post by Pulpish on 2010-09-27
> **philinux said:**
> That should get installed/show up in Hardware drivers then.

Have you updated your system?

```
sudo apt-get update && sudo apt-get upgrade
```

Then check Hardware Drivers.

I'm trying to get the latest version installed like Cavsfan mentioned.
I tried > sudo apt-get update && sudo apt-get upgrade and now I keep getting "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

---

### Post by philinux on 2010-09-27
> **Pulpish said:**
> I'm trying to get the latest version installed like Cavsfan mentioned.
I tried  and now I keep getting "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Thats because you have either synaptic or other open. 

If a new kernel comes along you will have to do the manual install again by going down this route.

---

### Post by Cavsfan on 2010-09-27
> **philinux said:**
> Thats because you have either synaptic or other open. 

If a new kernel comes along you will have to do the manual install again by going down this route.

I have an nVidia GeForce 9800 GT and have installed version 260.19.06 and this morning when I got the new kernel,
I didn't have to do anything! I had added the script that was suggested in the thread I mentioned. But that was for a later version that I am using.
But, It compiled the kernel and I didn't have to do anything! I was amazed! So, something has changed.

---

### Post by Cavsfan on 2010-09-27
You have to kill the x server and the key sequence to do so is disabled by default.
Here is how to enable it and kill the x server:

[LIST]
[*]Select "System"->"Preferences"->"Keyboard"
[*]Select the "Layouts" tab and click on the "Layout Options" button.
[*]Select "Key sequence to kill the X server" and enable "Control + Alt + Backspace".
[/LIST]
Then you can kill it by pressing the above key sequence. It will be restarted upon system restart after you have updated the driver.

PS Please don't PM me, just reply to this thread.

---

### Post by philinux on 2010-09-27
> **Cavsfan said:**
> I have an nVidia GeForce 9800 GT and have installed version 260.19.06 and this morning when I got the new kernel,
I didn't have to do anything! I had added the script that was suggested in the thread I mentioned. But that was for a later version that I am using.
But, It compiled the kernel and I didn't have to do anything! I was amazed! So, something has changed.

Well thats a step in the right direction for a change. :P

---

### Post by Pulpish on 2010-09-27
> **Cavsfan said:**
> You have to kill the x server and the key sequence to do so is disabled by default.
Here is how to enable it and kill the x server:

[LIST]
[*]Select "System"->"Preferences"->"Keyboard"
[*]Select the "Layouts" tab and click on the "Layout Options" button.
[*]Select "Key sequence to kill the X server" and enable "Control + Alt + Backspace".
[/LIST]
Then you can kill it by pressing the above key sequence. It will be restarted upon system restart after you have updated the driver.

PS Please don't PM me, just reply to this thread.

Thanks a lot. Right, so I killed the X server, then I tried installing. This thing called nouveau conflicted and Nvidia asked if it should attempt to kill it, I selected yes, and then it failed :S
Edit: btw i'm killing the x server using ```
sudo /etc/init.d/gdm stop
``` alt+ctrl+bkspce is just restarting the x server and logging me out

---

### Post by Cavsfan on 2010-09-27
> **philinux said:**
> Well thats a step in the right direction for a change. :P

Yes, it is indeed! I was happy to see that! :P

> **Pulpish said:**
> Thanks a lot. Right, so I killed the X server, then I tried installing. This thing called nouveau conflicted and Nvidia asked if it should attempt to kill it, I selected yes, and then it failed :S
Edit: btw i'm killing the x server using ```
sudo /etc/init.d/gdm stop
``` alt+ctrl+bkspce is just restarting the x server and logging me out

Did you have the regular driver from System > Administration > Hardware Drivers installed prior to doing this?
I didn't have anything come up about nouveau when I installed mine.

---

### Post by Cavsfan on 2010-09-27
Did you go by these instructions after downloading the driver:

[COLOR=Blue][http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)[/COLOR]

EDIT Step 4 I had to write down as you have to reboot and do some special stuff.

---

### Post by Pulpish on 2010-09-28
> **Cavsfan said:**
> Did you go by these instructions after downloading the driver:

[COLOR=Blue][http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)[/COLOR]

EDIT Step 4 I had to write down as you have to reboot and do some special stuff.

Hey cavsfan, sorry i kinda killed my PC after the X server killed nouveau yesterday.. had to boot up from CD drive and reinstall ubuntu.. was weird, the caps lock LED was blinking and I couldnt get any interface at all, just a blank screen, not even command terminal.. I'm working on it again now.. I'm just updating everything on my PC first.. Thanks for helping me bro, I owe ya

---

### Post by Cavsfan on 2010-09-28
> **Pulpish said:**
> Hey cavsfan, sorry i kinda killed my PC after the X server killed nouveau yesterday.. had to boot up from CD drive and reinstall ubuntu.. was weird, the caps lock LED was blinking and I couldnt get any interface at all, just a blank screen, not even command terminal.. I'm working on it again now.. I'm just updating everything on my PC first.. Thanks for helping me bro, I owe ya

You are welcome! Sorry that that happened to you! Once you get the latest nVidea drivers working, you'll be amazed!
Like I said be sure and write down step 4 as you have to do that during a reboot. And make sure you add the script
so that the driver gets rebuilt into the kernel.

I am kind of perplexed that I installed the latest driver from nVidia 256.53 but, System > Preferences NVIDA X Server 
Settings shows version 260.19.06! Don't ask me how that happened! But it is awesome! I have Compiz and Cairo-Dock 
and Emerald WM and I have it set to "burn" when I open or close an app. and I cannot get over the realism! I close FF 
and the screen burns with smoke! Sweet!

---

### Post by Pulpish on 2010-09-28
> **Cavsfan said:**
> You are welcome! Sorry that that happened to you! Once you get the latest nVidea drivers working, you'll be amazed!
Like I said be sure and write down step 4 as you have to do that during a reboot. And make sure you add the script
so that the driver gets rebuilt into the kernel.

I am kind of perplexed that I installed the latest driver from nVidia 256.53 but, System > Preferences NVIDA X Server 
Settings shows version 260.19.06! Don't ask me how that happened! But it is awesome! I have Compiz and Cairo-Dock 
and Emerald WM and I have it set to "burn" when I open or close an app. and I cannot get over the realism! I close FF 
and the screen burns with smoke! Sweet!

WOOO! I GOT IT RUNNING!!! THANK YOU THANK YOU THANK YOU THIS IS AMAZING! haha mine shows 256.53 though! :D How lucky I must have been that you saw my thread rofl I would be doing that long and boring Nvidia guide right now :P

---

### Post by Cavsfan on 2010-09-28
Fantastic! Did you create that script called "update-nvidia"? If so you should be good to go!

---

### Post by Pulpish on 2010-09-28
> **Cavsfan said:**
> Fantastic! Did you create that script called "update-nvidia"? If so you should be good to go!

Yeah I created it haha, I ran the commands but there was no response indicating it worked.. Script or not, I'm new to Ubuntu and still the graphics are nice but I just hit youtube and the quality is quite terrible :S.. I guess that's how it is :P Well thanks for your help :D

---

### Post by Cavsfan on 2010-09-28
Youtube works great for me. Check your Java version [[COLOR=blue]_here_[/COLOR]]("http://www.adobe.com/software/flash/about/").

---

