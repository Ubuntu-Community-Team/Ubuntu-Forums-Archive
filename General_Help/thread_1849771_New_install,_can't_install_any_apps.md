---
title: "New install, can't install any apps"
date: 2011-09-25
forum: General Help
---

### Post by Custardy on 2011-09-25
Hey guys, hoping you could give me some help with this problem.

I installed Ubuntu 11.04 on my laptop today because my hard drive died so I needed something light to install on my flash drive. 
I basically only use my laptop for watching movies and browsing in bed so it's rather annoying not being able to install VLC. 
I've tried installing it through Terminal and through Software center and I keep getting a "package dependencies cannot be resolved" error message. This also happens with I try to install flash for YouTube. 
I have literally done nothing on this install other than try to install those 2 programs and some googling.

Any help would be greatly appreciated, but please go easy on me as I haven't had any Ubuntu experience prior to today.

Thanks

---

### Post by Bucky Ball on 2011-09-25
Perhaps 10.04 would be a better choice for a new-comer, but anyhow ...

I presume you can get online with the machine, can browse with Firefox, etc ... ?

I suggest you do an update if you have only just installed. Then give this another try. You can do it with Update Manager (System>Administration>Update Manager) or type:

```
sudo apt-get update
```... in a terminal.

Then, perhaps:

```
sudo apt-get upgrade
```This won't upgrade the OS to a newer release, it upgrades any packages (apps and other things) to the newest version in the repsitory ... 

Welcome and good luck ... ;)

---

### Post by Custardy on 2011-09-25
I tried that and the problem still persists. I ran the Update Manager and downloaded all the updates from there too.

---

### Post by davdo2004 on 2011-09-25
Open up synaptic package manager and click on 'settings'  'Software Sources'. Check to see if 'software restricted by copyright', is checked. Under the 'other software tab', check 'Canonical Partners' . Click on the reload button and see if vlc and flash show up in the list.

---

### Post by Custardy on 2011-09-25
> **davdo2004 said:**
> Open up synaptic package manager and click on 'settings'  'Software Sources'. Check to see if 'software restricted by copyright', is checked. Under the 'other software tab', check 'Canonical Partners' . Click on the reload button and see if vlc and flash show up in the list.
They were both already checked. VLC does come up in the list, I just get the error message that I stated in my original post.

---

### Post by Custardy on 2011-09-25
If it's any help, this is what came up in the drop-down box of the error:


The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 1.1.11-2~ppa3) but 1.1.11-2~ppa3 is to be installed
     Depends: libaa1 (>= 1.4p5) but 1.4p5-38build1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.7-1) but 4:0.7.1.0u2~ppa1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.7-1) but 4:0.7.1.0u2~ppa1 is to be installed
     Depends: libc6 (>= 2.8) but 2.13-0ubuntu13 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.4-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
     Depends: libice6 (>= 1:1.0.0) but 2:1.0.7-1ubuntu1 is to be installed
     Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.3 is to be installed
     Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
     Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.1ubuntu3 is to be installed
     Depends: libstdc++6 (>= 4.5) but 4.5.2-8ubuntu4 is to be installed
     Depends: libtar but it is not going to be installed
     Depends: libxcb-xv0 (>= 1.2) but 1.7-2ubuntu2 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

---

### Post by oldos2er on 2011-09-25
Which PPAs do you have? I would try disabling them then retry installing vlc.

---

### Post by Custardy on 2011-09-25
> **oldos2er said:**
> Which PPAs do you have? I would try disabling them then retry installing vlc.
Sorry, don't know what you mean by PPAs.

---

### Post by oldos2er on 2011-09-25
PPA = Personal Package Archive. It's a repository that's enabled manually, meaning you or someone else using the computer added it. From what you posted,

vlc: Depends: vlc-nox (= 1.1.11-2~ppa3) but 1.1.11-2~[COLOR="Red"]ppa[/COLOR]3 is to be installed

says it's installing from a PPA. Can you run ```
ls /etc/apt/sources.list.d
``` and post the output here?

---

### Post by tech7 on 2011-09-25
> **davdo2004 said:**
> Open up synaptic package manager and click on 'settings'  'Software Sources'. Check to see if 'software restricted by copyright', is checked. Under the 'other software tab', check 'Canonical Partners' . Click on the reload button and see if vlc and flash show up in the list.

Did you update after you had done that?

---

### Post by Custardy on 2011-09-26
> **oldos2er said:**
> PPA = Personal Package Archive. It's a repository that's enabled manually, meaning you or someone else using the computer added it. From what you posted,

vlc: Depends: vlc-nox (= 1.1.11-2~ppa3) but 1.1.11-2~[COLOR=Red]ppa[/COLOR]3 is to be installed

says it's installing from a PPA. Can you run ```
ls /etc/apt/sources.list.d
``` and post the output here?
This is what came up: medibuntu.list  n-muench-vlc-natty.list  n-muench-vlc-natty.list.save
I haven't enabled any repositories, the ones that are enabled were already enabled.

---

### Post by oldos2er on 2011-09-26
So someone else has access to your computer? No PPAs are used by default.

Run ```
software-properties-gtk
``` and under the Other Software tab, disable the PPAs. When you're done run ```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by Custardy on 2011-09-26
> **oldos2er said:**
> So someone else has access to your computer? No PPAs are used by default.
 
Run ```
software-properties-gtk
``` and under the Other Software tab, disable the PPAs. When you're done run ```
sudo apt-get update && sudo apt-get install vlc
```
 Awesome, will try this when I get home. I really hope this works, I wanna watch movies :P
 
Thanks for the help guys.

---

### Post by Custardy on 2011-09-27
> **Custardy said:**
> Awesome, will try this when I get home. I really hope this works, I wanna watch movies :P
 
Thanks for the help guys.
Didn't work, is there an older version of ubuntu that I should change to?

---

### Post by oldos2er on 2011-09-27
Can you please post the full output from the command? "Didn't work" doesn't give enough info to try to solve the problem.

---

### Post by mike555 on 2011-09-27
So you installed to a flash drive? did you set persistence?

---

### Post by kaLuless on 2011-09-27
> **Bucky Ball said:**
> Perhaps 10.04 would be a better choice for a new-comer, but anyhow ...


Perhaps it would be nice if the Ubuntu didn't push the latest version that doesn't work. I'll follow your advice but I'm going to install in Windows - this has been wasting a huge amount of my time as well.

---

### Post by Bucky Ball on 2011-09-27
Installing in Windows might waste more. Wubi is not really intended for permanent use.

You might be spending a lot of time but once it's set up this will seem like nothing but a learning curve and once your machine is up and running, it's up and running. You won't have to faff around like this again possibly ever ... (unless you want to experiment, break things, then fix 'em for the fun of it but I have a separate install for that).

---

### Post by kaLuless on 2011-09-28
> **Bucky Ball said:**
> Installing in Windows might waste more. Wubi is not really intended for permanent use.

You might be spending a lot of time but once it's set up this will seem like nothing but a learning curve and once your machine is up and running, it's up and running. You won't have to faff around like this again possibly ever ...

I appreciate that encouragement. This morning had my day delayed by one of Windows' classic updates - couple hundred MB of files, several restarts....

I started downloading Wubi then noticed it was the broken v.11 as well, so downloaded 10.4 for a CD which loads a line or two of type, then sits doing nothing with a black screen. I remembered why I didn't install Ubuntu when v.10 came out - because I couldn't. Another new CD in the trash.

(How can I install v.10 if the installer CD doesn't work?)

I've updated as much as Update Manager will allow in v.11, and still no luck. But I'll keep playing with it and post results here.

---

### Post by Bucky Ball on 2011-09-28
Try a proper install rather than wubi. See if it runs from the disk. When you boot from the install CD you should get an option to 'Try Ubuntu'. Do that. If all runs okay you should be good to go.

The other option is to try the alternate install CD (not Desktop). That is text based and can make all the difference (especially if graphics is your issue which is not unusual). Then, it might not. ;)

---

