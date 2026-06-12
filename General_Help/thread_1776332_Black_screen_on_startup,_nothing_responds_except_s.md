---
title: "Black screen on startup, nothing responds except shutdown. 10.04 on a netbook"
date: 2011-06-06
forum: General Help
---

### Post by dissembly on 2011-06-06
Hi all,

I have an ASUS 1215NPU2 netbook with an nVidia ion graphics card.

This morning I installed Ubuntu 10.04 from a USB (no CD drive on a netbook), and everything went perfectly smoothly. I shut it down and restarted, and it started fine.

I changed my desktop around, installed the wireless driver, successfully got wireless, then downloaded a whole bunch of programs with synaptic. I also installed the driver that Ubuntu (System -> Administration -> Hardware Drivers) recommended for the nVidia card.

Everything was fine, except I had to restart to use the graphics card driver.

I did this just then, and it has come up with a black screen. None of the keys on the keyboard respond. There was no startup chime (as there had been earlier). Nothing happens at all.

I pressed the physical shutdown/startup key, and it brings up the Ubuntu shutdown screen (with the five dots that progressively light up untill it all shuts down).

I can enter the BIOS, and I can press the shutdown key. That's all I can do. There is no other option provided at any stage. No other keys respond.

Can anybody help?

- David

---

### Post by papibe on 2011-06-06
There are various tips in this [thread]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=black").

Regards.

---

### Post by dissembly on 2011-06-06
Okay, I tried following the flowchart, and it's made things worse.

I got to step 3, and found a GRUB menu that allowed me to select recovery mode.

I did this, and now I have a black screen that won't go away at all. Pressing the shutdown button does nothing this time. It's completely frozen!

edited to add:

Okay, I tried some key combinations, and Ctrl + Alt + Del allowed me to shut it down. But now I'm back to square one. I have no idea what to do, the troubleshooting thread seems dependent on being able to get into a text console. But I can't do anything. Is there a way to use to bootable USB to trouble-shoot it?

---

### Post by dissembly on 2011-06-06
I've booted from the USB to see what the details of the graphics driver are. If it makes any difference at all, the information that comes up under "System -> Administration -> Hardware Drivers" is:
> 
NVDIA accelerated graphics driver (version current) [Recommended]
Tested by the Ubuntu developers
License: Proprietary
3D-accelerated proprietary graphics driver for NVIDIA cards

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards,
as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and
will not be able to run software that requires 3D acceleration, such as some
games.I kept the wireless off so that I could see what address/file name the actual package has (because then an error message comes up telling me the address it tried (and failed) to download from), and it is:> [http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_195.36.08-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_195.36.08-0ubuntu2_i386.deb)I assume "nvidia-settings_195.36.08-0ubuntu2_i386.deb" is the driver.

I can't see any option in the USB booted desktop to troubleshoot an existing installed operating system, or anything like that.

---

### Post by dissembly on 2011-06-06
Okay, the problem is unequivocally the NVIDIA graphics card driver. I just re-installed Ubuntu 10.04 from scratch, set up wireless, shut down, restarted with no problem, installed NVIDIA driver (as per last post), shut down, restarted - black screen.

Exactly the same symptoms as before - pressing the physical shutdown button brings up the Ubuntu "shutting down" screen; holding "shift" during startup brings up the options for loading it in recovery mode - which doesn't do anything besides make the problem slightly worse; other than that, I see nothing of Ubuntu at all. Just a black screen with an unresponsive keyboard.

Can anyone maybe offer advice now that I've narrowed it down to the NVIDIA driver that "System -> Administration -> Hardware Drivers" recommends to install - which are supposed to be Ubuntu tested?

I guess I could still use the netbook by re-installing Ubuntu a third time and forgetting about the fact that I have a graphics card, but I went out of my way to find a netbook with a graphics card for which Linux drivers are supposedly available. It would be a bit of a waste.

---

### Post by dissembly on 2011-06-06
Help, I think I've made the situation worse.

I found this thread: [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

And followed the instructions to the letter.

However, it did not work. It got to the very last stage, and then a message came up saying that nvidia drivers refused to install because I was running an "X server" (?), and that I should look for the readme file on the nvidia driver download website to explain how to install.

I looked, and there is no such readme file. There are a few "help" pages, none of which seemed to have any information relevant to this problem.

Then I found this post: [http://ubuntuforums.org/showthread.php?p=9211609#post9211609](http://ubuntuforums.org/showthread.php?p=9211609#post9211609)

Because it says something about removing "xserver-xorg-video-nouveau", I thought, maybe that will fix it?

So I began to follow the instructions in that post. I wrote:> sudo gdm-stop... which is the first instruction that I hadn't actually done already.

Immediately my desktop disappeared and my screen went to a black screen that says:> fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 136991/30154752 files, 2432493/120593920 blocks
* Starting AppArmor profiles  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                     {ok}
* Setting sensors limits     {ok}
* Speech-dispatcher configured for user sessions
* Starting Common Unix Printing System: cupsdAnd my computer appears to be frozen there. I have no idea why, i have no idea what's going on, or why nobody mentioned this in the thread containing the instructions i've followed...! Can someone please help?

---

### Post by dissembly on 2011-06-06
Okay, I pressed shut down, and it shut down.

I looked around again on the nVidia website, and eventually found this:

[http://us.download.nvidia.com/XFree86/Linux-x86/270.41.19/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86/270.41.19/README/installdriver.html)

It told me that to stop "X server" from running, and to enable me to attempt to install the nVidia driver from the website, I had to change the "run level". I googled that for a bit, and eventually found the name of the file I need to edit (which apparently isn't "/etc/inittab", which the nVidia guide thought it would be), and edited it to runlevel "1" (it was set at 2).

Then i rebooted.

Now I have a black screen that does not respond to the physical shutdown button (or to "Ctrl-Alt-Del") as my other black screens have.

Can somebody please help? I'm just flailing about here. Everything I've tried has either been a dead-end or made the situation worse.

Now I don't know how I can get out of the current black screen without unplugging the machine and removing the battery (which I've always been told was not something you're supposed to do), and then re-installing Ubuntu from scratch (which will be my fourth install since this morning, setting me back to square one again).

---

### Post by dissembly on 2011-06-19
Ok, well, I have given up on using an nVidea driver at all. I've used it for a week now without it, and I'm just too afraid of rendering the machine unusable again, so Ill probably just stay away from video card drivers entirely.

If anyone ever comes across this thread with advice on the issue, I'd realllly appreciate it, and will be receiving reply notifications.

---

