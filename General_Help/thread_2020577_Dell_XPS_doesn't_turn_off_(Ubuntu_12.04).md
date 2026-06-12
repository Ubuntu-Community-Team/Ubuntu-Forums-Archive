---
title: "Dell XPS doesn't turn off (Ubuntu 12.04)"
date: 2012-07-08
forum: General Help
---

### Post by Sapienso on 2012-07-08
Hi. My computer is a Dell XPS 1730, and I have had a problem since I  installed 12.04. It  does not turn off, unless I apply for a few seconds  the turn off button.  It does not reiniciate, either. 

I have done a number of things recommended in [www.ubuntu-es.org]("http://www.ubuntu-es.org"), the Spanish forums, but to no avail:

I have done things like installing   **wmshutdown** and **qshutdown**; also I have edited the grub file to modify the line that says 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

to add  "acpi=force", so that it ends up like: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" 

It has not worked.Can anyone help me, please?[FONT=Ubuntu]

[/FONT]

---

### Post by Redblade20XX on 2012-07-09
Have you tried shutting off acpi and see what happens?

Instead of "acpi = force", try pushing the parameter "noacpi" and see what happens.

- Red

---

### Post by Sapienso on 2012-07-09
I works!!!! :p

Thanks a lot, [Redblade20XX]("http://ubuntuforums.org/member.php?u=859037"). I have had this problem for quite a while, and only now somebody is able to solve it. 

I will describe in detail what I did, so that other people with the same problem, who, like me, are not experts, can handle the solution. 

First edit the file grub:

$ sudo emacs gedit /etc/default/grub
(you might use another editor, like gedit, instead of emacs) 

Then, within the file, modify the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add, as [Redblade20XX]("http://ubuntuforums.org/member.php?u=859037") suggested,  "noacpi=force", so that it ends up like 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noacpi=force"  

After that, save the file, close the editor, and update the grub file from the propt:

 $ sudo update-grub 

The first time I reiniciated it did not work (probably the system had not recognized the change yet). But, after turning the machine off by force, using the turn off button (you have to wait a few seconds), I turned it on, and did the test: reiniciate, or turn off, a few times. 

It worked!!! How glad I was when this happened :popcorn:
Thanks again, Redblade20XX

---

### Post by Redblade20XX on 2012-07-09
> **Sapienso said:**
> I works!!!! :p

Thanks a lot, [Redblade20XX]("http://ubuntuforums.org/member.php?u=859037"). I have had this problem for quite a while, and only now somebody is able to solve it. 

I will describe in detail what I did, so that other people with the same problem, who, like me, are not experts, can handle the solution. 

First edit the file grub:

$ sudo emacs gedit /etc/default/grub
(you might use another editor, like gedit, instead of emacs) 

Then, within the file, modify the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add, as [Redblade20XX]("http://ubuntuforums.org/member.php?u=859037") suggested,  "noacpi=force", so that it ends up like 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noacpi=force"  

After that, save the file, close the editor, and update the grub file from the propt:

 $ sudo update-grub 

The first time I reiniciated it did not work (probably the system had not recognized the change yet). But, after turning the machine off by force, using the turn off button (you have to wait a few seconds), I turned it on, and did the test: reiniciate, or turn off, a few times. 

It worked!!! How glad I was when this happened :popcorn:
Thanks again, Redblade20XX

Just as a note, you just killed an acpi functionality but have identified the problem as an acpi problem.

If you want any power management events to work, try updating BIOS and  removing the "noacpi=force" option to see if anything changes.


- Red

---

### Post by Sapienso on 2012-07-24
> **Redblade20XX said:**
> Just as a note, you just killed an acpi functionality but have identified the problem as an acpi problem.

If you want any power management events to work, try updating BIOS and  removing the "noacpi=force" option to see if anything changes.


- Red

Hi, Red. Sorry for the delay in reponding. 

In fact, the problem is back :(. I do not understand your last sentence. Does it mean that once I uptade BIOS, I should remove the option "noacpi=force" from the same file I modifed, or brom BIOS?

Sapienso

---

### Post by mc4man on 2012-07-24
Does that laptop have a nvidia display adapter & if so are you using the nvidia-current driver?

---

### Post by Sapienso on 2012-07-24
> **mc4man said:**
> Does that laptop have a nvidia display adapter & if so are you using the nvidia-current driver?

Hi, mc4man

I have a VGA compatible controller nVidia Corporation G84 [GeForce 8700M GT] 

To the second question, I have a "graphic acceleration controller for Nvidia cards (current vertion)[recommended]". I am translating from Spanish. 

Sapienso

---

### Post by mc4man on 2012-07-24
Here on a xps 1300m, (8400m),  I've had a shutdown/restart issue ever since nvidia went past 290.XX
Generally I'd get shutdowns/restarts for a limited time, then they would start failing. the monitor shuts off but the computer stays powered on.

Sometimes certain changes would restore shutdown/restarts, but the issue always would shortly return.
If this sounds similar, what I've found - 

using nouveau there is no issue, though there are some downsides to nouveau but enabling vsync in nouveau helps a lot.

Downgrading to the 290.10 driver fixes the issue *nvidia-current_290.10-0ubuntu2

I only see this on a 32 bit install, so starting over with a 64 bit install also resolves here.

current open bug on - 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564)

---

### Post by Sapienso on 2012-07-25
Thanks a lot, mc4man. That is exactly what is going on with my machine (a Dell XPS M1730). Sorry for my ignorance on many of the issues in the comments that follow your points:  

> **mc4man said:**
> Here on a xps 1300m, (8400m),  I've had a shutdown/restart issue ever since nvidia went past 290.XX

I thought that the problem was with Ubuntu 12.04 on my machine, since I did not have this problem before that ubuntu release. 

> **mc4man said:**
>  Generally I'd get shutdowns/restarts for a limited time, then they would start failing. the monitor shuts off but the computer stays powered on.

Sometimes certain changes would restore shutdown/restarts, but the issue always would shortly return.
If this sounds similar,...


Exactly that is what has happened to me. Just what is described in more detail in the bug link you provided. 
 
 
> **mc4man said:**
> what I've found - 

using nouveau there is no issue, though there are some downsides to nouveau but enabling vsync in nouveau helps a lot.

Ok. I will remove nvidia and install nowveau like in the bug link you provided: 

<start quote>
Remove nvidia driver: sudo apt-get --purge remove nvidia*
 and install the open one:
 sudo apt-get install xserver-xorg-video-nouveau libdrm-nouveau1a nouveau-firmware
<end quote>
 
But before that, I wanted to ask you how do you enable vsync in nouveau.

> **mc4man said:**
> Downgrading to the 290.10 driver fixes the issue *nvidia-current_290.10-0ubuntu2
Sorry, but I do not understand this. First, I do not understand the meaning of "downgrading to the 290.10 driver". Does it refer to the nvidia driver I currently use? By the way, as far as I remember, I am using the one that comes by default when I installed Ubuntu 12.04. But I suspect I had graphics problems at the beginning, and had to chose one of the alternatives using the hardware manager of Ubunto. Sorry, but I do not remember well. Now,  do you suggest that, instead of removing nvidia and install nouveau, should I downgrade the driver instead? And if so, how do I do it, please?  

> **mc4man said:**
> I only see this on a 32 bit install, so starting over with a 64 bit install also resolves here.

I really do not understand what this means, sorry again. In fact, in my ignorance, I thought that a machine is either 32 bit, or 64 bit, and depending on that, you do the instalation. I though it was not a software issue, but a hardware issue. In any case, how do I start with a 64 bit install? Do you think this would be the solution, instead of installing nouveau, or downdraging nvidia?

> **mc4man said:**
> current open bug on - 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564)

Thanks a lot for the link. I read it, but there many things I did not understand. Technical issues. I skipped over them and concentrated on the general issues, and the solutions. 

Thank you again, mc4man.

Sapienso

---

### Post by mc4man on 2012-07-25
Will try to explain the various options you can try -

**64 bit install** - 
The default iso offered on Ubnutu's website is a 32 bit one. To do a 64 bit install you'd need to expand the dropdown under "pick your flavor" & choose the 64 bit option, download the .iso, ect..
This would be a new install, - you'd be completely starting over from scratch
[B]
To go back to nouveau from nvidia-current in 12.04-[/B] 
Note that nouveau does Not support powermizer so you'll likely get a bit less runtime on battery, if that's an issue then no point doing

If proceeding - 
```
sudo apt-get purge nvidia-current
```

Before you reboot you need to either move /etc/X11/xorg.conf to a .bak or replace what's in it with something to enable vsync in nouveau
Note that not all nvidia cards support vsync in nouveau, I'm almost 100% sure that your card  does.

So after removing nvidia-current do this to enable vsync in nouveau
```
sudo gedit /etc/X11/xorg.conf
```

Replace **all that's in the file** with this, if empty then just add this, use copy & paste, then save
```

Section "Device"
 Identifier "My Graphics"
 Option "GLXVBlank" "on"
EndSection
```

If you don't want to enable vsync or if upon rebooting there is an issue then move xorg.conf to a bak like this
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then reboot & you'll be using nouveau

**To downgrade to the 290.10 nvidia-current package**
Note that 12.04 is using a newer nvidia version, one reason was it supplied a security update. Like many 'vulnerabilities' found the actual risk is quite minor.

These commands assume you are still using nvidia-current, ir you've already moved to nouveau then may need to adjust method slightly - ask first
If deciding to do on your **32 bit 12.04 install** 
- ```
mkdir nvidia_down && cd nvidia_down

```

```
wget https://launchpad.net/~canonical-x/+archive/x-staging/+build/3103493/+files/nvidia-current_290.10-0ubuntu2_i386.deb
```
```
sudo dpkg -i nvidia-current_290.10-0ubuntu2_i386.deb
```
reboot

---

### Post by Sapienso on 2012-07-26
Hi, mc4man.

Thanks for your long and precise answer. 

From the three alternatives you gave me, I opted for the downgrading of the Nvidia driver. After doing it following your directions, and after doing several tests, it seems to work perfectly. 

I chose this option because that driver worked for me before the Ubuntu 12.04 install. Besides, it was the most simple one. I trust you on the security issue you mentioned. 

The 64bit option required a lot of work, and I would prefer to find information on the overal advantages and disadvantages of doing that. Since this is off topic here, I will later post the question in the install forum. 

I will make the decition later on, when I have the opportunity of doing an Ubuntu upgrade. 

Thanks a lot for the information, for the help. It really solved a problem that was anoying for me, and a litle disheartnening with respect to Ubuntu. Of course I never abandoned the idea of being a believer of FS, and your help strengthen my convitions on this. 

Sapienso. 
PS: I will post the link in the Spanish forums, so that they can see your answers. 
PS2: sorry for this question, but how do you insert the [SOLVED] word in the title of the thread? I tried to do it before (as you know, it did not really work then, but now it is indeed apropriate.

---

### Post by mc4man on 2012-07-26
For solved you click on "thread tools", it's in the drop down

Make sure that you don't inadvertently upgrade nvidia-current back to the 12.04 default version. You can lock/pin the package in various ways, myself I only use synaptic for updating so I lock it there
(best to always pay attention when updating...

The bug is still open and still going strong on 12.10 & the 302.xx drivers so I don't have much confidence it will be fixed unless it 'just happens'.

If down the road you move up to 12.10 or 13.04 & still have that laptop then just go ahead & do a fresh 64 bit install - while I've modified the 290.xx package to work with the 3.5/6 kernel it's not likely to work with the xserver version in 12.10 & certainly not in 13.04 
(in other words 12.04 may be the last time one can use the nvidia 290.xx drivers

---

### Post by Sapienso on 2012-07-28
Hi, mc4man.

> **mc4man said:**
> For solved you click on "thread tools", it's in the drop down

Thanks. I am going to use when we are (really!) done

> Make sure that you don't inadvertently upgrade nvidia-current back to the 12.04 default version. 
Excellent (and life saving!) remark. In fact, it just happened to me. Without your warning, I would have been really frustrated, since my problem came back, and I did not know that the reason was that I did an ordinary updating of several packages, without checking that one of them was the Nvidia default (judging for what happened later). When it happened I was really surprised and disappointed. Fortunately, I had had a first look at your reply, without really knowing how easy it is to go back to the default Ubuntu 12.04 version of Nvidia. 

For updating, I have used, since I have Unity (as I recall, it was since the previous version to Ubuntu 12.04), the "Update Manager" (I am translating from Spanish). It is the one that pups up whenever there is a new version of at least one package. A funny thing is that, once I read carefully your post, I did the downgrading again, and within few moments, I think, the Update Manager appeared again, with only the default of Nvidia, asking me if I agreed with the update recommended! Usually the Update Manager appears with several packages to update, and since I am a simple final user, I usualy do not check for the recommended updates, and simply agree to go on. 

> You can lock/pin the package in various ways, myself I only use synaptic for updating so I lock it thereBefore using Update Manager, I used Synaptic too. Now, following your advise, I installed Synaptic (using Software Center). But, after looking at the nvidia related packages, I am not sure how to lock the downgraded version. According to Synaptic, my computer has the following installed:
 

  ```
E            Package                                Installed version            Last version
        
 green       nvidia-settings                           295.33-0ubuntu1           295.33-0ubuntu1
 green      nvidia-settings-updates         295.33-0ubuntu1           295.33-0ubuntu1
 green      nvidia-common                         1:0.2.44                               1:0.2.44
  “!”            nvidia-current                            290.10-0ubuntu2           295.40-0ubuntu1
 green      nvidia-settings-updates        295.49-0ubuntu0.1        295.49-0ubuntu0.1
```> (best to always pay attention when updating...OK!. Now, I wonder if you can lock things up so that the specific package which I have downgraded does not appear for updating in the Update Manager. 

> The bug is still open and still going strong on 12.10 & the 302.xx drivers so I don't have much confidence it will be fixed unless it 'just happens'. OK. It is nice for us final users to know that there are technical people out there working for everyone. I myself do some work in my capacity (I advocate a lot FS with my students, for example). I think this is the model of the future in society: solidarity production and distribution of public goods, like technology, science, which are, by far, the most important components of any economic good now. It is the miracle of “good, pretty, and inexpensive” made reality. 

> If down the road you move up to 12.10 or 13.04 & still have that laptop then just go ahead & do a fresh 64 bit install - while I've modified the 290.xx package to work with the 3.5/6 kernel it's not likely to work with the xserver version in 12.10 & certainly not in 13.04 
(in other words 12.04 may be the last time one can use the nvidia 290.xx drivers OK. Great. When the time comes to do the updates, I will make sure to change to 64 bit install. Before that, I will document myself a little about its implications and requirements.  
 

 Thanks a lot, mc4man
 

 Sapienso

---

### Post by Sapienso on 2012-08-01
Hi, mc4man, and everyone. 

Since my problem has been solved, and I have asked additional questions which are basically off topic, I am flagging this thread as "SOLVED". 

Thanks a lot, again.

---

### Post by Sapienso on 2012-08-06
Hi again. Thanks to Black veil, I found the answer (comented below) to my following question: 
> **Sapienso said:**
> 

Before using Update Manager, I used Synaptic too. Now, following your advise, I installed Synaptic (using Software Center). But, after looking at the nvidia related packages, I am not sure how to lock the downgraded version. According to Synaptic, my computer has the following installed:
 

  ```
E            Package                                Installed version            Last version
        
 green       nvidia-settings                           295.33-0ubuntu1           295.33-0ubuntu1
 green      nvidia-settings-updates         295.33-0ubuntu1           295.33-0ubuntu1
 green      nvidia-common                         1:0.2.44                               1:0.2.44
  “!”            nvidia-current                            290.10-0ubuntu2           295.40-0ubuntu1
 green      nvidia-settings-updates        295.49-0ubuntu0.1        295.49-0ubuntu0.1
```OK!. Now, I wonder if you can lock things up so that the specific package which I have downgraded does not appear for updating in the Update Manager. 


The answer is in the following link: 

[http://ubuntuguide.net/stop-an-application-from-being-update-in-ubuntu](http://ubuntuguide.net/stop-an-application-from-being-update-in-ubuntu)

I tried and it works! What was most interesting to me is that the procedure using Synaptic  blocks the application from being updated not only within Synaptic, but also in Update Manager. 

Thanks a lot, Black veil,

Sapienso

---

### Post by Sapienso on 2012-08-07
> **Sapienso said:**
> 
I tried and it works! 
  I forgot something about my question. The (only) package I locked is the fourth line of the above chart, as it appears in Synaptic:

“!”            nvidia-current                            290.10-0ubuntu2           295.40-0ubuntu1

Best, 

Sapienso

---

