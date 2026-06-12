---
title: "no console available"
date: 2010-01-21
forum: General Help
---

### Post by repsakkgn on 2010-01-21
after latest updates i've got none of the consoles(clrl-alt F1-F6) working. it's just an empty screen i see.. what happened&how to fix?
P.S. ubuntu 9.10

---

### Post by lykwydchykyn on 2010-01-21
What kind of video card do you have?  If you aren't sure, run this command and post the output here:

```

lspci|grep -i vga

```

---

### Post by repsakkgn on 2010-01-21
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
driver installed from official nvidia site/
this may probably be a grub issue. i have GRUB_CMDLINE_LINUX=" vga=773" set, but i have the widescreen monitor 1440x900. tryed
GRUB_CMDLINE_LINUX=" vga=normal ,but that didnt help.

---

### Post by lykwydchykyn on 2010-01-21
I've not had this problem with nvidia cards.  I'm currently using the (proprietary) driver from the repositories with my 8400 GS, is there a reason you downloaded one from Nvidia instead?

---

### Post by repsakkgn on 2010-01-21
the one from the site is newer. thats the only reason. newer doesn't mean it's better though...:)

---

### Post by lykwydchykyn on 2010-01-21
> **repsakkgn said:**
> the one from the site is newer. thats the only reason. newer doesn't mean it's better though...:)

Very often not, I'm afraid.

I'd try the one in the repos, see if it works better.  Or you can see if there's an even newer one on Nvidia's site.  What I suspect is that an update to Xorg is not liking whatever version of the driver you have.

---

### Post by repsakkgn on 2010-01-21
Is there a chance for the last official driver to be older than the one in the repos? I doubt it. What about the absense of consoles?

---

### Post by lykwydchykyn on 2010-01-21
> **repsakkgn said:**
> Is there a chance for the last official driver to be older than the one in the repos? I doubt it. What about the absense of consoles?

What I'm saying is that the newer version on Nvidia's website may be having a problem with your current version of Xorg.  There was an update to Xorg that went out in the last day or two, in theory this could be where the problem started.

When they (Ubuntu) test a package update like this, it's going to be tested against the video drivers in the repositories, not the latest ones from Nvidia.  So if there is a bug between the latest Nvidia driver and the new Xorg package, nobody's going to see that.  So it's worth trying the OLDER driver package in the repos to see if it's more compatible.

It may have nothing to do with your consoles, but it's where I'd start troubleshooting first.  I've had problems in the past (not with Nvidia cards, but with older SiS and intel chips) where the VT's disappeared or became garbled after starting X.  It was a video driver issue.

---

### Post by repsakkgn on 2010-01-21
ok. thanx, i'll try the driver from the repos, but the thing is that when i do /etc/init.d/gdm stop there's no console too. Just the blank screen. I believe this command stops the x server...:(

---

### Post by lykwydchykyn on 2010-01-21
> **repsakkgn said:**
> ok. thanx, i'll try the driver from the repos, but the thing is that when i do /etc/init.d/gdm stop there's no console too. Just the blank screen. I believe this command stops the x server...:(

You may have to select "recovery mode" from the GRUB prompt at boot to get to a console.  If my suspicions are correct, the consoles should work as long as X doesn't get launched.

---

### Post by repsakkgn on 2010-01-21
they don't...:( even when i boot into recovery mode...

---

### Post by ratcheer on 2010-01-21
All of this sounds very strange. I am running driver 195.30 downloaded from the nVidia web site. My card is a 9400GT. I know of no troubles starting a console, but since I haven't done so in the past few days, I will see if I can start one, now, and report back.

Tim

---

### Post by repsakkgn on 2010-01-21
the problem is that getty daemon is not started. the question is how do i make it start and why the updates broke the system?

---

### Post by ratcheer on 2010-01-21
Ctrl-Alt-F1 worked to take me to a console. Unless I am completely misunderstanding, I don't think it is a problem with the latest nVidia drivers.

Tim

---

### Post by repsakkgn on 2010-01-21
try to update the system;)

---

### Post by lykwydchykyn on 2010-01-21
Seems I sent you on a wild goose chase with the drivers; sorry.

If getty's aren't starting I'd expect to see some kind of errors in the output from dmesg.  dmesg puts out a lot of stuff, maybe first try dmesg|grep getty and see if that looks useful.

---

### Post by repsakkgn on 2010-01-22
sudo dmesg|grep getty gives no output. manual searchinf for "getty" in var/log/dmesg gives nothing too..

---

### Post by repsakkgn on 2010-01-22
somebody heelp!!

---

### Post by repsakkgn on 2010-01-23
is there any way to fix it?

---

### Post by lykwydchykyn on 2010-01-23
> **repsakkgn said:**
> is there any way to fix it?

I'm sure there is.  

But step one is always determining what the actual issue is, and we're not there yet.

After you're booted, does anything come back from:
```

ps -e |grep getty

```

Also, if you leave your monitor on one of the non-functional terminals, does it stay active or go into sleep mode (i.e., as if it's getting no input)?

---

### Post by repsakkgn on 2010-01-23
there's no output...
the monitor doesnt go in the sleep mode..the cursor blinks ...

---

### Post by repsakkgn on 2010-01-24
please help!!:)

---

### Post by pbrane on 2010-01-24
You should delete the vga=xxx from /etc/default/grub and look closely at any changes you have made to this file. Then run *update-grub*. I assume you are using grub2 and not legacy grub? There seems to be a problem with the framebuffer and some vga modes, even those the BIOS supports. What I got when I tried to use a vga=xxx that was supported ( by running vbeinfo at grub prompt ) was just a blinking cursor. I do use vga=791 now and it works fine. Grub2 gives a warning that I ignore. 

You can try *sudo dpkg-reconfigure grub* and/or *grub-pc* and/or *grub-common*. That may help to fix any config problems.

Also I use the nvidia driver from the nvidia site ( 190.53 ) I have never had any issues with those drivers. The ones in the repos are the same drivers, just older.

---

### Post by repsakkgn on 2010-01-24
There is no vga line (not even vga at all) in my /etc/default/grub. Can you post your /etc/default/grub file?

all i have is GRUB_GFXMODE=1440x900. maybe it is the problem?

---

### Post by repsakkgn on 2010-01-24
i did  *sudo dpkg-reconfigure grub & * [I]sudo dpkg-reconfigure grub-pc & common
and at least now i'm able to see the output of fsck, perfomed by system during boot and some system messages too/ Things are getting better! but still there's just a blinking cursor after the messages , not the login prompt...
[/I]

---

### Post by repsakkgn on 2010-01-25
is there any chance to get help at this forum?

---

### Post by repsakkgn on 2010-01-25
where's the "friendly community "?

---

### Post by ratcheer on 2010-01-25
We've been friendly and we've been trying to help. Nobody seems to know how to fix your problem. Sorry.

Tim

---

### Post by lykwydchykyn on 2010-01-25
> **repsakkgn said:**
> where's the "friendly community "?

I resent this.  I tried to help, and I don't know the solution. Sorry I'm not a genius and a psychic.

The community is as friendly as you make it.  You're part of this community too, you know?

---

### Post by realzippy on 2010-01-25
I also cannot help you with your missing shell,but if you want to install the latest (195.xx) driver from NVIDIA without Alt+Ctrl+Fx (Assume you are on Karmic Koala):

Open terminal,type:

[B]sudo add-apt-repository ppa:nvidia-vdpau/ppa

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767

sudo apt-get update && sudo apt-get install nvidia-195-modaliases nvidia-glx-195

sudo reboot[/B]

---

### Post by repsakkgn on 2010-01-25
> **lykwydchykyn said:**
> 
The community is as friendly as you make it.
good words. I'll try to do my best. Anyway, thanx.

---

