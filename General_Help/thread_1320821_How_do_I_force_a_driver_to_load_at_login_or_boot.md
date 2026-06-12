---
title: "How do I force a driver to load at login or boot?"
date: 2009-11-09
forum: General Help
---

### Post by dixie460 on 2009-11-09
I have a Dell Inspiron 1545 with the atrocious Broadcom wireless module...I wish I had ordered it with the Intel unit instead. I plan on picking one up anyway and swapping it out. For now Id like some help forcing the wl.ko driver to load when I log in or start up my computer. Everytime I reboot, I have to open a terminal after I log in and do this:

andy@Rosemarie:~$ cd hybrid_wl
andy@Rosemarie:~/hybrid_wl$ sudo modprobe lib80211
[sudo] password for andy: 
andy@Rosemarie:~/hybrid_wl$ sudo insmod wl.ko
andy@Rosemarie:~/hybrid_wl$ 

Is there a way to force the driver to load? I added a line "wl" (without the quotes) to my /etc modules file, but it didnt help any. Do I need to put the folder containing the driver module in a certain location? Right now the module is in /home/andy/hybrid_wl and I'm not sure if having there is causing it not to load.

Also, I read that the Intel wireless chipset offered by Dell is more compatible with Ubuntu, is this true? If so, I'll snag one and swap it in place of the broadcom unit.

Thanks!!

---

### Post by Brandon Williams on 2009-11-10
Is there some reason why you need to use a different version of the Broadcom driver than the one that is part of standard ubuntu? The one that is installed if you use the 'Hardware Drivers' configuration GUI (jockey)? You can also just install bcmwl-kernel-source.

If that version doesn't work, then the documentation for the version that you're using should have installation instructions. What do those instructions tell you to do? It's probably something simple, like 'sudo make install'.

---

### Post by dixie460 on 2009-11-14
Apparently the driver included with ubuntu wont work. It just says No Network Available when I mouse over the network icon. I did get it working, after messing with it some more I finally got the driver to show up in the list under System > Admin > Hardware Drivers. Activated it and now it loads itself at boot.

Regards

Andy

---

### Post by jeb800e on 2009-11-14
Try installing NDISWRAPPER and download the driver for your wireless card.

Open us Synaptic Package Manager, and type in the search box "ndis". Check "ndiswrapper-common" and "ndisgtk". One or two more boxes will automatically be checked. Thats okay. Now click "Apply Changes".

Now go to System < Administration < Windows Wireless Drivers. Follow the instructions. You will need a downloaded or proprietary CD-ROM version of the driver/programs for the wireless card.

---

### Post by MaxIBoy on 2009-11-14
OK, my philosophy is to not only help you with your problem, but explain how the solution actually works. (I'm using parts of a canned tutorial I have on initscripts.) If you don't care about how it works, you just want it to work, you can skip the explanations, but if you read them you'll learn interesting things about how Ubuntu works.




If what you need can be accomplished with just a couple console commands, its very easy to do. Just create a shell script for it! A shell script is just a list of commands which are executed in order as if they were a program.

Make a file called wireless-drivers.sh and put this in it:
```
#! /bin/sh
cd /etc/hybrid_wl
modprobe lib80211
insmod wl.ko
```

To explain:

 You don't need the sudo there because this script is going to be run as  root anyway. That's because we will make it an initscript (which is run at startup time.)

The "#!" on the first line (must be the exact first two characters of the file) is what we call a "shebang." It basically means "open me with," in this case "open me with /bin/sh." /bin/sh is what is parsing your commands as you type them from the command line, but it can open a file with commands just as easily.

I also suggest moving your hybrid_wl directory to /etc/ instead of your home folder, that's simply a better place for it. If you want to leave it where it is, adjust that script as needed. However, keep in mind that "~" and "$HOME" will go to /root and not your normal home folder, because that's where the root user's home directory is.

Now, to make this script into an initscript, first we move it to /etc/init.d/ and allow it to run as an executable:
```
mv wireless-drivers.sh /etc/init.d/
sudo chmod +x /etc/init.d/wireless-drivers.sh

```

Now we will make it an initscript. If you want the driver to start up on both normal and recovery mode, make a link to it in /etc/rcS.d like this:
```
sudo ln -s /etc/init.d/wireless-drivers.sh /etc/rcS.d/S99wireless-drivers.sh
```
This creates a "symbolic link" (like a shortcut) from /etc/rcS.d/S99wireless-drivers.sh into /etc/init.d/wireless-drivers.sh. When Linux enters runlevel S as the first stage of its boot process, it will find that script there and run it. 

The "S" means that it should be started when entering the runlevel. ("K" would mean "kill.") 

The 99 just means that it should be executed after everything else in runlevel S. If you used "00" it would run before everything else, but you need to allow the other initscripts to set stuff up first before you can modprobe things.

Ubuntu uses upstart for its boot/shutdown process, but upstart is backward-compatible with SysV Init, and that's easier for me to use, so we'll go with that. SysV Init first appeared in System V Unix as a way to switch between [runlevels](http://en.wikipedia.org/wiki/Runlevel). The boot process is basically the process of going from no runlevel at all (just the kernel) to the runlevel at which you normally use the computer. 

The first runlevel it always goes to is runlevel S, which sets some really basic things up. (Like hardware drivers.) For single-user (recovery) mode it will then go to runlevel 1. For normal mode, on Debian/Ubuntu it will go to runlevel 2. 

Each runlevel is described as a list of initscripts, which are shell scripts as I've described before. All the initscripts are stored in /etc/init.d. The different runlevels are in /etc/rcS.d, plus /etc/rc0.d through /etc/rc6.d. In Ubuntu, /etc/rc2.d through rc6.d are the same by default and the default choice is rc2.d. (RC stands for run-control-- the scripts are run in order to control stuff.) 

You give the shortcuts in thes runlevel folders different names to control when and how they are run. Scripts with names starting in "K" mean that the script will be used to "kill" something. Scripts with names starting in "S" mean that the script will  be used to "start" something. In our case, this is not an important distinction. Our script is very simple and doesn't make the distinction. But its good form to use "S" if you want to use the script to start something. Then comes a two-digit number describing when the script should be run. For example, a simple runlevel might look like this:
```
K00something_we_dont_need_running_anymore.sh
S01first_thing_we_need_to_start.sh
S01this_also_starts_first_thing.sh
S05this_goes_next.sh
S10this_goes_after_that.sh
S80this_is_the_last_step.sh
```

You can change your boot order by renaming the symbolic links with different numbers, but that's for advanced users.

---

### Post by dixie460 on 2009-11-24
Thanks for the NDISwrapper suggestion jeb800e.  MaxIBoy, thanks for the long and detailed explanation, I really appreciate it as I am new to Linux yet and still learning. I love it so far, never going back to windoze again. :)

---

