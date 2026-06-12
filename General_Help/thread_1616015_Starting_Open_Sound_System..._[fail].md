---
title: "Starting Open Sound System... [fail]"
date: 2010-11-07
forum: General Help
---

### Post by Furi on 2010-11-07
I had updated a good 20 hours before I rebooted. Since it stopped in the middle of the boot, I rebooted again to the same thing. I've tried using older versions I have, and recovery mode, but still to no avail. What can I do about this?

[COLOR=Red]**@@@ NEWER INFO @@@**
[COLOR=Black]It is **NOT** OSS acting up that is stopping my booting. **NOT NOT NOT**. Booted up after removing OSS. It's the same f---ing problem, minus the OSS part.
```

 * Setting console screen modes and fonts

^[[12;2R
```It IS the "console screen modes and fonts" configuration file. I'd like this laptop fixed.
[/COLOR][/COLOR]

---

### Post by Furi on 2010-11-07
Bump.

---

### Post by Furi on 2010-11-07
Bump, again...

---

### Post by Furi on 2010-11-07
How do I change the title of the thread in the list? I tried changing the post title, but that didn't work...

---

### Post by corrytonapple on 2010-11-07
First, only bump once per 24/36 hours. Second, if the OSS sound system is not starting, go to the Terminal and type:
```

sudo soundoff

```
and then:
```

sudo soundon

```
That will turn off and then back on OSS. Post back if it works. Also, did it work before the update?

---

### Post by Furi on 2010-11-07
> **corrytonapple said:**
> First, only bump once per 24/36 hours. Second, if the OSS sound system is not starting, go to the Terminal and type:
```

sudo soundoff

```and then:
```

sudo soundon

```That will turn off and then back on OSS. Post back if it works. Also, did it work before the update?
First of all, sorry about that. I kinda spend my life on this laptop and I can't live without it.
Second, yes. Completely worked. Will try the code, but where do I put it down? In a tty? I can only access one when it gets the "Starting TiMidity++ ALSA midi emulation..." error, and luckily enough, I got it this time. Should I try it on one, though?

EDIT: Must add that on both errors the boot does *not* continue. It stops completely.

EDIT2: **Tried it in a tty. It says that the command wasn't found.**

---

### Post by corrytonapple on 2010-11-07
If it stops in the middle of the boot, then something else may be wrong. But first, if it does boot you would go to the Terminal by going to **Applications>Accessories>Terminal**. Then try those commands.

---

### Post by Furi on 2010-11-07
> **corrytonapple said:**
> If it stops in the middle of the boot, then something else may be wrong. But first, if it does boot you would go to the Terminal by going to **Applications>Accessories>Terminal**. Then try those commands.

But that's the thing. I *can't* finish the boot because of this. It's like
```
 * Starting Open Sound System:            [[COLOR=Red]fail[COLOR=Black]]
 * Setting console screen modes and fonts[/COLOR][/COLOR]
```[COLOR=Red][COLOR=Black]then it just stops.
[/COLOR][/COLOR]

---

### Post by corrytonapple on 2010-11-07
What variables are you using to get the second code result? I am sorry, I did not read your post right. 
The next solution I would think is to boot from your Live CD/USB, and then uninstall and reinstall OSS.

---

### Post by Furi on 2010-11-07
> **corrytonapple said:**
> What variables are you using to get the second code result? I am sorry, I did not read your post right. 
The next solution I would think is to boot from your Live CD/USB, and then uninstall and reinstall OSS.
What I don't get about that solution is I don't know how to mount my HDD to it, so I'm left with all the defaults. After I figure that out (or you help) would I just look it up on Synaptic? Or would it be more simpler doing it on terminal, like...```
sudo apt-get remove oss
sudo apt-get install oss
```I don't know the package's name though.

EDIT: Also, I'm using an Xubuntu disc, because I can't find the Ubuntu one I used. I don't think there will be any difference, but I need a heads-up just in case.

---

### Post by corrytonapple on 2010-11-07
Yes, I believe that is the code for uninstalling and reinstalling OSS. Just try that from the Live CD/USB. The Live CD/USB (Lets call it a Live CD) automatically mounts all partions it sees. Since the Live CD does not come with OSS, the changes will take affect to the HDD with the OSS installed on it.

---

### Post by Furi on 2010-11-08
> **corrytonapple said:**
> Yes, I believe that is the code for uninstalling and reinstalling OSS. Just try that from the Live CD/USB. The Live CD/USB (Lets call it a Live CD) automatically mounts all partions it sees. Since the Live CD does not come with OSS, the changes will take affect to the HDD with the OSS installed on it.
So the disc I used to install Ubuntu onto my computer is a Live CD, no? As is the Xubuntu disc I have? Or is "Try without installing" not what I am supposed to do?

EDIT: [COLOR=Red]Yes, ***YES***, I've managed to find my filesystem. However, how can I uninstall *its* OSS without uninstalling the Live CD's?
[COLOR=Black]Colored that red so it'd be easier to find.

EDIT2: Oh, so you're saying I could just run it in terminal just fine, without any extra shiz? I'll try that.
[/COLOR]

[/COLOR]

---

### Post by Furi on 2010-11-08
Tried the command, and it didn't work. It says it couldn't find the package.

EDIT: Shoot, shoot, shoot... Accidental reply. Sorry.

---

### Post by Furi on 2010-11-09
[LEFT]Currently on xubuntu via livecd with a chrooted terminal up. Someone told me on the IRC channel to check how pulseaudio works on a tty. Will try that.
[/LEFT]

---

### Post by Furi on 2010-11-09
Trying to open pulseaudio returns a load of E: returns. Too many for the screen to hold, so I can't pastebin the output of it.
EDIT: Oh my gosh, crap, crap, crap. I keep hitting "New Reply" thinking it's the edit button.

---

### Post by Furi on 2010-11-09
Ugh, I'm sorry for this bump, but I've been getting only 3-6 hours of sleep every day because of this problem, and I'm trying as hard as I can to fix it. I really need help.

---

### Post by corrytonapple on 2010-11-09
> **Furi said:**
> Ugh, I'm sorry for this bump, but I've been getting only 3-6 hours of sleep every day because of this problem, and I'm trying as hard as I can to fix it. I really need help.
I will edit this post later to help you. As of right now I have to go to school so hold on till the afternoon. I a sumarry, just go in and look for where OSS is and edit that. Also look for how to make changes take effect on your drive that has this issue.

---

### Post by Furi on 2010-11-09
> **corrytonapple said:**
> I will edit this post later to help you. As of right now I have to go to school so hold on till the afternoon. I a sumarry, just go in and look for where OSS is and edit that. Also look for how to make changes take effect on your drive that has this issue.
Okay. It's been 12 hours since that post though.

---

### Post by corrytonapple on 2010-11-09
> **Furi said:**
> Okay. It's been 12 hours since that post though.
Yes, I posted this morning before I had to start. Also, I had other things to do (I have a farm of chickens). Remember, this is a volunteer community, so we can help as we can. I typed out what you basically had to do, and you apparently have not got around to doing it or you did not know how. So to the problem. Lets try something new. I believe this makes the changes go to a certain HDD. Boot your Live CD, then Go to **Applications>Accessories>Terminal**. Then type:
```

cd /media

```
Then:
```

ls

```
and:
```
cd <hard drive label>

```
You will find the Hard Drive label to be entered in the screenshot. It will show you what the title of your HDD is and that is what you put in for "<hard drive label>. Then we can go on with:
```

sudo apt-get purge oss

```
After that is done we will want to put it back on.
```

sudo apt-get install oss

```
That **should **work. Then, restart normally and see what happens. If it wants a password try "ubuntu" or just hitting enter. :)

---

### Post by Furi on 2010-11-09
> **corrytonapple said:**
> Yes, I posted this morning before I had to start. Also, I had other things to do (I have a farm of chickens). Remember, this is a volunteer community, so we can help as we can. I typed out what you basically had to do, and you apparently have not got around to doing it or you did not know how. So to the problem. Lets try something new. I believe this makes the changes go to a certain HDD. Boot your Live CD, then Go to **Applications>Accessories>Terminal**. Then type:
```

cd /media

```Then:
```

ls

```and:
```
cd <hard drive label>

```You will find the Hard Drive label to be entered in the screenshot. It will show you what the title of your HDD is and that is what you put in for "<hard drive label>. Then we can go on with:
```

sudo apt-get purge oss

```After that is done we will want to put it back on.
```

sudo apt-get install oss

```That **should **work. Then, restart normally and see what happens. If it wants a password try "ubuntu" or just hitting enter. :)

Thank you so much. However, don't you think the "chroot" command would be more appropriate? I mean, I'm just asking. I'll try what you said.

EDIT: Tried, couldn't find OSS it says. Tried with chroot too. Still no. I seriously think it actually isn't OSS doing this. Like I said in the edit of the OP, it may be the lines after it. I forgot to mention, I installed devilspie and other stuff to get a desktop terminal. Could THAT be the problem?

---

### Post by corrytonapple on 2010-11-09
> **Furi said:**
> Thank you so much. However, don't you think the "chroot" command would be more appropriate? I mean, I'm just asking. I'll try what you said.

EDIT: Tried, couldn't find OSS it says. Tried with chroot too. Still no. I seriously think it actually isn't OSS doing this. Like I said in the edit of the OP, it may be the lines after it. I forgot to mention, I installed devilspie and other stuff to get a desktop terminal. Could THAT be the problem?
I would have to look into that. I am surprised that did not work. I got the code off of a site and put some of it together from my knowledge and it did not work. :) I have learned. I will see tomorrow later in the evening when I have time. Please try to be patient. I know it is hard having you laptop die. :( Desktop Terminal. Never heard of it. Is that the whole error code? Does it just sit after that or restart? I think OSS might have something to do with it, but you mention other stuff so that could be it. Every thing we try is the closer we get to fixing it and finding out what is wrong. 
:KS

---

### Post by Furi on 2010-11-10
> **corrytonapple said:**
> I would have to look into that. I am surprised that did not work. I got the code off of a site and put some of it together from my knowledge and it did not work. :) I have learned. I will see tomorrow later in the evening when I have time. Please try to be patient. I know it is hard having you laptop die. :( Desktop Terminal. Never heard of it. Is that the whole error code? Does it just sit after that or restart? I think OSS might have something to do with it, but you mention other stuff so that could be it. Every thing we try is the closer we get to fixing it and finding out what is wrong. 
:KS
Yes, it just sits there. I guess I can wait, as long as it's eventually fixed.

---

### Post by corrytonapple on 2010-11-11
It should. If that is the complete error, than it is OSS's fault. Sooo, we have to find out how to uninstall OSS. But, since it has lots of files, I would like to try to dump DevilsPie. I need you to know though that you will loose your current configuration.
So, boot up the Live CD, then go to **Places>Your Ubuntu HDD/Partion**. It should have that partion's File System on the screen. Now go hunting for where DevilsPie is. You could do a search of the drive, which might be up on the top panel. If not, it is in **Accessories**. Take it and delete it! This will dump DevilsPie, which you think must me causing the problem. I go on what you think, not just me. :) Your guess could just be as good as mine.

---

### Post by Furi on 2010-11-11
> **corrytonapple said:**
> It should. If that is the complete error, than it is OSS's fault. Sooo, we have to find out how to uninstall OSS. But, since it has lots of files, I would like to try to dump DevilsPie. I need you to know though that you will loose your current configuration.
So, boot up the Live CD, then go to **Places>Your Ubuntu HDD/Partion**. It should have that partion's File System on the screen. Now go hunting for where DevilsPie is. You could do a search of the drive, which might be up on the top panel. If not, it is in **Accessories**. Take it and delete it! This will dump DevilsPie, which you think must me causing the problem. I go on what you think, not just me. :) Your guess could just be as good as mine.
Oh, it's totally fine getting rid of devilspie. I only installed it for the desktop terminal thing anyways. Can't I use that one "purge" function though?

---

### Post by corrytonapple on 2010-11-11
The last code I gave you was to find the Ubuntu HDD, then apply the code
```

sudo apt-get purge oss

```In this case that did not work, but you could try it with DevilsPie. I might work. If it does, than the "purge oss" part is wrong. Try the code way first. Then the File Browser.
Just thought of this: What if you got to your desktop, but you don't really know it. Just check to see if it is some output code when the system started OSS.

---

### Post by Furi on 2010-11-11
> **corrytonapple said:**
> The last code I gave you was to find the Ubuntu HDD, then apply the code
```

sudo apt-get purge oss

```In this case that did not work, but you could try it with DevilsPie. I might work. If it does, than the "purge oss" part is wrong. Try the code way first. Then the File Browser.
Just thought of this: What if you got to your desktop, but you don't really know it. Just check to see if it is some output code when the system started OSS.
No output code. I just finished removing the devilspie stuff via xubuntu's thunar as root. Hopefully this will work. Will be back.

EDIT: Shoot, still no.

---

### Post by corrytonapple on 2010-11-11
What does it do now? No output code would mean you were probably getting to your desktop with that error code. Can you log in with another user account? Was DevilsPie System wide applied?

---

### Post by Furi on 2010-11-11
> **corrytonapple said:**
> What does it do now? No output code would mean you were probably getting to your desktop with that error code. Can you log in with another user account? Was DevilsPie System wide applied?
Nonono, it's the actual beginning boot before the login screen that it happens.

---

### Post by corrytonapple on 2010-11-11
That is what I thought, but it was a theory. If you still have safe mode on your GRUB screen, then go to recovery mode. Then select "Drop to root terminal". It will be on the very bottom, so you may not see it and will have to scroll. Then type:
```

apt-get purge oss

```
No sudo since you are already root. If it does not work or gives a permissions error, through sudo in. It won't hurt. If this is not it, then the command we are being given is wrong.

---

### Post by Furi on 2010-11-11
> **corrytonapple said:**
> That is what I thought, but it was a theory. If you still have safe mode on your GRUB screen, then go to recovery mode. Then select "Drop to root terminal". It will be on the very bottom, so you may not see it and will have to scroll. Then type:
```

apt-get purge oss

```No sudo since you are already root. If it does not work or gives a permissions error, through sudo in. It won't hurt. If this is not it, then the command we are being given is wrong.
Tried, with sudo too. Nope.
EDIT: Looked it up on synaptic just now, and found these few:

[LIST]
[*]oss4-base
[*]oss4-gtk
[*]python-oss
[*]oss4-dkms
[*]oss4-dev
[*]oss4-preserve
[*]alsa-oss
[*]linux-sound-base
[/LIST]
Should I try purging all of those and reinstalling? Also linux-sound-base?

---

### Post by corrytonapple on 2010-11-11
Do:
```

sudo apt-get purge oss4-base

```
That should be the main part.

---

### Post by Furi on 2010-11-11
> **corrytonapple said:**
> Do:
```

sudo apt-get purge oss4-base

```That should be the main part.
Alright.

EDIT: Problem.

```
root@ubuntu:/# apt-get install oss4-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  oss4-modules
The following NEW packages will be installed:
  oss4-base
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 589kB of archives.
After this operation, 1,106kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  oss4-base
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe oss4-base i386 4.2-build2003-1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/oss4/oss4-base_4.2-build2003-1ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```Same "wicked" stuff happens when I try update and everything else that doesn't involve deletion.

I did try --fix-missing.
```
root@ubuntu:/# apt-get install oss4-base --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  oss4-modules
The following NEW packages will be installed:
  oss4-base
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 589kB of archives.
After this operation, 1,106kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  oss4-base
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe oss4-base i386 4.2-build2003-1ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/oss4/oss4-base_4.2-build2003-1ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

---

### Post by corrytonapple on 2010-11-12
You typed:
```

sudo apt-get install oss4-base

```
It should have been:
```

sudo apt-get **purge **oss4-base

```
Purge Removes and install gets it and installs it.

---

### Post by Furi on 2010-11-12
> **corrytonapple said:**
> You typed:
```

sudo apt-get install oss4-base

```It should have been:
```

sudo apt-get **purge **oss4-base

```Purge Removes and install gets it and installs it.
I removed it successfully, so I was reinstalling it.

---

### Post by Furi on 2010-11-12
Wow, it's been 5 days since I've used my actual Ubuntu.

Anyways, would it have to do with the console configuration file?

---

### Post by Furi on 2010-11-12
Ugh, I'm pretty sure that everything isn't going to work out, and I'm going to have to reinstall my Ubuntu. 

Happy birthday to me.

EDIT: On the 11th.

---

### Post by corrytonapple on 2010-11-12
> **Furi said:**
> Wow, it's been 5 days since I've used my actual Ubuntu.

Anyways, would it have to do with the console configuration file?

> **Furi said:**
> Ugh, I'm pretty sure that everything isn't going to work out, and I'm going to have to reinstall my Ubuntu. 

Happy birthday to me.

EDIT: On the 11th.
Happy late birthday!=D>IDK about the config file, but I will have to agree and if you can reinstall. Not the way I want to point you but it will be much faster that this. :(

---

### Post by Furi on 2010-11-12
> **corrytonapple said:**
> Happy late birthday!=D>IDK about the config file, but I will have to agree and if you can reinstall. Not the way I want to point you but it will be much faster that this. :(
Thank you, and yeah, I'm 15 now.

Anyways, it is NOT OSS. I have confirmed that it isn't. Now that OSS is uninstalled and I haven't reinstalled it yet, starting up regular boot doesn't show the "Starting Open Sound System..." part. Now that we know what it is, we won't be sitting here wondering why nothing is working. It has to do with the config. I can't remember if I changed anything about console prefs when I installed devilspie, but I probably did if I'm going for a desktop terminal. It HAS to be the settings.

However.
I have found my ubuntu livecd. Booting via that ends up with the EXACT same problems. Something must have tampered with grub or something. Booting xubuntu is fine.

---

### Post by corrytonapple on 2010-11-12
> **Furi said:**
> Thank you, and yeah, I'm 15 now.

Anyways, it is NOT OSS. I have confirmed that it isn't. Now that OSS is uninstalled and I haven't reinstalled it yet, starting up regular boot doesn't show the "Starting Open Sound System..." part. Now that we know what it is, we won't be sitting here wondering why nothing is working. It has to do with the config. I can't remember if I changed anything about console prefs when I installed devilspie, but I probably did if I'm going for a desktop terminal. It HAS to be the settings.

However.
I have found my ubuntu livecd. Booting via that ends up with the EXACT same problems. Something must have tampered with grub or something. Booting xubuntu is fine.
Then recovery mode:
```

sudo apt-get purge grub

```
I think. Then:
```

sudo apt-get install grub

```
Try that to dump GRUB and have it come back. So you go to boot the Ubuntu Live CD and it messes up? After GRUB or before?

---

### Post by Furi on 2010-11-12
> **corrytonapple said:**
> Then recovery mode:
```

sudo apt-get purge grub

```I think. Then:
```

sudo apt-get install grub

```Try that to dump GRUB and have it come back. So you go to boot the Ubuntu Live CD and it messes up? After GRUB or before?
It's the exact same problem. You know, the[COLOR=Red][COLOR=Black]```
* Setting console screen modes and fonts
^[[12;2R
```[/COLOR][/COLOR]thing.

---

### Post by corrytonapple on 2010-11-12
OK. Try the reinstall. Back up your documents and stuff first though! Also, when you tried install OSS back, did you drop to root shell with networking? If not, not networking so no connect.

---

### Post by Furi on 2010-11-12
> **corrytonapple said:**
> OK. Try the reinstall. Back up your documents and stuff first though! Also, when you tried install OSS back, did you drop to root shell with networking? If not, not networking so no connect.
It didn't connect when I tried. Also, I can't get anywhere on the ubuntu disk (like I said, same error), and I don't want to install xubuntu.

---

### Post by corrytonapple on 2010-11-12
When you tried the GRUB purge/reinstall? If you have not tried that, try it again. Though it sounds like you are past GRUB when it fails.

---

### Post by Furi on 2010-11-12
> **corrytonapple said:**
> When you tried the GRUB purge/reinstall? If you have not tried that, try it again. Though it sounds like you are past GRUB when it fails.
Yes, I'm past grub. Forget what I said about it. It wouldn't connect when I tried starting the connected console.

---

### Post by corrytonapple on 2010-11-12
Then not GRUBs fault. Boot that Xubuntu Live CD (I have never used it, so you are on your own here), backup documents, and then wipe Ubuntu. You could format or go in and delete manually (Not recommended). Then install Ubuntu in the slot you gave it. I have not done that either, but I would assume it would have a button on the installer to let you do that.

---

### Post by Furi on 2010-11-12
> **corrytonapple said:**
> Then not GRUBs fault. Boot that Xubuntu Live CD (I have never used it, so you are on your own here), backup documents, and then wipe Ubuntu. You could format or go in and delete manually (Not recommended). Then install Ubuntu in the slot you gave it. I have not done that either, but I would assume it would have a button on the installer to let you do that.

Just a reminder, my ubuntu disc gets the same errors that the hard drive boot does. I don't want xubuntu either.

---

### Post by corrytonapple on 2010-11-12
So the above steps will work. You are just formatting your Ubuntu HDD, then taking out your Xubutnu disk then putting in your Ubuntu disk, and installing from there. After formatting, there should be no issues booting the Ubuntu Live CD.

---

### Post by Furi on 2010-11-12
> **corrytonapple said:**
> So the above steps will work. You are just formatting your Ubuntu HDD, then taking out your Xubutnu disk then putting in your Ubuntu disk, and installing from there. After formatting, there should be no issues booting the Ubuntu Live CD.
But what if something new in ubuntu is doing this? What if this has nothing to do with my actions? I never said the update I did wouldn't have caused it.

---

### Post by Furi on 2010-11-13
> **Furi said:**
> But what if something new in ubuntu is doing this? What if this has nothing to do with my actions? I never said the update I did wouldn't have caused it.
Well?

Sorry, I'm getting really stressed from all of this.

---

### Post by corrytonapple on 2010-11-13
IDK. If it is some new update nothing new is going to happen to your machine booting or anything being that you cannot even boot to the update manager (GUI) or get networking in the Recovery Mode (CLI) to update.

---

### Post by Yellow Pasque on 2010-11-13
What kind of graphics chip/card do you have?

---

### Post by Furi on 2010-11-13
> **Temüjin said:**
> What kind of graphics chip/card do you have?
I don't see how that has to do with this because it worked fine previously, but it's Intel. Intel 4 Chipset Family... or something like that.

---

### Post by Furi on 2010-11-14
Bump.

---

### Post by corrytonapple on 2010-11-14
Not much more I can tell you. I have to agree I don't know what the graphics chip would have to do with anything. Since we cannot update the system, know it is not OSS's fault, and I nor other users seem to know how to fix this, I must say if you want a working system faster than this, you need to reinstall via the steps I gave you in my last post. I am out of ideas now....

---

### Post by Yellow Pasque on 2010-11-14
Boot with the nomodeset flag and see what happens

---

### Post by corrytonapple on 2010-11-14
> **Temüjin said:**
> Boot with the nomodeset flag and see what happens
How do you do that?

---

### Post by Yellow Pasque on 2010-11-14
> **corrytonapple said:**
> How do you do that?
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Furi on 2010-11-14
> **Temüjin said:**
> [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Already did. Same errors, just the console was in a much smaller resolution. Looked like 640x480.

---

### Post by Furi on 2010-11-17
Bump. I still need this fixed...

---

### Post by corrytonapple on 2010-11-17
> **corrytonapple said:**
> Then not GRUBs fault. Boot that Xubuntu Live CD (I have never used it, so you are on your own here), backup documents, and then wipe Ubuntu. You could format or go in and delete manually (Not recommended). Then install Ubuntu in the slot you gave it. I have not done that either, but I would assume it would have a button on the installer to let you do that.
> **corrytonapple said:**
> So the above steps will work. You are just formatting your Ubuntu HDD, then taking out your Xubutnu disk then putting in your Ubuntu disk, and installing from there. After formatting, there should be no issues booting the Ubuntu Live CD.
Try the above steps. Really, you should. We have helped you and it has come down to a reinstall. Is there something wrong with reinstalling? If you are unsure we are here to help you reinstall. With this many posts in a thread, chances are good that no more users are going to check out this thread. I am sorry, but this is it.........
> **Temüjin said:**
> [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
I will bookmark that. :)

---

### Post by Furi on 2010-11-17
> **corrytonapple said:**
> Try the above steps. Really, you should. We have helped you and it has come down to a reinstall. Is there something wrong with reinstalling? If you are unsure we are here to help you reinstall. With this many posts in a thread, chances are good that no more users are going to check out this thread. I am sorry, but this is it.........

I will bookmark that. :)

The disc doesn't boot. It instead just boots from hard drive a few minutes after reading it. The Ubuntu one, I mean.

---

### Post by corrytonapple on 2010-11-17
Try to boot the Xubuntu one since you said it boots. Then pull of any data you want and put it on a external hard drive or flash drive. Format your Ubuntu partion from whatever Disk Utility it uses, and make it an ext3 partion. Shut down, eject your Xubutnu CD, and boot from your Ubuntu CD. Install Ubuntu to that partion you made from the Xubuntu CD. Your machine will restart, and then you have a working system.

---

