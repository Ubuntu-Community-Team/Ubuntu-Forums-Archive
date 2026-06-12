---
title: "Ubuntu 10.04 and Nvidia cards"
date: 2010-04-30
forum: General Help
---

### Post by arizonagirl11 on 2010-04-30
Hello everyone. I am having a big problem. I just installed the newest Ubuntu, 10.04 I believe the number is. It found my video card driver without a problem. it asks me to reboot. I reboot, and I get an error telling me that Ubuntu has to run in low graphics mode. So then, when I open the software for my graphics card, I get this...

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I do not know what to do in order to fix this. Can anyone please help me? Thanks.

---

### Post by dino99 on 2010-04-30
on top panel, goto system --> admin --> synaptic and search for nvidia

you might have these packages installed:

- nvidia-current
- nvidia-common
- nvidia-current-modaliases

as lucid dont need xorg.conf by default, into console run:

sudo rm -f /etc/X11/xorg.conf

reboot

then goto system --> admin --> hardware driver, to see if nvidia-current is activated, you should have now your full resolution.

---

### Post by wfp on 2010-04-30
Try this from a terminal ~$ sudo apt-get install nvidia-current

After it installs reboot again.

---

### Post by Badingo on 2010-04-30
Similar symptoms.
 
In Kernel 2.6.32 I'm stuck with lower resolution graphics with the "You do not appear to be using the NVIDIA X driver..."
 
In Kernel 2.6.31 I get the chance to reset my graphics configuration. After doing that I get full 1920 x 1200 resolution. I also show no proprietary drivers in use after a restart.

---

### Post by arizonagirl11 on 2010-04-30
Thank you. Unfortunately, it is still not working. I was so hoping I would be able to get Ubuntu working with this new version :(

---

### Post by dino99 on 2010-04-30
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure nvidia-current

watch .xsession-errors and logs (system - admin - log viewer)

---

### Post by arizonagirl11 on 2010-04-30
I got an error saying that jockey was not installed. The other command went through, but still, my graphics is not working.

---

### Post by arizonagirl11 on 2010-04-30
I looked up Jockey, and I do indeed have it, so not sure why I got that error. Time for bed for me. If anyone else has any other ideas, I would really appreciate it. It looks like I might have to bite the bullet, and just go and buy Windows 7.

---

### Post by dino99 on 2010-04-30
> **arizonagirl11 said:**
> I looked up Jockey, and I do indeed have it, so not sure why I got that error. Time for bed for me. If anyone else has any other ideas, I would really appreciate it. It looks like I might have to bite the bullet, and just go and buy Windows 7.

my bad its jockey-gtk

---

### Post by cenwesi on 2010-04-30
why not get the latest driver from Nvidia site. Stop GDM and login as root (cli) and install. Restart GDM and login as normal

---

### Post by arizonagirl11 on 2010-04-30
well, I downloaded the newest driver from the nvidia site. The driver name is

NVIDIA-Linux-x86.195.36.24-pkg1(2).run


But I have no clue what to do with it now :(

---

### Post by Vaphell on 2010-04-30
assuming it resides on your desktop
launch terminal

```

cd Desktop
chmod +x NVIDIA-Linux-x86.195.36.24-pkg1(2).run
sudo ./NVIDIA-Linux-x86.195.36.24-pkg1(2).run

```

1. goto Desktop 2. make installer an executable file 3. execute it with admin rights to install

name of the installer is complicated but you don't need to type it, use tab to autocomplete after first few letters
or better yet, select the text of commands here and paste it with middle click into terminal without deselecting - the easiest way to perform terminal magic from online hints and tutorials

---

### Post by arizonagirl11 on 2010-05-01
I have no idea what I am doing wrong. I tried that but got this error...

kimberly@kimberly-tower:~$ cd Desktop
kimberly@kimberly-tower:~/Desktop$ chmod +x NVIDIA-Linux-x86.195.36.24-pkg1(2).run
bash: syntax error near unexpected token `('
kimberly@kimberly-tower:~/Desktop$ sudo ./NVIDIA-Linux-x86.195.36.24-pkg1(2).runbash: syntax error near unexpected token `('
kimberly@kimberly-tower:~/Desktop$ 



Should I give up? Maybe Ubuntu isn't right for me :(

---

### Post by jmszr on 2010-05-01
arizonagirl11,

This may be of help: [http://www.ubuntugeek.com/incompatibility-with-nvidia-upstream-driver-installer-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/incompatibility-with-nvidia-upstream-driver-installer-in-ubuntu-10-04-lucid.html)

Edit: Did you run 'sudo nvidia-xconfig' in the terminal and restart the X-server?

---

### Post by arizonagirl11 on 2010-05-01
how do you restart the x server?

---

### Post by arizonagirl11 on 2010-05-01
I rebooted after doing that, but the video card is still not working. I am being told in the hardware drivers that the driver is activated, but not in use.

---

### Post by arizonagirl11 on 2010-05-01
it says at bootup that the driver was found, but it could not detect any usable configurations.

---

### Post by jmszr on 2010-05-01
arizonagirl11,

Here are a couple of threads that may be of use to you: [http://ubuntuforums.org/showthread.php?p=9001547](http://ubuntuforums.org/showthread.php?p=9001547) and: [http://ohioloco.ubuntuforums.org/showthread.php?t=1386207](http://ohioloco.ubuntuforums.org/showthread.php?t=1386207)

---

### Post by arizonagirl11 on 2010-05-01
Thank you everyone for your help. I have attempted everything that are in these threads, however, my Ubuntu is still not working properly. I continue to get the same errors. Ubuntu has to start in low graphic settings. I get that the driver is loaded, but not active, or however it's worded. I tried everything here.

According to the sites in which I have read, it appears that it is a bug in Ubuntu. Which, if this is true, the bug would have to be eliminated, and unless I missed it, none of those links described how to eliminate the bug.

I have spent several days on this, hours at a time. Still, it is not working. I read how that the computer will read that the driver is not active, but it is working, and the computer works fine. My computer does work, until I try to access games that need the graphics. 

I"m kind of at a loss. I so didn't want to give my money to Microsoft, but I think that may have to be the result in the end. It seems that Ubuntu (linux) is only for those who know what they are doing. Unfortunately, I am not one of those people.

Thank you to everyone who have attempted to help me. Unfortuantely, it's obvious to me that this is a losing battle for me.

Good luck to those who have this problem. And thanks again.

Kimmy

---

### Post by mattlopezdias on 2010-05-01
I had a similar problem in a new install of 10.04 lucid.

It would boot but stall at the splash screen, or just boot into safe graphics low-res mode.

my fix:
Booted up into recovery low graphics mode.
Removed the proprietary nvidia driver (in: System>Admin>Hardware Drivers)
Removed /etc/X11/xorg.conf
Rebooted normally, this gave me the correct resolution back.
I then added back the nvidia proprietary driver. (in: System>Admin>Hardware Drivers)

rebooted and has been fine since

---

### Post by Mr. Moustache on 2010-05-01
> **mattlopezdias said:**
> my fix:
Booted up into recovery low graphics mode.
Removed the proprietary nvidia driver (in: System>Admin>Hardware Drivers)
Removed /etc/X11/xorg.conf
Rebooted normally, this gave me the correct resolution back.
I then added back the nvidia proprietary driver. (in: System>Admin>Hardware Drivers)

rebooted and has been fine since

I have the same problem, but your "fix" does not work here...
But I found another "workaround":

After reboot choose "low graphics mode" or just log in directly into the terminal.

In terminal enter:

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm restart

The GUI restarts and works fine with the NVIDIA-driver.

Unfortunately: at the next reboot you have to do it again...
But until a fix comes out, I can live with that, because my systems runs 24/7 anyway. ;)

---

### Post by GSF1200S on 2010-05-01
Open a terminal and type:
```
sudo apt-get update
```
Leave it open, and browse to: System>Administration>Hardware Drivers and enable the latest Nvidia drivers.

Go back to the terminal and type:
```
sudo nvidia-xconfig
```

*NOTE: This shouldnt be necessary, but as many users have had issues getting TO the desktop in 10.04, I suggest a precautionary measure. Run the following command:
```
sudo gedit /etc/default/grub
```
and search for the line that says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and change it to:
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
``` (Note: This will make it "ugly" by showing you all kinds of text at boot. You can try leaving quiet splash in there if this thought disturbs you, but numerous have had issues with these options enabled).
Save and exit gedit.
Go back to the terminal and type:
```
sudo update-grub
```

Then reboot and hopefully its working :)

---

### Post by isr.igo on 2010-05-01
> **mattlopezdias said:**
> I had a similar problem in a new install of 10.04 lucid.

It would boot but stall at the splash screen, or just boot into safe graphics low-res mode.

my fix:
Booted up into recovery low graphics mode.
Removed the proprietary nvidia driver (in: System>Admin>Hardware Drivers)
Removed /etc/X11/xorg.conf
Rebooted normally, this gave me the correct resolution back.
I then added back the nvidia proprietary driver. (in: System>Admin>Hardware Drivers)

rebooted and has been fine since


hello,

i did as suggested , and my resolution is 1280x780 (it should be 1200x800) and drives are activated but aren't in use ...

and for these settings:
pci@0000:01:00.0   display  G98 [GeForce 9200M GS]
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
nvidia-current, 195.36.15, 2.6.32-21-generic, i686: installed

i get in Xorg.0.log:

(EE) [drm] failed to open device
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


but when i do nvidia-xconfig i get messed up screen

---

### Post by arizonagirl11 on 2010-05-01
I tried all of this, nothing works. I don't know if this will help or not, but I am running the nvidia graphics card called GeForce 9500 GT.

I tried everything that everyone has suggested, yet still, I am at square one :( Thank you though. your help is much appreciated.

---

### Post by sendblink23 on 2010-05-01
> **isr.igo said:**
> hello,
i did as suggested , and my resolution is 1280x780 (it should be 1200x800) and drives are activated but aren't in use ...

and i get (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

but when i do nvidia-xconfig i get messed up screen

sorry but i gotta smile at the windows 7 background :)


@ arizonagirl11
Anyways did you try instead on using 10.04, download 9.10 version and try it out... maybe it works better for you... I'm just suggesting this to you since you have tried various things already mentioned and nothing is honestly making a fixable solution for you.

---

### Post by arizonagirl11 on 2010-05-01
yes actually, I did. And I liked it, However, a week after installing it, I got a kernel panic, and could not do anything with the computer anymore. From my other computer, I tried getting help through the Ubuntu forums, and everyone was telling me that they got the same problem with it, and no one knew why, or how to fix it. So that really scared me away from that version of Ubuntu. It seems once that happens, the computer is garbage, and you have to reformat the whole thing. 

I did a search on it to see if it has been fixed at all, but found that people still had that problem. So I waited for this version to come out. Now, I am thinking of using this or text stuff, and vista for my games, until I can afford Windows 7 *cringe*

---

### Post by Majorflam on 2010-05-02
> **GSF1200S said:**
> Open a terminal and type:
```
sudo apt-get update
```
Leave it open, and browse to: System>Administration>Hardware Drivers and enable the latest Nvidia drivers.

Go back to the terminal and type:
```
sudo nvidia-xconfig
```

*NOTE: This shouldnt be necessary, but as many users have had issues getting TO the desktop in 10.04, I suggest a precautionary measure. Run the following command:
```
sudo gedit /etc/default/grub
```
and search for the line that says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and change it to:
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
``` (Note: This will make it "ugly" by showing you all kinds of text at boot. You can try leaving quiet splash in there if this thought disturbs you, but numerous have had issues with these options enabled).
Save and exit gedit.
Go back to the terminal and type:
```
sudo update-grub
```

Then reboot and hopefully its working :)

I'm having display problems after an upgrade last night. I'm trying your fix, but when I reach this stage:

```
sudo nvidia-xconfig
```

I get this error in terminal:

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

Could this be my problem?

---

### Post by arizonagirl11 on 2010-05-02
when I do sudo apt-get update, I get this...

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.




Then at the second step,  
sudo nvidia-xconfig   I get this...


WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


Perhaps that is why it won't work for me? Any suggestions?

---

### Post by GSF1200S on 2010-05-02
> **Majorflam said:**
> I'm having display problems after an upgrade last night. I'm trying your fix, but when I reach this stage:

```
sudo nvidia-xconfig
```

I get this error in terminal:

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

Could this be my problem?

I get the exact same message with the latest updates, yet the changes made (in my case enabling a second monitor) work fine. I would ignore that message for now. You can alternatively do:
```
sudo nvidia-settings
```
and under X Server Display Configuration, click "Save to X Configuration File." You will get the same error (as I did). Since you have not mentioned, are you having the exact same issue as the OP?

---

### Post by GSF1200S on 2010-05-02
> **arizonagirl11 said:**
> when I do sudo apt-get update, I get this...

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.




Then at the second step,  
sudo nvidia-xconfig   I get this...


WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


Perhaps that is why it won't work for me? Any suggestions?

Were you connected to the internet when you ran:
```
sudo apt-get update
```
Whenever it says fail to fetch, its because APT cannot establish a connection with the server its trying to update from. I had your exact error when I attempted to chroot into another partition and forgot to copy /etc/resolv.conf from the running install to the chroot'ed partition. In short, make sure you are linked to the internet when you run this command. You can double check you have an internet connection by opening a web browser to google or doing:
```
sudo ping -c 3 www.google.com
```
in a terminal.

---

### Post by GSF1200S on 2010-05-02
> **isr.igo said:**
> hello,

i did as suggested , and my resolution is 1280x780 (it should be 1200x800) and drives are activated but aren't in use ...

and for these settings:
pci@0000:01:00.0   display  G98 [GeForce 9200M GS]
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
nvidia-current, 195.36.15, 2.6.32-21-generic, i686: installed

i get in Xorg.0.log:

(EE) [drm] failed to open device
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


but when i do nvidia-xconfig i get messed up screen

I have a question- do you have one of those laptops that has both an intel graphics card as well as an Nvidia card? If so, this might be a complicated fix. Ill have to research this, as I only have Nvidia cards.

---

### Post by arizonagirl11 on 2010-05-02
Yes, I am connected to the internet when I tried that. my problem is, the video card driver is there, it is installed and activated, but it is not "in use", and nothing I can do will make it "in use".

---

### Post by GSF1200S on 2010-05-02
> **arizonagirl11 said:**
> Yes, I am connected to the internet when I tried that. my problem is, the video card driver is there, it is installed and activated, but it is not "in use", and nothing I can do will make it "in use".

I dont know why this is being such a pain. Lets try one more set of steps and see if it works.

Open a terminal and do:
```
sudo -i
```
and enter your password. Then do:
```
apt-get purge nvidia-current nvidia-common nvidia-current-modaliases
apt-get update
apt-get install -f
dpkg --configure -a
dpkg-reconfigure -phigh xserver-xorg

```

Then (and this will restart X, so make sure everything you are doing is saved) do:
```
sudo /etc/init.d/gdm restart
```
When X reloads, you will be in low graphics mode. Then, open Hardware Drivers, and see if the Nvidia driver is displayed. If not, close Hardware Drivers, go to a terminal and type:
```
sudo -i
```
enter your password and then do:
```
apt-get install nvidia-current-modaliases
apt-get update
```
Then open Hardware Drivers again and enable the driver (it should be there, but if its not see below). After thats done, reboot as Ubuntu suggests. 

If Ubuntu decides you need to struggle and the Nvidia driver STILL isnt listed in Hardware Drivers (ONLY do this next step if nothing showed in Hardware Drivers), then do:
```
sudo -i
```
enter your password, and then do these commands:
```
apt-get install nvidia-current
nvidia-xconfig
```
Then restart the computer and pray ;)

Again, it shouldnt be anywhere this difficult. I have 2 nvidia cards in SLI mode and all I needed to do, literally, was open Hardware Drivers, enable the recommended drivers, and reboot. Done. Im still trying to figure out why and how you are having an issue.

---

### Post by arizonagirl11 on 2010-05-02
Nope. Same error. "This driver is activated" but currently not in use". 

I do find that I get errors when trying to access that conical web site to get things. I dunno. I think getting ubuntu to work is something I need to declare impossible. Thanks again for your help. I guess Linux is just not right for me.

---

### Post by GSF1200S on 2010-05-02
> **arizonagirl11 said:**
> Nope. Same error. "This driver is activated" but currently not in use". 

I do find that I get errors when trying to access that conical web site to get things. I dunno. I think getting ubuntu to work is something I need to declare impossible. Thanks again for your help. I guess Linux is just not right for me.

Well, perhaps. I think you came in at a bad time- Ubuntu just did a big LTS (long term service) release and inevitably when they are trying to make Ubuntu work on every computer some people are going to have problems- you happen to be one of them :(. I would suggest, if youre interested, trying to download Ubuntu again in a few months once they get the initial bugs worked out and doing a clean install. When you adopt early, like right after release, you stand a good chance to run into issues. The community is where Linux must test, because unfortunately OEM's dont usually bundle Linux with their computers. The Ubuntu community will be here when/if you ever change your mind ;)

---

### Post by GSF1200S on 2010-05-02
If you are still willing to give this a final try (your choice), run the following command and place the contents of that file in a reply here. Im going to have you replace the Driver line with the Nvidia driver and see what the error message is in xorg.log.

---

### Post by arizonagirl11 on 2010-05-02
ok so after nosing around a bit, I tried once again the driver from nvidia site. I almost got it to go into the system, but it says I need to be root. I have the driver onmy desktop, how do I login as root?? I am listed as root in the terminal after doing sudo -i, but that's not good enough for the program.

---

### Post by arizonagirl11 on 2010-05-02
I would love to give it another try. I really want Ubuntu to work. I have a really old version on my other computer, and it works real nice. Had it for years, never had to reinstall, or anything. So I should go and redo all those steps, and then paste the results?

---

### Post by GSF1200S on 2010-05-03
> **arizonagirl11 said:**
> ok so after nosing around a bit, I tried once again the driver from nvidia site. I almost got it to go into the system, but it says I need to be root. I have the driver onmy desktop, how do I login as root?? I am listed as root in the terminal after doing sudo -i, but that's not good enough for the program.

You cant run it while X is running- you have to kill X. Im gonna tell you how to do this, so refresh this page in a little bit- ill be editing this post.

**EDIT 1** Also, how do you connect to the internet? If its ethernet, no problem. If its wireless, then we might have an issue. Working on Edit 2...

**EDIT 2** Before we do the below portion, would you mind posting the contents of:
```
sudo gedit /etc/X11/xorg.conf
```
and
```
sudo gedit /var/log/Xorg.0.log
```
so I can see whats going on?

PROCESS FOR INSTALLING NVIDIA DRIVERS FROM WEBSITE:
Ok, lets try the drivers from the site. You might want to print this page out so you have a copy to use when you dont have X (the graphical stuff).

First off, I would suggest changing the name of the nvidia driver to something easier like:
> nvidia.run
that way you dont have to type the long name when you go to run it. Make sure its on your desktop.

Next, lets remove all the existing nvidia drivers. Open a terminal and do:
```
sudo -i
```
then enter your password. Then do:
```
apt-get purge nvidia-current nvidia-common nvidia-current-modaliases
```
Then, kill GDM (**You will LOSE the desktop at this point** GDM is running the desktop you are on):
```
/etc/init.d/gdm stop
```
If it asks you to login, do so. If its sitting at username@computer-name, then proceed to the next command:
```
sudo -i
```
and enter your password. Then:
```
sh /home/kimberly/Desktop/nvidia.run
```
Tell it yes to everything it asks, ignoring errors if necessary (but keep track of what they are so you can tell me). After its done, run:
```
nvidia-xconfig
```
and then reboot the computer using:
```
reboot
```
The nvidia drivers should be in use at this point. Unfortunately, this method will need to be repeated when a new kernel update comes out (just the killing gdm and running the nvidia driver part).

Im still trying to figure out why the Hardware Drivers window isnt working.

---

### Post by SFCampbell on 2010-05-03
I'm just catching up to you guys with 10.04 and I experienced the exact same problem.  **Please anyone having troubles, try this and tell me if it works for you**, because *it worked for me*.

I haven't had to reconfigure an X-server in almost 2 years since the Hardware manager was built into Ubuntu, so I believe the problem is instead a driver conflict.  In another post (sorry, I would like to give credit but I lost the link) I found a list of potentially conflicting drivers that I added to my blacklist.  Once I rebooted, my nVidia card has been working since.  Please try this:

**sudo gedit /etc/modprobe.d/blacklist.conf**

At the end of this file, paste the following:
[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]

It may have been pure luck and this was a circumstantial fix for my system, but I hope it may help others as well.

---

### Post by GSF1200S on 2010-05-03
> **SFCampbell said:**
> I'm just catching up to you guys with 10.04 and I experienced the exact same problem.  **Please anyone having troubles, try this and tell me if it works for you**, because *it worked for me*.

I haven't had to reconfigure an X-server in almost 2 years since the Hardware manager was built into Ubuntu, so I believe the problem is instead a driver conflict.  In another post (sorry, I would like to give credit but I lost the link) I found a list of potentially conflicting drivers that I added to my blacklist.  Once I rebooted, my nVidia card has been working since.  Please try this:

**sudo gedit /etc/modprobe.d/blacklist.conf**

At the end of this file, paste the following:
[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]

It may have been pure luck and this was a circumstantial fix for my system, but I hope it may help others as well.

arizonagirl11: I would highly suggest you try this BEFORE you do my method. The behavior you have seems to be odd, as it doesnt happen to me nor many others. Im actually gonna try this suggestion to see if it solves my framebuffer problem (cannot use the console outside of X or my monitor shuts off).

Even if it doesnt help, thanks for posting this SFCampbell :)

---

### Post by nanog on 2010-05-03
> when I do sudo apt-get update, I get this...

W: Failed to fetch [http://archive.canonical.com/ubuntu/...id/Release.gpg]("http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg")   Something wicked happened resolving 'archive.canonical.com:http' (-5 -  No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old  ones used instead.

This smells like an apt/deb issue to me.

If you are having problems with apt authentication, have broken packages, or corrupt packages none of the commands people are telling you to try will work. Its really important when asking for help to give all the output of failed commands. 


[LIST]
[*]Can you confirm that you are successfully accessing repos?
[*]Do you have any broken packages (see broken package filter in synaptic)?
[*]When you attempt to update or reinstall relevant packages do you get any errors.
[/LIST]

---

### Post by GSF1200S on 2010-05-03
> **nanog said:**
> This smells like an apt/deb issue to me.

If you are having problems with apt authentication, have broken packages, or corrupt packages none of the commands people are telling you to try will work. Its really important when asking for help to give all the output of failed commands. 


[LIST]
[*]Can you confirm that you are successfully accessing repos?
[*]Do you have any broken packages (see broken package filter in synaptic)?
[*]When you attempt to update or reinstall relevant packages do you get any errors.
[/LIST]

Actually man, im trying to research this. I stumbled onto a thread that listed this as a bug with sudo (somehow). This is why youll notice I switched from giving sudo apt-get install commands to logging in as root first (sudo -i)- Im trying to find out more about this. You are right though- if apt isnt working, she isnt going to get the drivers installed...

---

### Post by arizonagirl11 on 2010-05-03
here are the logs from the two commands...

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Fri Mar 12 01:42:27 PST 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection





AND



X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux kimberly-tower 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=6bca0ca7-b033-466e-a99a-30148447aba6 ro nomodeset
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May  2 21:57:50 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0640:19f1:0943 nVidia Corporation G96 [GeForce 9500 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/524288
(--) PCI: (0:2:4:0) 14f1:5b7a:0070:7400 Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xe8000000/67108864
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) May 02 21:57:51 NVIDIA(0): Enabling RENDER acceleration
(II) May 02 21:57:51 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 02 21:57:51 NVIDIA(0):     enabled.
(EE) May 02 21:57:51 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) May 02 21:57:51 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) May 02 21:57:51 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) May 02 21:57:51 NVIDIA(0):     README for additional information.
(EE) May 02 21:57:51 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by nanog on 2010-05-03
if its a sudoers problem then they should be able to create a new user and install the drivers there. there are usually simple solutions to these problems but its really hard to help without detailed error logs. 

arizonagirl, if you want to get to the bottom of this its good practice to past in your log files (for example go to system-->administration-->log file viewer and paste syslog, dmesg, and xorg). if you are running commands sometimes the error messages flash by and are hard to capture. this is the solution

```
command_with_errors  [FONT=monospace][/FONT]>>errorlog 2>&1
```

---

### Post by nanog on 2010-05-03
[FONT=monospace]Exact error output from these commands that [/FONT][GSF1200S]("http://ubuntuforums.org/member.php?u=261396") posted earlier[FONT=monospace] would really help:


[/FONT]```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get install nvidia-current-modaliases
sudo apt-get install nvidia-current
```

---

### Post by arizonagirl11 on 2010-05-03
Ok, I am connected via ethernet. Adding those files to the blacklist didn't seem to do anything on my end. I checked the updater, and got these errors...

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

I have no broken packages.

As for the repositories, I do not believe I am getting those correctly.

For the code...   
[sudo] password for kimberly: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Fetched 189B in 11s (16B/s)                                                    
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kimberly@kimberly-tower:~$ 

kimberly@kimberly-tower:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kimberly@kimberly-tower:~$ 




kimberly@kimberly-tower:~$ sudo dpkg --configure -a
kimberly@kimberly-tower:~$ 



kimberly@kimberly-tower:~$ sudo apt-get install nvidia-current-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current-modaliases is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kimberly@kimberly-tower:~$ 


kimberly@kimberly-tower:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kimberly@kimberly-tower:~$

---

### Post by nanog on 2010-05-03
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource  temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is  another process using it?
```

Yep, apt authentication is not working due to a lock. You need to kill all programs using apt and/or restart. In fact, why don't you just restart.

You should then be able to get this to work using [GSF1200S]("http://ubuntuforums.org/member.php?u=261396") instructions:

[http://ubuntuforums.org/showpost.php?p=9223031&postcount=33](http://ubuntuforums.org/showpost.php?p=9223031&postcount=33)

---

### Post by nanog on 2010-05-03
One other thing...make sure you have dkms installed.

---

### Post by standingwave on 2010-05-03
> **SFCampbell said:**
> **sudo gedit /etc/modprobe.d/blacklist.conf**

At the end of this file, paste the following:
[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]

It may have been pure luck and this was a circumstantial fix for my system, but I hope it may help others as well.Huzzah! This seemed to work for me. I was pulling my hair out last night (at my age I don't have much left) and I was this -><- close to giving up and going back to Karmic but I made these edits before running the NVIDIA (.run) installer. Now extra effects are back! You don't realize how much you miss OpenGL until you don't have it for a couple of days!

Now to not touch anything. Ah, who am I kidding?

---

### Post by nanog on 2010-05-03
blacklisting is not the preferred way to handle this. you should really try to figure out why nvidia and jockey are not working correctly.

---

### Post by GSF1200S on 2010-05-03
> **nanog said:**
> ```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource  temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is  another process using it?
```

Yep, apt authentication is not working due to a lock. You need to kill all programs using apt and/or restart. In fact, why don't you just restart.

You should then be able to get this to work using [GSF1200S]("http://ubuntuforums.org/member.php?u=261396") instructions:

[http://ubuntuforums.org/showpost.php?p=9223031&postcount=33](http://ubuntuforums.org/showpost.php?p=9223031&postcount=33)

Maybe the OP just has Synaptic or the software center open? I know in Arch I can remove the lock file if I deem no process is using it- perhaps APT needs the same assuming the OP has nothing open?

---

### Post by arizonagirl11 on 2010-05-03
I am sooo jealous! Anyway, I did all that, rebooted, and redid all the stuff that gsf suggested. Here's what I got...



  	 	 	 	 	 	  kimberly@kimberly-tower:~$ sudo -i  
 [sudo] password for kimberly:  
 root@kimberly-tower:~# apt-get purge nvidia-current nvidia-common nvidia-current-modaliases  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Package nvidia-common is not installed, so not removed  
 The following packages will be REMOVED: 
   nvidia-current* nvidia-current-modaliases*  
 0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.  
 After this operation, 72.6MB disk space will be freed.  
 Do you want to continue [Y/n]? apt-get update  
 Abort.  
 root@kimberly-tower:~# apt-get update  
 Get:1 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [189B]                     
 Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US        
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                  
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                         
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                       
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US    
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US  
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US  
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages               
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages               
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources                
 Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                              
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US           
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources  
 Fetched 189B in 17s (11B/s)  
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 

 E: Some index files failed to download, they have been ignored, or old ones used instead.  
 root@kimberly-tower:~# apt-get install -f  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
 root@kimberly-tower:~# dpkg --configure -a  
 root@kimberly-tower:~# dpkg-reconfigure -phigh xserver-xorg  
 root@kimberly-tower:~#

---

### Post by GSF1200S on 2010-05-03
I would seriously try to install the drivers you downloaded from the site as I told you in EDIT 2 of an above post. 

Nanog has a good suggestion in showing us those logs. Paste the contents of the logs here as he suggested if you still want this whole Ubuntu thing to go.

Allow me to ask a few things though. Did you upgrade into 10.04? If not, perhaps you had whats called a "bad burn" and somehow your issues are related to that. Basically, a CD could get corrupted as it gets burned, and your issues could be related to this. You could try downloading a fresh Ubuntu 10.04 iso and burning it SLOWLY to a disc (at 4x is good). As ive said, usually there isnt so many issues with simple video drivers, especially as Ubuntu has evolved over the releases. Good luck, and if you try the drivers from the website as ive suggested, feel free to ask questions in this thread.

---

### Post by arizonagirl11 on 2010-05-03
ok, got a question. I attempted to install the driver that I downloaded from that nvidia site. But this is what I got. 

everything went well until I attempted to do this...

sh ~/Desktop/nvidia.run

I got


sh:can't open /root/desktop/nvidia.run

The actual location of this file is at

/home/kimberly/Desktop

I am guessing that is why It won't open. instead of going to /home/kimberly/desktop, it's trying to reach a desktop that is on the root account? how do I manage that?

---

### Post by GSF1200S on 2010-05-03
> **arizonagirl11 said:**
> ok, got a question. I attempted to install the driver that I downloaded from that nvidia site. But this is what I got. 

everything went well until I attempted to do this...

sh ~/Desktop/nvidia.run

I got


sh:can't open /root/desktop/nvidia.run

The actual location of this file is at

/home/kimberly/Desktop

I am guessing that is why It won't open. instead of going to /home/kimberly/desktop, it's trying to reach a desktop that is on the root account? how do I manage that?

Thats my fault :(.. recheck my instructions in that post in about five minutes- ill fix it..

**UPDATE** Fixed page 4 instructions..

---

### Post by arizonagirl11 on 2010-05-03
Thanks :D

---

### Post by todak on 2010-05-03
In a terminal type this ```
sudo nvidia-xconfig
``` That worked for me.

---

### Post by GSF1200S on 2010-05-03
> **todak said:**
> In a terminal type this ```
sudo nvidia-xconfig
``` That worked for me.

OP has tried this if you read the thread ;) and it didnt work.

---

### Post by arizonagirl11 on 2010-05-03
ok, we may be getting somewhere with information. This is what I got in way of errors...

Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidia/fb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s) or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.

Please see the log entries 'kernel module load error and 'kernel messages' at the end of the file /var/log/nvidia-installer/log' for more info.


When attempting to access that file, I get this...

kimberly@kimberly-tower:~$ /var/log/nvidia-installer.log
bash: /var/log/nvidia-installer.log: Permission denied
kimberly@kimberly-tower:~$ sudo -i
[sudo] password for kimberly: 
root@kimberly-tower:~# /var/log/nvidia-installer.log
-bash: /var/log/nvidia-installer.log: Permission denied
root@kimberly-tower:~#

---

### Post by GSF1200S on 2010-05-03
> **arizonagirl11 said:**
> ok, we may be getting somewhere with information. This is what I got in way of errors...

Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidia/fb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s) or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.

Please see the log entries 'kernel module load error and 'kernel messages' at the end of the file /var/log/nvidia-installer/log' for more info.


When attempting to access that file, I get this...

kimberly@kimberly-tower:~$ /var/log/nvidia-installer.log
bash: /var/log/nvidia-installer.log: Permission denied
kimberly@kimberly-tower:~$ sudo -i
[sudo] password for kimberly: 
root@kimberly-tower:~# /var/log/nvidia-installer.log
-bash: /var/log/nvidia-installer.log: Permission denied
root@kimberly-tower:~#

You have to open it with something. So, you would run for example:
```
sudo gedit /var/log/nvidia-installer.log
```
and then paste the contents here (this assumes you started the desktop with the command I put in the instructions..)

---

### Post by arizonagirl11 on 2010-05-03
Unfortunately, I need to go to bed, as I have work early in the morning. I will do whatever you suggest from here when I return from work, and will post my results. I really appreciate all your help. Thank you so much!

Kimmy

---

### Post by arizonagirl11 on 2010-05-03
AHH! Thank you! here is the log from that file.


nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun May  2 23:28:11 2010
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 195.36.24.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-21-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-21-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.32-21-gener
   ic/build SYSOUT=/lib/modules/2.6.32-21-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.2
   4-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude
    -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include includ
   e/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration 
   -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -
   mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtu
   ne=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -f
   stack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-
   sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mn
   o-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibli
   ng-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-ove
   rflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x8
   6-195.36.24-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-
   defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)"  -c -o /tmp/se
   lfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz216
   5/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv.o";
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.nv_
   gvi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibling-calls -pg -Wdec
   laration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-
   cfi-asm -fconserve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)
   =#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.tm
   p_nv_gvi.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv_gvi
   .c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration -Wno-format-security -fno-delete-
   null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-
   args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unw
   ind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv -Wall 
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195
   .36.24\" -UDEBUG -U_DEBUG -DNDEBUG 
    -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.
   36.24-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.2
   4-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-la
   rger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdec
   laration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-
   cfi-asm -fconserve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)
   =#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.tm
   p_os-agp.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/os-agp
   .c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include 
   -Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune
   =generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CF
   I_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mn
   o-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-
   pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tm
   p/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv -Wall -Wimplicit -Wr
   eturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith
   -Wno-multicha
   r -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KE
   RNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -D
   NDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_inter
   face)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2165/NVIDIA-
   Linux-x86-195.36.24-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz2165/NVID
   IA-Linux-x86-195.36.24-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregp
   arm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=ge
   neric -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack
   -protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-
   compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dn
   ow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-ca
   lls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow
   -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x86-195.
   36.24-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wcha
   r-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer
   -pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNV
   RM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-p
   kg1/usr/src/nv/.tmp_os-registry.o /
   tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gene
   ric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIG
   NAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibli
   ng-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-ove
   rflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x8
   6-195.36.24-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-
   defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNA
   ME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg
   1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/u
   sr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D
   __KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alia
   sing -fno-common -Werror-implicit-function-declaration -Wno-format-security 
   -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-stru
   ct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumula
   te-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCON
   FIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asy
   nchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-large
   r-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclar
   ation-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi
   -asm -fconserve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/
   src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -W
   parentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign
   -compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION
   _STRING=\"195.36.24\" -UDEBUG -U_DEB
   UG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nva
   cpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2165/NVIDIA-L
   inux-x86-195.36.24-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz2165/NVIDIA-Linu
   x-x86-195.36.24-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:27,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:95,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nv-linux.h:126,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-21-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz21
   65/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nvacpi.o";
     ld -m elf_i386   -r -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv_gvi.o /tmp/sel
   fgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz2165/N
   VIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/os-agp.o /tmp/selfgz2165/NVIDIA-Li
   nux-x86-195.36.24-pkg1/usr/src/nv/os-interface.o /tmp/selfgz2165/NVIDIA-Linu
   x-x86-195.36.24-pkg1/usr/src/nv/os-registry.o /tmp/selfgz2165/NVIDIA-Linux-x
   86-195.36.24-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.3
   6.24-pkg1/usr/src/
   nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/u
   sr/src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.32-21-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-21-generic/Modu
   le.symvers -I /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/M
   odule.symvers -S -w  -s
   WARNING: could not find /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -
   Iinclude  -I/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraph
   s -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wn
   o-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mre
   gparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=
   generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fsta
   ck-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overfl
   ow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2165/NVIDIA-Linux-x86-1
   95.36.24-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -W
   char-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-de
   fer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -
   DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /t
   mp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nvidia.mod.o /tmp/s
   elfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.32-21-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.32-21-generic/scripts/modu
   le-common.lds --build-id -o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/
   usr/src/nv/nvidia.ko /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src
   /nv/nvidia.o /tmp/selfgz2165/NVIDIA-Linux-x86-195.36.24-pkg1/usr/src/nv/nvid
   ia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Cannot allocate memory
-> Kernel messages:
   [   23.251561] pci 0000:01:00.0: setting latency timer to 64
   [   23.253492] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card
   (0x096000c1)
   [   23.253943] __ratelimit: 12 callbacks suppressed
   [   23.253946] vmap allocation for size 33558528 failed: use vmalloc=<size>
   to increase size.
   [   23.254160] [drm] nouveau 0000:01:00.0: Failed to init RAMIN mapping,
   limited instance memory available
   [   23.254186] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on
   minor 0
   [   23.356776] [TTM] Zone  kernel: Available graphics memory: 436860 kiB.
   [   23.356780] [TTM] Zone highmem: Available graphics memory: 1030206 kiB.
   [   23.356791] [drm] nouveau 0000:01:00.0: 1024 MiB VRAM
   [   23.356882] [drm] nouveau 0000:01:00.0: Error creating sgdma object: -12
   [   23.356886] [drm] nouveau 0000:01:00.0: Error initialising PCI(E): -12
   [   23.356959] [TTM] Trying to take down uninitialized memory manager type 1
   [   23.356990] [TTM] Zone  kernel: Used memory at exit: 0 kiB.
   [   23.356996] [TTM] Zone highmem: Used memory at exit: 0 kiB.
   [   26.184599] CPU0 attaching NULL sched-domain.
   [   26.184607] CPU1 attaching NULL sched-domain.
   [   26.212191] CPU0 attaching sched-domain:
   [   26.212196]  domain 0: span 0-1 level MC
   [   26.212199]   groups: 0 1
   [   26.212207] CPU1 attaching sched-domain:
   [   26.212210]  domain 0: span 0-1 level MC
   [   26.212213]   groups: 1 0
   [   34.587458] UDF-fs: Filesystem marked read-only because writing to
   pseudooverwrite partition is not implemented.
   [   34.736021] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp
   2010/04/14 18:07 (1e5c)
   [ 1032.866958] vmap allocation for size 10817536 failed: use vmalloc=<size>
   to increase size.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by frappe1 on 2010-05-03
Is your display hanging at seemingly random intervals?

---

### Post by KonaRurrik on 2010-05-03
I'm not sure if you've tried this, or is related but this has always worked for me:

1) Download corresponding package from [www.nvidia.com]("http://www.nvidia.com") (verify the architecture, 32 vs 64 bit is correct)

2) Do (assuming firefox downloads to ~/Downloads/) obviously replacing NVIDIA-Linux-x86-195.36.24-pkg1.run with whatever you just downloaded from NVIDIA:

```

kona@rurrik:cd Downloads/
kona@rurrik:sudo chmod +x NVIDIA-Linux-x86-195.36.24-pkg1.run
kona@rurrik:sudo service gdm stop
kona@rurrik:sudo ./NVIDIA-Linux-x86-195.36.24-pkg1.run
kona@rurrik:sudo service gdm start
```That has worked up through 9.10 with my computer (HP G60, Nvidia 8200m, dual Turion @ 2.1gHz)

However, and I'm not sure if this is related, but now my computer refuses to go into the terminal that is usually achieved by CTRL-ALT-F2. It goes, but then displays graphics card gibberish (blue, green, red dots and lines, drawn at random where display lines should be)

Any ideas on this?

@arizonagirl11
Still try the above procedure, as it works fine on another computer of mine in 10.04LTS.

---

### Post by GSF1200S on 2010-05-03
> **KonaRurrik said:**
> I'm not sure if you've tried this, or is related but this has always worked for me:

1) Download corresponding package from [www.nvidia.com]("http://www.nvidia.com") (verify the architecture, 32 vs 64 bit is correct)

2) Do (assuming firefox downloads to ~/Downloads/) obviously replacing NVIDIA-Linux-x86-195.36.24-pkg1.run with whatever you just downloaded from NVIDIA:

```

kona@rurrik:cd Downloads/
kona@rurrik:sudo chmod +x NVIDIA-Linux-x86-195.36.24-pkg1.run
kona@rurrik:sudo service gdm stop
kona@rurrik:sudo ./NVIDIA-Linux-x86-195.36.24-pkg1.run
kona@rurrik:sudo service gdm start
```That has worked up through 9.10 with my computer (HP G60, Nvidia 8200m, dual Turion @ 2.1gHz)

However, and I'm not sure if this is related, but now my computer refuses to go into the terminal that is usually achieved by CTRL-ALT-F2. It goes, but then displays graphics card gibberish (blue, green, red dots and lines, drawn at random where display lines should be)

Any ideas on this?

@arizonagirl11
Still try the above procedure, as it works fine on another computer of mine in 10.04LTS.

I listed the same procedure on Page 4 my second post edit 2, but the OP has still had problems.

Im having the same issues as you with switching TTY's.. my monitor just shuts off and I cant do anything but Ctrl+Alt+F7 back to X. If I kill GDM, i have to control alt delete to restart (unless im brave enough to type commands in the dark). I think its a bug in the latest Nvidia driver.

---

### Post by isr.igo on 2010-05-03
> **GSF1200S said:**
> I have a question- do you have one of those laptops that has both an intel graphics card as well as an Nvidia card? If so, this might be a complicated fix. Ill have to research this, as I only have Nvidia cards.

can this help ?: (i have samsung R510 p8400 don't know if i have on-board device)
 
gabriel@igor-pc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)

gabriel@igor-pc:~$ sudo lshw -C video
[sudo] password for gabriel: 
  *-display               
       description: VGA compatible controller
       product: G98 [GeForce 9200M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ce000000-ceffffff memory:d0000000-dfffffff(prefetchable) memory:cc000000-cdffffff ioport:2000(size=128)

---

### Post by KonaRurrik on 2010-05-03
> **GSF1200S said:**
> I listed the same procedure on Page 4 my second post edit 2, but the OP has still had problems.

Im having the same issues as you with switching TTY's.. my monitor just shuts off and I cant do anything but Ctrl+Alt+F7 back to X. If I kill GDM, i have to control alt delete to restart (unless im brave enough to type commands in the dark). I think its a bug in the latest Nvidia driver.


Sorry about the repost then! 

At least your CTRL+ALT+F7 command works, for some reason mine flashes as if its trying to get back to the active Xserver, but then fails to. I'll try rolling back to the 185 driver or the 173 if needed.

---

### Post by tekkidd on 2010-05-03
I would recomend installing graphics drivers from the nvidia website because they are more current than the ones supplied with lucid. To do this 

1) Go to [www.nvidia.com](www.nvidia.com) and download the appropriate drivers for your card and system 
2) Go to the TTY (CTRL+ALT+F1) and type ```
sudo /etc/init.d/gdm stop
``` or if you are using kde replace gdm with kdm 
3) Now cd into the directory of the driver 
4) ```
chmod +x <filename>
```
5) Then ```
./filename
```
6) Follow the installer 
7) When done type in ```
sudo /etc/init.d/gdm start
``` or kdm if you are using kde

---

### Post by niite on 2010-05-03
I found this... might be helpful.  [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

haven't tried it yet..  i got mine running with the 173 proprietary, but it's kinda sluggish - gonna wait a bit before i do anything though.

As for if you have an onboard graphics card coupled with nvidia cards, i just disabled integrated graphics in bios so it only picks up the nvidia cards.

-niite

---

### Post by Linuxforall on 2010-05-03
For now the PPA for X also has latest drivers for Lucid so save yourself the hassle and the ppa and hope it would be kept regularly updated from now on.

ppa for x at [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by arizonagirl11 on 2010-05-04
Yes, I have tried all of that. Thank you very much for the suggestions though :D

---

### Post by TCWriter on 2010-05-04
I've been following this thread with a great deal of interest; I upgraded my normally rock-solid desktop machine from 9.10 to 10.04 (Nvidia 7100 video) prior to the weekend and have been getting random freezing of the screen, and if I was running an Nvidia driver (it never loaded the latest version, natch), upon reboot the config file was hosed.

At times I was running on the brand-new Nouveau driver (essentially an open-source Nvidia driver project) and while it worked better, it would eventually freeze too.

<strong>A Fix?</strong>

Yesterday I did the following - and the thing's still running this morning (crossing fingers). 

First, someone mentioned a driver conflict. I think there might be a conflict between the nouveau driver and Nvidia's drivers.

Even when I tried to blacklist nouveau and install the latest Nvidia drivers (as detailed in the link below), it still crashed.


[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)


In fact, despite the blacklist, my machine still loaded the nouveau drivers after I purged the Nvidia stuff and re-booted.

So I used Synaptics to remove the nouveau xserver (xserver-org-video-nouveau) and *then* performed the whole procedure mentioned in the link above, and... so far (about 12 hours later), it's still running.

It'll likely freeze the second I post this, but it seems as if nothing you've tried is working - maybe that's the result of a conflict between Nvidia and nouveau systems.

Good luck.

I know how frustrating this is.

---

### Post by psullie on 2010-05-04
Just to add my 2c

Upgraded from 9.10 over the weekend and had all sorts of graphic issues as above, nothing fixed it. So this morning I backed up everything and wiped the drive and did a clean install from the Live CD. I was able to activate the Recommended Nvidia driver via System -> Hardware Drivers and all worked after a reboot, even the Boot Menu looked better (dual boot system) and it took less than an hour. 

My guess is that the upgrade leaves too many conflicting files behind.

---

### Post by Linuxforall on 2010-05-04
A new update relased on xswat ppa just now which corrects the nvidia 2 or more cards issue with kernel 2.6.32

---

### Post by TCWriter on 2010-05-04
> **psullie said:**
> Just to add my 2c

Upgraded from 9.10 over the weekend and had all sorts of graphic issues as above, nothing fixed it. So this morning I backed up everything and wiped the drive and did a clean install from the Live CD. I was able to activate the Recommended Nvidia driver via System -> Hardware Drivers and all worked after a reboot, even the Boot Menu looked better (dual boot system) and it took less than an hour. 

My guess is that the upgrade leaves too many conflicting files behind.

I did two clean installs and still suffered the issues. I wonder if you didn't time it right so you got the latest version of the Nvidia drivers...

---

### Post by dino99 on 2010-05-04
> **TCWriter said:**
> I did two clean installs and still suffered the issues. I wonder if you didn't time it right so you got the latest version of the Nvidia drivers...

you only need genuine packages: nvidia-current, nvidia-current-modaliases, nvidia-common and nvidia-settings

and xorg.conf (check it to see if it exist)

---

### Post by niite on 2010-05-04
> **Linuxforall said:**
> A new update relased on xswat ppa just now which corrects the nvidia 2 or more cards issue with kernel 2.6.32

cool - this resolved all performance issues i've been having.  zinging along just fine now.

---

### Post by andyanderso on 2010-05-04
> **Mr. Moustache said:**
> I have the same problem, but your "fix" does not work here...
But I found another "workaround":

After reboot choose "low graphics mode" or just log in directly into the terminal.

In terminal enter:

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm restart

The GUI restarts and works fine with the NVIDIA-driver.

Unfortunately: at the next reboot you have to do it again...
But until a fix comes out, I can live with that, because my systems runs 24/7 anyway. ;)

I have a similar issue. Nvidia fails to initialize on start up.  I get kicked into the low graphics mode. If I then go straight to a console login and start gdm, it works fine...but it will not start automatically. Seems like this is similar enough to keep in this thread...Has anyone submitted a bug report for this problem?

---

### Post by grndnl on 2010-05-05
> **Linuxforall said:**
> A new update relased on xswat ppa just now which corrects the nvidia 2 or more cards issue with kernel 2.6.32

im sorry ive been having this problem too, and so far nothing has worked.
how do i get this upadate? tx

---

### Post by dino99 on 2010-05-05
> **grndnl said:**
> im sorry ive been having this problem too, and so far nothing has worked.
how do i get this upadate? tx

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by GSF1200S on 2010-05-05
> **Linuxforall said:**
> A new update relased on xswat ppa just now which corrects the nvidia 2 or more cards issue with kernel 2.6.32

Well, the current nvidia drivers from this ppa fixed my framebuffer issue; I can kill X and have a console now, as well as change tty's without the monitors shutting off :)

Its too bad.. using these drivers might have fixed the OP's problems. Cant win them all..

---

### Post by niite on 2010-05-05
i had to blacklist nouveau to get it to work, but it works fine now.. i did the following:

open a terminal and type: sudo nano /etc/modprobe.d/blacklist.conf add the following at the bottom and save:
blacklist nouveau
 

after that run:  nvidia-xconfig 



then reboot.

---

### Post by nvaytet on 2010-05-05
What worked for me was to install the 173 version of the nvidia driver in the Hardware drivers utility instead of the 'current'.

---

### Post by psullie on 2010-05-05
> **TCWriter said:**
> I did two clean installs and still suffered the issues. I wonder if you didn't time it right so you got the latest version of the Nvidia drivers...

Driver 195.36.15 installed via Hardware Drivers (after clean install), I tried installing 195.36.24 before I did the clean install but it didn't work.

In Hardware Drivers I have only two options; 173 and Current, I choose Current. 

Dell T7400 + Quadro FX 3700

---

### Post by andyanderso on 2010-05-05
Today's kernel update fixed this problem for me...Any luck for the rest of you?

---

### Post by TCWriter on 2010-05-05
> **andyanderso said:**
> Today's kernel update fixed this problem for me...Any luck for the rest of you?

Looks like it may have. This morning I finally gave up on 10.04 (nothing worked over the long haul) and installed 9.10 in its own partition. 

If this continues to work, can someone tell me if there's an easy way to get rid of the 9.10 partition and reclaim all that hard disk space for this 10.04 install?

---

### Post by topCturV on 2010-05-05
Not sure if this will be any help as I am a newbie to Ubuntu 10.04 but I have the same graphics card as you had mentioned, the Geforce 9500GT.
I am using nvidia driver version 173.14.22 and am having no problems.
The driver is located here:
[http://www.nvidia.com/object/linux_display_ia32_173.14.22.html](http://www.nvidia.com/object/linux_display_ia32_173.14.22.html)
[ATTACH]155648[/ATTACH]
I see lots of expert help here, so again a reminder that I am a newbie, but this older driver version works for me very well.

---

### Post by Mr. Moustache on 2010-05-06
> **andyanderso said:**
> Today's kernel update fixed this problem for me...Any luck for the rest of you?

At the first reboot after installing the kernel update everything was ok (NVIDIA drivers came up with no error or warning, Dual-Screen, just like it should)... I logged in, checked the NVIDIA settings (everything was still ok)... then I rebooted, because I couldn't believe it, and I was right: the error was back. So I logged in with minimal resolution - again - and did

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

X restarts, NVIDIA comes up, everything's ok - until the next boot I guess.

Very strange.

---

### Post by Linuxforall on 2010-05-06
> **topCturV said:**
> Not sure if this will be any help as I am a newbie to Ubuntu 10.04 but I have the same graphics card as you had mentioned, the Geforce 9500GT.
I am using nvidia driver version 173.14.22 and am having no problems.
The driver is located here:
[http://www.nvidia.com/object/linux_display_ia32_173.14.22.html](http://www.nvidia.com/object/linux_display_ia32_173.14.22.html)
[ATTACH]155648[/ATTACH]
I see lots of expert help here, so again a reminder that I am a newbie, but this older driver version works for me very well.

That driver is old for a 9600 card. The new version works flawlessly for your card, it works very well with 8400 series and upward.

---

### Post by Baochan on 2010-05-06
This is my experience on my laptop Asus W7 with Nvidia 9300M

Repositories: all Ubuntu 10.04 x64 and ppa X-Updates

Kernel: 2.6.32-22-generic

Driver Nvidia 173.14.22: Black internal monitor LCD but I see gdm in external CRT if I plug that.

Driver Nvidia 195.36.15 or 24: White screen of death like isr.igo [#23]("http://ubuntuforums.org/showpost.php?p=9209430&postcount=23")

- I tried many .run from Nvidia site but nothing change.
- I tried blacklist.conf setting but nothing change.
- I tried Alberto's (Milone) ppa but nothing change.
- I tried "nomodeset" in grub kernel launcher but nothing change.

Xorg.0.log and syslog seems clean of errors...

I used this laptop since ubuntu 7.10 and I haven't problem whit Nvidia driver, but now really I don't know what I can do... AAAAAARGH! ](*,)

---

### Post by TCWriter on 2010-05-06
> **Mr. Moustache said:**
> At the first reboot after installing the kernel update everything was ok (NVIDIA drivers came up with no error or warning, Dual-Screen, just like it should)... I logged in, checked the NVIDIA settings (everything was still ok)... then I rebooted, because I couldn't believe it, and I was right: the error was back. So I logged in with minimal resolution - again - and did

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

X restarts, NVIDIA comes up, everything's ok - until the next boot I guess.

Very strange.

Strange is right. After I saw yesterday's note about the kernel update, I updated my 10.04 installation, and for the rest of the day and night, the thing ran perfectly. 

I haven't been experiencing boot problems but random screen freezes. There's never any static or drama, but windows just - over the course of a few minutes - stop working, and, then the mouse freezes too.

It didn't go south yesterday or last night, so I was confident the problem was solved. 

This morning I started it, fired up the browser, took the kiddo to day care, and the computer was frozen when I got back. 

I'm back working on 9.10, hoping somebody figures this out...

---

### Post by niite on 2010-05-06
> **Mr. Moustache said:**
> At the first reboot after installing the kernel update everything was ok (NVIDIA drivers came up with no error or warning, Dual-Screen, just like it should)... I logged in, checked the NVIDIA settings (everything was still ok)... then I rebooted, because I couldn't believe it, and I was right: the error was back. So I logged in with minimal resolution - again - and did

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

X restarts, NVIDIA comes up, everything's ok - until the next boot I guess.

Very strange.

Yeah I'm having the same problem.. and doing what you are doing everytime to get it to work.    I'll get it working fine, restart and all is fine.. even shut down and restart (if i do it right away)... but when i just it down for an extended period of time, and boot up, something is getting blown out.. i do notice that on boot up, before grub loads i get a display message that the configuration has been updated -- so maybe something is getting blown out at shutdown, that shouldn't be blowing something out?  i have no idea.

---

### Post by couzin2000 on 2010-05-06
I actually have tried everything this thread has mentioned, yet I'm stuck trying it from the LIVE CD... everytime I try to boot, I get to the "low-graphics mode" message, but my mouse and keyboard are stuck. Since I use legacy-enabled USB hardware, this surprises me. I've tried others, to no avail. It's like the drivers aren't loaded.

So I'm stuck using the live CD. I won't install from the CD since it will format all and I have many gigs of stuff, hence the upgrade.

Help me out???

---

### Post by maxniko on 2010-05-07
Hello everyone.
I got a computer with a Asus P7P55-M motherboard, Intel i3 530 2.93Ghz, nVidia 9600GT, 2Gb Ram. I installed Ubuntu 10.04 Lucid Lynx and everything looked just perfect until I installed the propietary drivers for my nvidia graphics card (in order to be able to use compiz and 3D graphics). After I reboot I get, as everyone else, an ugly 640x480 resolution on my desktop and my splash screen.

If I change the resolution on the nvidia settings manager (manually), what I get is a 1024x768 resolution (my monitor's native resolution) but cropped down to 640x480. So, if I want to get to the upper right corner of the screen I have to "push" the edge with the mouse til it reaches the border. Nasty!

I've already tried deleting the xorg.conf file and the packages installing nvidia-common, nvidia-current, nvidia-current-modalises

Please, some help.

---

### Post by griever1980 on 2010-05-07
Howdy folks,

My first post :).  Wish it was a happier one though.  I've been running Lucid on a clean install since launch day.  Everything was fine until yesterday's kernel update.  Now when I boot into Ubuntu I get the Low Graphics Mode window with an error message about NVIDIA.  Same message everyone else seems to have about failure to initialize, screen error, etc.

So I did the whole sudo nvidia-xconfig thing and rebooted... didn't help.  Then I found on a forum a suggestion of adding the BusID to the xorg.config file.  So I added:

BusID "PCI:3:0:0" 

This goes under the Device section, under the driver = nvidia line.

After adding this line and rebooting, everything comes up great :)

Until I reboot again.

Then it all goes :(

I get the same Low Graphics Mode and error screen that I got when I first started.  If I redo the nvidia-xconfig and BusID trick it works for the next reboot and fails again on the following one.

Considering returning to Karmic, which is sad... I rather like Lucid.

---

### Post by Linuxforall on 2010-05-07
I have been on Lucid since day one of its release and am yet to get any kernel update everyone is talking about.

---

### Post by griever1980 on 2010-05-07
> **Linuxforall said:**
> I have been on Lucid since day one of its release and am yet to get any kernel update everyone is talking about.

Are you using an NVIDIA card?  If so, which one and could you post your xorg.conf file?

---

### Post by isr.igo on 2010-05-07
> **Linuxforall said:**
> For now the PPA for X also has latest drivers for Lucid so save yourself the hassle and the ppa and hope it would be kept regularly updated from now on.

ppa for x at [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)



hello again,
early this morning i have updated the kernel
but it didn't help , i tried again - removed the nvidia drivers (195....) and reinstalled from the synaptic the nvidia-current , common and modularies

and now (as was expected) it got worse now it prompet me on startup to boot in low graph mode and i get this :

(**) May 07 20:19:56 NVIDIA(0): Enabling RENDER acceleration
(II) May 07 20:19:56 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 07 20:19:56 NVIDIA(0):     enabled.
(EE) May 07 20:19:56 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) May 07 20:19:56 NVIDIA(0):     system's kernel log for additional error messages and
(EE) May 07 20:19:56 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


then i have restarted the comp and again got this :

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

i give up... it's useless.

---

### Post by Linuxforall on 2010-05-07
> **griever1980 said:**
> Are you using an NVIDIA card?  If so, which one and could you post your xorg.conf file?


```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

I have a 8400GS

---

### Post by TCWriter on 2010-05-07
> **isr.igo said:**
> 

i give up... it's useless.


I too ran out of troubleshooting skills and patience at the same time, so I simply purged all the Nvidia stuff (sudo apt-get --purge remove nvidia-* ) and used Synaptics to reinstall the Nouveau driver.

Now it runs without the random freezes (admittedly without the special effects) but at least I'm getting work done while this gets cleared up.

---

### Post by negora on 2010-05-07
I also have a nVidia graphics card (GeForce 9600 GT) and faced big problems to run the Live CD and also to boot after installing from the Alternate CD. My problem was very close to the one described here: [https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/558569](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/558569) .

In my case all my head aches were caused because the kernel loaded the module "viafb" by default. I blacklisted it and also had to boot editing the kernel line in GRUB, removing "quiet splash" and adding "nomodeset" (I don't know what it does exactly).

Then I installed the "nvidia-current" package and everything has been OK since then, even after installing the last kernel update.

I don't know why, but this Ubuntu 10.04 has caused me a lot of problems: with the graphics card, with my WiFi adapter, with my tablet... Not a good successor for Karmic Koala. Many steps back.

PS: Is Canonical going to alter the official release to include the fixes to all these problems? Because non-experienced users won't be able even to start the Live CD :S .

---

### Post by griever1980 on 2010-05-08
Agreed, Canonical should revise this LTS.  On this computer I've run Hardy, Jaunty, Karmic, and now Lucid... Karmic was the best of the bunch.  

Back on topic, remember how I said that I added BusID "PCI:3:0:0" to my xorg.config file and it worked on the reboot directly after inserting it, but then failed on the following reboot?

It stopped failing.

I have absolutely no clue what I did between turning off the machine Thursday night and turning it on Friday afternoon, but the error messages are no more.

So, if anyone is still fighting the good fight on this one...

open Terminal
type "**lspci**" without the quotes
Look on the list for BusID of your NVIDIA card.  Mine showed 03:00.0

Now remake the xorg.config file

```
**sudo nvidia-xconfig**
```

Now to add the BusID

```
**sudo nano /etc/X11/xorg.conf**
```

We want to add the BusID to the Device section.  Here's what mine looks like after adding it:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    **BusID "PCI:3:0:0"**
EndSection
```

Obviously change the number to whatever your Bus comes up as.  Also eliminate the extra zeros (remember mine listed 03:00.0).

Save the file and reboot.  

Like I said when I did first did this it behaved inconsistently until I powered down for the night and came back to it after work.  I have no clue why this happened but for the moment I'm not complaining... its working.

For now.

---

### Post by mfraser on 2010-05-08
Not sure what I've done, but this morning when I booted up the screen went blank after Plymouth had done its thing. For some reason I found that I couldn't log in with either the nvidia or novueau drivers enabled.

For now I've fixed it by adding
vmalloc=256MB
to the end of the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub

---

### Post by ZazzyE on 2010-05-08
I ran into some of the same errors on my dell.  Before this, I did the same 'nvidia-xconfig' in the terminal that you've been doing.

Load up synaptic package manager, and search for 'nvidia'

I had to get 'jockey-gtk' and 'nvidia-common', and near the bottom, remove 'xserver-xorg-video-nouveau', and make sure that 'xserver-xorg-video-nv' was installed.  'nvidia-common' just pointed to older drivers in the same package manager, and jockey needed some other files too, but that's standard.  Heck, while you're here, make sure 'nvidia-current' is installed too.  Worst comes to worst, install every driver you can get your hands on and remove the rest later.

After installing, i hit run, and typed in jockey-gtk.  After it scanned my hardware, it offered to apply the drivers I had installed (just those that would fit). I picked one, then rebooted.  Now it works, even on the "current" driver that gave me trouble before.  

If you don't like how the driver performs, you can select an older one.

Hope this helps!

---

### Post by arizonagirl11 on 2010-05-08
It is now working! I got a new video card, cause I discovered that my old video card was overheating! Now, it works. I wonder if maybe it was not reading the video card because it was broken.

Thank yous o much everyone!

---

### Post by griever1980 on 2010-05-09
Glad you solved it.  Which video card did you end up going with?

---

### Post by maxniko on 2010-05-09
> **negora said:**
> 
In my case all my head aches were caused because the kernel loaded the module "viafb" by default. I blacklisted it and also had to boot editing the kernel line in GRUB, removing "quiet splash" and adding "nomodeset" (I don't know what it does exactly).

Then I installed the "nvidia-current" package and everything has been OK since then, even after installing the last kernel update.

Can you give a detailed list of steps you followed to do that? It's just that I'm a relatively new linux user.
Thanks.

---

### Post by maxniko on 2010-05-12
I give up! I'll downgrade to Ubuntu Karmic Koala 9.10 (where my nvidia drivers actually worked fine) and when Maverik comes up then I'll use Lucid. Hopefully then they've fixed the problem already. :(

---

### Post by GSF1200S on 2010-05-12
> **arizonagirl11 said:**
> It is now working! I got a new video card, cause I discovered that my old video card was overheating! Now, it works. I wonder if maybe it was not reading the video card because it was broken.

Thank yous o much everyone!

Oh my god are you kidding me?! Well, at least its fixed.. it didnt seem like there was any logical reason it should be failing..

---

### Post by TCWriter on 2010-05-12
> **maxniko said:**
> I give up! I'll downgrade to Ubuntu Karmic Koala 9.10 (where my nvidia drivers actually worked fine) and when Maverik comes up then I'll use Lucid. Hopefully then they've fixed the problem already. :(

I started to do that, but finally (finally!) got Lucid running on the Nouveau driver. It doesn't offer the snazzy desktop effects, but I don't need them, and want my desktop to run 10.04 like my two laptops, which upgraded with zero difficulties. 

Good luck!

---

### Post by griever1980 on 2010-05-13
Ok, so I checked my Update Manager yesterday afternoon and, nestled silently in the list, there was an update to nvidia-current.  "Oh", I thought, "perhaps this will quell the issues we've been having with the drivers since launch."

I downloaded everything, continued working on my VirtualBox Hackintosh (what a pain it is to get it work by the way), rebooted into Windows 7 to check on something for a friend of mine, then rebooted again into Lucid.

Again I was greeted with the Low Graphics nonsense, something I thought I fixed the last time around.  

I did my BusID trick, foolishly thinking that it would correct the issue... it did not.

Long story short, I went into Synaptic and completely removed anything that had "nvidia" in the name, rebooted, and then went back to Synaptic and installed _everything_ that had "nvidia" in its name.  Reboot, sudo nvidia-xconfig, reboot, and presto, back in action.

This is what bugs me.  I migrated from Karmic to Lucid Beta 1 and everything, including nvidia, worked flawlessly.  When Beta 2 went live I updated, my nvidia broke.  I switched back to Karmic to wait for the Lucid Final and still I have to struggle with something that has never been an issue for me in previous installations (Hardy, Jaunty, Karmic all worked flawlessly).

Windows is a tired OS that has really shown its age over the past couple of years and Mac OS X is a complete ripoff and proprietary.  Google's Chromium OS is still a long way from completion.  Ergo, OS's like Ubuntu have a decent window to sneak in and really contend as a mainstream OS.  However, botched major releases tend to turn people off completely.  Just ask the early Vista adopters... or the early Windows Me adopters... or the early Windows 9x adopters...

Picking up on a trend here.

Sorry for the deviation, but this driver nonsense is rather annoying.

---

### Post by arizonagirl11 on 2010-05-13
it was funny. The video card I ended up with is a Zotac NVIDIA GeForce  FTS250

But I actually replaced the whole computer.

---

### Post by maxniko on 2010-05-14
> **griever1980 said:**
> Long story short, I went into Synaptic and completely removed anything that had "nvidia" in the name, rebooted, and then went back to Synaptic and installed _everything_ that had "nvidia" in its name.  Reboot, sudo nvidia-xconfig, reboot, and presto, back in action.

You say you downloaded _everything_. There are several versions of all the packages. So, by "everithing" you mean all the packages of a specific version or actually all the "nvidia-something" packages?

---

### Post by griever1980 on 2010-05-15
All as in all versions.  I figured a shotgun approach might yield some sort of result.  I can't tell at this point if the shotgun approach helped me or if its working simply because it feels like it, but for the moment everything seems to be working.

I'm holding my breath until the next kernel / driver update.  If it breaks again I'm returning to Karmic, where the desktop is browner and the drivers work like they're supposed to.

---

### Post by KilianValkhof on 2010-05-16
After a thoroughly frustrating weekend culminating in this unsolvable problem, my macbook is going back to karmic. 10.04 is a very disappointing release :(

---

### Post by maxniko on 2010-05-21
So far I've uninstalled all the nvidia named packages and my screen resolution went back to normal. Now I'm downloading the packages again... Cross your fingers guys. I'll let you know what happened...

---

### Post by maxniko on 2010-05-21
](*,) ](*,) ](*,) ](*,) ](*,)!!!!!!!!!!!

That's it... Karmik: here I come.
I don't know why I held my breath... Too bad it didn't work. Apparently I'll have to wait for an update (a better one).

If anyone discovers one, let us know through this thread

---

### Post by mascom on 2010-05-22
I've fix the same problem in 9.04 this way. Maybe it can help You: remove as super user /etc/X11/xorg.conf; Then go to nvidia driver menu, advanced, click create new x configuration file (or simillar, i do it on Russian language).

Now I have the same problem, but it's hardly. May be anyone can help me. I tried to install nVidia 173 (recommended) then I reboot. Now it's not loading. Says:

> Loading, please wait...
Error: unexpectedly disconnected from boot status daemon.What is it? My Ubuntu is 10.04.
Sorry for my bad English...

---

### Post by mascom on 2010-05-22
I think that my problem is not connected with nVidia 'cause I've just unactivate Plymouth and now it's can't find the root file system...

---

### Post by ronnielsen1 on 2010-05-22
10.04 doesn't seem to play well with nvidia. I went back to 9.10. Hopefully, later it will

---

### Post by mascom on 2010-05-22
OK. Perhaps I'll have to also revert to the 9.10. When it changes in 10.04 - report me please.

---

### Post by psycho5 on 2010-05-22
> **arizonagirl11 said:**
> I have no idea what I am doing wrong. I tried that but got this error...

kimberly@kimberly-tower:~$ cd Desktop
kimberly@kimberly-tower:~/Desktop$ chmod +x NVIDIA-Linux-x86.195.36.24-pkg1(2).run
bash: syntax error near unexpected token `('
kimberly@kimberly-tower:~/Desktop$ sudo ./NVIDIA-Linux-x86.195.36.24-pkg1(2).runbash: syntax error near unexpected token `('
kimberly@kimberly-tower:~/Desktop$ 



Should I give up? Maybe Ubuntu isn't right for me :(

Just do this, assuming there is only one NVIDIA driver downloaded in the folder:

```

chmod +X NVIDIA*
sudo ./NVIDIA*
```

---

### Post by ronnielsen1 on 2010-05-23
>  sudo ./NVIDIA-Linux-x86.195.36.24-pkg1(2).runbash: syntax error near unexpected token
As far as the (2) in your line, this means you downloaded the file twice. You also should have a file called NVIDIA-Linux-x86.195.36.24-pkg1.run in the same place.

---

### Post by isr.igo on 2010-05-23
hello again,
i have stumbled upon something odd, after i lost hope with lucid i went back to OpenSUSE but the same problem followed me there so i tried it on Gentoo and guess what ?! i got the same old bug there too.
i guess it has something to do with the nVidias drivers or the mix of cards/MB or something else. 
and as always it works on windows (7,xp...):(

---

### Post by lucasta on 2010-05-23
So i have a similar situation as others who have posted here only the nvidia-current driver works fine in the generic kernel, but i am forced into the low-graphics mode when booting to the rt kernel.

any ideas as to why that is?

---

### Post by joelzehring on 2010-05-24
> **SFCampbell said:**
> I'm just catching up to you guys with 10.04 and I experienced the exact same problem.  **Please anyone having troubles, try this and tell me if it works for you**, because *it worked for me*.

I haven't had to reconfigure an X-server in almost 2 years since the Hardware manager was built into Ubuntu, so I believe the problem is instead a driver conflict.  In another post (sorry, I would like to give credit but I lost the link) I found a list of potentially conflicting drivers that I added to my blacklist.  Once I rebooted, my nVidia card has been working since.  Please try this:

**sudo gedit /etc/modprobe.d/blacklist.conf**

At the end of this file, paste the following:
[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]

It may have been pure luck and this was a circumstantial fix for my system, but I hope it may help others as well.

This seemed to work for my laptop. Thanks for the simple fix!

---

### Post by pickandwhammy on 2010-06-01
I know this is ages later, but it might still be useful.
A lot of people had trouble installing the nVIDIA drivers on 10.04 including me, and this is what seemed to have helped for most:
1. Download the nVIDIA driver from their own website, rename it to something small (like "n.run") and save it in a location easily accessible from the terminal. 
Note: The one I used which worked was 185.xx, so I can't guarantee whether the latest one will work.

2. Do the blacklisting

gsudo gedit /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

2. Purge nouveau

sudo apt-get --purge remove xserver-xorg-video-nouveau

3. Switch off GDM:

(Press Ctrl+Alt+F1)
service gdm stop

4. Go to the directory you've saved the downloaded driver to, for example /home/nv, and run the package (I named it as "n.run" in step 1, replace 'n' with whatever you've named it)

./n.run

This worked for me.

---

### Post by rliegh on 2010-06-11
Nothing works. Full stop. Nvidia+Lucid=garbage.:mad:

---

### Post by rliegh on 2010-06-11
> **rliegh said:**
> Nothing works. Full stop. Nvidia+Lucid=garbage.:mad:

blacklisting noveau and friends ---doesn't work.
apt-get purge nvidi-* and reinstall ---doens't work
manually downloading and installing from nvidia directly --doesn't work.

I'm fresh out of ideas here, and my 10.04/amd64 desktop is stuck at an unacceptable 1024x768. 

Is there **anything** I can do short of falling back to jaunty (karmic is also unacceptable) and/or going back to Windows 7?

---

### Post by ronnielsen1 on 2010-06-12
> Is there **anything** I can do short of falling back to jaunty  (karmic is also unacceptable) and/or going back to Windows 7?
I got my nvidia driver (8400GS) working by blacklisting and installing the driver from Nvidia's site but I don't see one of your posts that says what video card you have

---

### Post by entaro on 2010-06-19
1. 
updatedb and sync :P
2. 
locate nvidia |grep ko | xargs rm
3. 
apt-get remove nvidia*
4. (in my case) the ideea is to clean everyting! that is nvidia
dpkg --list |grep nvidia
dpkg --remove nvidia-current
dpkg --purge nvidia-current
dpkg --remove nvidia-kernel-common
dpkg --purge nvidia-kernel-common
5.
init 1 - drop a root shell
6.
init 3
7.
bash NVIDIA-Linux-x86_64-195.36.31-pkg2.run
here it will go on error (nv commons) hit ok and ok and ok ... and ok when ask for xorg

system info

04:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
2.6.32-22-generic #36-Ubuntu SMP  x86_64 GNU/Linux
Ubuntu 10.04 LTS

References: (did not work for me but worked for others)
[http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html](http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html)

---

### Post by mainerror on 2010-06-21
Hello,

Sadly I'm not able to solve my problem my-self so I have to ask you guys now.

First of all I have a Nvidia 6800 GT. The problem I'm encountering is that the highest resolution I can get using the Nvidia drivers is 1024x768.

I have tried the manual installation method without success, it got even worse with a resolution of 800x600.

I'm running out of ideas. Do you guys have any ideas?

---

### Post by Riffronan on 2010-06-27
I just wanted to thank GFS1200S for his advice on page 4 in this thread.  I installed the newer 2.6.34 kernel and couldn't get the Nvidia driver to work that was already working on the previous one.

sudo -i
apt-get install nvidia-current
nvidia-xconfig
reboot

I showed no drivers in Hardware Drivers and so these commands allowed me to get the newest 195 Nvidia driver to work...love that Compiz  (!)

---

### Post by RedRat on 2010-06-27
I may be off base here, but is EnvyNG available for 10.04? If so, you might want to try and use it. It is the only way I could bet my 8.04 to use the NVida graphics card. Your trials and tribulations here remind me of my own. See if EnvyNG is in your repository and try it out. Remember when you go to run it, best through the command line, use the sudo prefix in the command:
sudo envyng

It will load a GUI. 

Also, if you use NVida-settings, you must run that with sudo also, since it writes the settings to config file.

---

### Post by flanagam on 2010-07-07
i have an onboard ati video that goes to two monitors, and a pci-e nvidia 9500 that goes to a third monitor. i was wondering if someone could help me get all three running.

system is: 
 
[LEFT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333][B][COLOR=#000099][Biostar  TA790GX 128M AMD 790GX Socket AM2+ MB]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4408236&SRCCODE=WEBLET101SATSFY&cm_mmc=Email-_-WebletMain-_-WEBLET101SATSFY-_-Satisfy")
AMD Athlon 64 x2 dual core 4200+ 
nvidia 9500 GT 1gb

[/COLOR][/B][COLOR=#000099][COLOR=Black]All three displays work under windows 7, but i can not find a way to get them working under ubuntu. 
btw, using ubuntu 10.04[/COLOR]
[/COLOR][/COLOR][/SIZE][/FONT][/LEFT]

---

### Post by griever1980 on 2010-07-11
Howdy again everyone :)

So its been a short while since I last posted on my NVIDIA / Lucid fail.  Here's another update to what I'm stuck with.

For a few weeks everything worked fine.  I would boot into Lucid and it would immediately go to the desktop with the proper resolution (1680x1050), no errors.  All my wonderful compiz settings worked flawlessly and I was a happy Ubuntu-er.  

Then I downloaded the latest Linux driver from NVIDIA.

Everything went awry.  None of the little tweaks mentioned in this forum seemed to get my desktop back.  So I bit the bullet and decided on a clean install of Lucid.

Installed, updated, rebooted... Low Graphics Mode.

To save myself some frustration I used the command line login and ran sudo nvidia-xconfig followed by sudo gdm start.  That would get me back to a full resolution desktop.

I had to do this every time I rebooted.  More than a little annoying.

Next I "fixed" the ugly low-rez plymouth screen.  Rebooted, Low Graphics Mode, click on Command Line Login... black screen?

No command line.  Interesting.  So for fun I logged in blindly and ran my configure / gdm start lines.  That worked and brought me to a full resolution desktop.

This is what I have to do now every time I reboot.  I get greeted with the error, screwed on my command line so I have to do everything blindly, then finally get into the desktop.

LTS... indeed.

I'm keeping my fingers crossed that 10.10 is more friendly with proprietary drivers, but something tells me come 10.10.2010 I'll have a pretty desktop but no sound or internets.

Hell, I wouldn't be surprised to see a BSOD.

---

### Post by DesiBabu on 2010-07-14
Earlier today I upgraded to 10.04 version of Ubuntu and disaster....
 
now when I boot up (normal or recovery mode both end up at the same problem).
 
In recovery mode, I first get a "Recovery menu" screen in which I get several options:
Resume - resume normal boot
Clean - try to make free space
dpkg - repair broken packages
failsafeX - run in failsafe graphic mode
grub - update grub boot loaded
netroot - drop to root shell prompt with networking
root - drop to root shell prompt
 
I chose the failsafeX - but it ends up with the same screen with the nvidia drivers issue and my keyboard and mouse don't work - only option is to reset or power cycle
 
Can someone share some experience on how to get out of this situation? Is there a way I can get back to my 9.0.x version from here?
 
Screen message where it just stalls:
 
Ubuntu is running in low-graphics mode
The following error was encountere. you may need to update your configuration to solve this.
(EE)Nvidia: Failed to load the NVIDIA kernel module. Please check your
(EE)Nvidia: System's kernel log for additional error messages.
(EE) failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
 
There is an ok button but since my mouse or k/b do not work I can't go past this.

---

### Post by DJ Wings on 2010-07-26
I'm having the same problems on a Vaio F (GT 330M), but with a weird twist: When I installed the latest official drivers (256.35) and got them working, instead of a GDM screen, I got a white screen with a bunch of dark, pulsating splotches. That's probably the creepiest thing any computer has ever done to me.
I'll read the rest of the thread tomorrow, sorry for the bump.

---

### Post by dart1007 on 2010-07-29
This solution worked for me!!
Check it out guys!!;)

[http://kubuntuforums.net/forums/index.php?topic=3107406.0]("http://kubuntuforums.net/forums/index.php?topic=3107406.0")

---

### Post by turtle.ninja on 2010-08-02
Hi,
I have a GeForce GTS 250. My Ubuntu is 10.04 and my kernel is 2.6.32-24-generic-pae. I downloaded the driver NVIDIA-Linux-x86-256.44 from nvidia.com.
I stopped GDM and installed the driver fine. Then I rebooted. It seems to start ok, but at a certain moment the screen goes blank and I get stucked. My keyboard and mouse don't work anymore. The only thing I can do to restart the computer is to turn it off and the turn it on again. In order to get the computer up and running again I have to boot into safe mode, drop to a shell, erase /etc/X11/xorg.conf and restart.

Can someone please help me to configure my GTS 250 ?

Turtle

---

### Post by wojox on 2010-08-02
Hey Turtle, things have changed a little for installing the Nvidia driver from the site. This link helped me out. [Install NVIDIA drivers manually on Lynx]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=nvidia+lynx")

---

### Post by turtle.ninja on 2010-08-02
Thanks wojox,
I'll give a try and post my results later.

Turtle

---

### Post by mauripop on 2010-08-08
Hi all.

I thought I had left my Nvidia troubles behind but I am trying to use a Samsung 40" TV / LCD monitor with an Ubuntu media server. I put a new GE Force 6200 in it. This is a 1080p capable monitor but the regular drivers gave me only 1024x768. After I went into jockey-gtk to install the nvidia current driver and rebooted, it only gave me 640x480, and the only other option in nvidia-settings is 320x480. 


The nvidia acceleration is working at least, glx-gears and such work well. The drivers are working.

Before Plymouth I used to be able to tweak xorg.conf to add video modes. I tried adding the 1024x768 at least and that didn't do anything at all. 

Currently the PC is plugged into the display's VGA port. I ordered a DVI  to HDMI cable that I am hoping will help communication between the PC and display maybe and give me a higher res.

Any ideas?  I'd like to get at least 854x480, which I got the the standard vesa driver; but I do need OpenGL acceleration; otherwise Boxee is unusable.

---

### Post by DJ Wings on 2010-08-11
Is anyone else having the case I mentioned last page? I still am after installing Fedora. It happens with any combination of Ubuntu/Fedora, download from site/repository, and v190/v256. Hardware, maybe?

---

### Post by RedRat on 2010-08-12
> **DJ Wings said:**
> Is anyone else having the case I mentioned last page? I still am after installing Fedora. It happens with any combination of Ubuntu/Fedora, download from site/repository, and v190/v256. Hardware, maybe?
This sounds like a hardware issue but with some software kinks thrown in. I assume that since you are using a Sony Vaio that it came with Windows. Did it work with Windows?

---

### Post by jtanner28 on 2010-08-12
Hi everyone. I need some help. I'm running Ubuntu 10.04 and I want to enable the Nvidia drivers for my 8600 GS card. The problem is that I cannot disable the onboard video in the BIOS. All I can do is set the order of which video output the machine picks first. I used to have a line in my xorg.conf that specified the PCI port: "PCI:00:02:00"... something like that. I also specfied the monitor, refresh rate, and other video details. (I can post the old xorg.conf or any other details if needed.) And that worked quite well with 9.10. However, apparently 10.04 doesn't use xorg.conf anymore. I have tried to simply install the driver and see if it works and have gotten stuck with no video output at all. I am currently running on the onboard video output (which kinda sucks... no compiz eye-candy, no RGBa support... boo!)What is the proper procedure to get the driver set up correctly and get myself switched over to high-definition sweetness? Any help or tutorial would be appreciated. Thanks in advance! :)

---

### Post by realzippy on 2010-08-12
> **jtanner28 said:**
> Hi everyone. I need some help. I'm running Ubuntu 10.04 and I want to enable the Nvidia drivers for my 8600 GS card. The problem is that I cannot disable the onboard video in the BIOS. All I can do is set the order of which video output the machine picks first. I used to have a line in my xorg.conf that specified the PCI port: "PCI:00:02:00"... something like that. I also specfied the monitor, refresh rate, and other video details. (I can post the old xorg.conf or any other details if needed.) And that worked quite well with 9.10. However, apparently 10.04 doesn't use xorg.conf anymore. I have tried to simply install the driver and see if it works and have gotten stuck with no video output at all. I am currently running on the onboard video output (which kinda sucks... no compiz eye-candy, no RGBa support... boo!)What is the proper procedure to get the driver set up correctly and get myself switched over to high-definition sweetness? Any help or tutorial would be appreciated. Thanks in advance! :)


You could try your old xorg.conf file,changing "nvidia" to "nouveau" in the device section;might work.Then running X on the pci card try again to install the nvidia driver...

Maybe start an own thread?

---

### Post by Zarckon on 2010-08-13
For me the low graphics mode problem just started this week. I can't be sure that it was the recent kernal upgrade (downgrade?) that did it, but it was around that time. This machine has been working fine with this Nvidia card from Jaunty to Karmic and until this week Lucid.

I see that there is a lot of talk that implies that it's the Nvidia driver. But given that it's been working fine and that I can correct the problem by running only the line below that was suggested in a post on page 4, I am convinced that it has to be the kernal.

> **GSF1200S said:**
> a terminal and do:sudo /ect/x11/gdm restart

Currently I always get an error and a default to low graphics mode on startup. Once I log in I have to start a terminal and run the line above, then on the restart of x it all works fine. That is a major problem with with this distro. Things had gotten to where I truly thought that it was all easy enough for my parents who are in their late 70s to actually use Ubuntu. But, problems like this keep it firmly in the you have to be a geek category. I expect that the problem will be solved sooner or later, but it actually appears to be getting worse for now in that computers that were not affected before are now affected. Very disappointing. I don't think that I'm going to go back to Karmic as some appear to have done, but there is some temptation to do that.

---

### Post by DJ Wings on 2010-08-13
> **RedRat said:**
> This sounds like a hardware issue but with some software kinks thrown in. I assume that since you are using a Sony Vaio that it came with Windows. Did it work with Windows?

Indeed. 3D acceleration works like it's supposed to, so do on-card features like hardware antialiasing. I'm not sure what's going on, but I really want to get Linux working.

---

### Post by RedRat on 2010-08-13
> **DJ Wings said:**
> Indeed. 3D acceleration works like it's supposed to, so do on-card features like hardware antialiasing. I'm not sure what's going on, but I really want to get Linux working.
Graphics cards in laptops are a bit of a different breed than the cards that you buy and place in Desktop computers. I suspect that there is far more integration of the card with the motherboard, which means hardware and software having to work together. The symptoms that you describe on the previous page certainly tell me that the graphics card and drivers just are not working correctly, but for what reason I don't know. This may well be one of those times when you have to talk to the people at Sony and see it they have any Linux-types there (I wouldn't hold my breath).

This is why when I bought a laptop, I got one from System76 with Linux pre-installed. System76 is a Linux shop and they have done the required engineering design to ensure that Linux and their hardware work together--hey, I am not doing an advertisement for System76 but there are other Linux Laptop shops out there. 

I visit, of course, the Syetem76 user group here at the forum. There I noted several weeks ago a question about using Mint on the System76 machines. The System76 rep who answered the question said that it couldn't be done. Whether that is true or not or exactly why it could not be done wasn't stated, but clearly laptop motherboard design is apparently pretty tightly integrated. So that may well be part of the problem.

---

### Post by Meizirkki on 2010-08-13
Post removed by author

---

### Post by Zarckon on 2010-08-14
Just wanted everyone in this thread to know that at least for me, I appear to have stumbled on to a solution. I did a search for Nvidia in Synaptic and found that the Nvidia-kernal-common was not installed. I installed that and have had my first error free boot in about a week. Why that would suddenly become necessary after years of perfect boots without it is a mystery to me, but the installation does appear to have corrected the problem of booting into low graphics mode.

So, one more thing to try for those that haven't found a solution yet.

---

### Post by toffuuu on 2010-09-05
ok, now I hope some of u might recognize me lol   but if not my problem now with my newly built PC and fresh install of 10.04 Video and audio edition of the OS  is well i already have the Proprietary Driver from nvidia for my 240 GT video card, but the .run file every time i try to run it  says it needs to be run in "Root"   and  considering that I know what root is, since i worked with OS X..  but it still gives me trouble..   also now heh, the Built PC does not have wireless net capability at all, and so I am now on my MacBook Pro  using a no lock type connection where i am now, but have been able to do things slightly through the use of a USB Flash Drive,  so if possible  please consider that as well with regards to me being able to fix this...   cause well the Ubuntu Linux PC  has no Net capability at least for now..   Thanks for any of ur help in advance..

---

### Post by RedRat on 2010-09-05
> **toffuuu said:**
> ok, now I hope some of u might recognize me lol   but if not my problem now with my newly built PC and fresh install of 10.04 Video and audio edition of the OS  is well i already have the Proprietary Driver from nvidia for my 240 GT video card, but the .run file every time i try to run it  says it needs to be run in "Root"   and  considering that I know what root is, since i worked with OS X..  but it still gives me trouble..   also now heh, the Built PC does not have wireless net capability at all, and so I am now on my MacBook Pro  using a no lock type connection where i am now, but have been able to do things slightly through the use of a USB Flash Drive,  so if possible  please consider that as well with regards to me being able to fix this...   cause well the Ubuntu Linux PC  has no Net capability at least for now..   Thanks for any of ur help in advance..
do you run this using the "sudo" command in the terminal?

For the wireless capability, do first of all have a wireless card installed. If so, did you install the wireless drivers?

---

### Post by toffuuu on 2010-09-05
> **RedRat said:**
> do you run this using the "sudo" command in the terminal?

For the wireless capability, do first of all have a wireless card installed. If so, did you install the wireless drivers?

Yes let me do that now  and post on here what it says...   
and no i don't have wireless card installed at all  since i did not get one  and well do not really want too..  the only way i am able to get online here where i am at now is cause im using another puter, a MacBook Pro...   and not my newly built PC... 

after running sudo nvidiablabla.run command
it says next here "ERROR: You appear to be running an X Server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at nvidia.com"

---

### Post by RedRat on 2010-09-05
> **toffuuu said:**
> Yes let me do that now  and post on here what it says...   
and no i don't have wireless card installed at all  since i did not get one  and well do not really want too..  the only way i am able to get online here where i am at now is cause im using another puter, a MacBook Pro...   and not my newly built PC... 

after running sudo nvidiablabla.run command
it says next here "ERROR: You appear to be running an X Server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at nvidia.com"
As to running and installing the nvida driver via sudo, I recall that you might have to stop the x-server, forget the command for that, and then restart it after it is installed. You might want to check and see if EnvyNG is available for 10.04. I have found that for 8.04 it works well. I don't know if it is available for Lucid. 

Are you sure that your MB in this computer has a connector for internet. Sometimes the phone modem and internet connector are very close in size. Does your new computer recognize the network connection when it is plugged in? I believe you use Device Manager for that. Under System>Administration there should be an entry for "Network" and "Network Tools" (these are the words I have on 8.04) I am not currently using 10.04 since that is on my laptop.

---

### Post by toffuuu on 2010-09-05
> **RedRat said:**
> As to running and installing the nvida driver via sudo, I recall that you might have to stop the x-server, forget the command for that, and then restart it after it is installed. You might want to check and see if EnvyNG is available for 10.04. I have found that for 8.04 it works well. I don't know if it is available for Lucid. 

Are you sure that your MB in this computer has a connector for internet. Sometimes the phone modem and internet connector are very close in size. Does your new computer recognize the network connection when it is plugged in? I believe you use Device Manager for that. Under System>Administration there should be an entry for "Network" and "Network Tools" (these are the words I have on 8.04) I am not currently using 10.04 since that is on my laptop.

I am not at all gonna be able to connect at least now, since i do not have an long enough ethernet cable, and yes it does have ethernet on the PC..   just right now, I do not have my own Net, but i will this coming 13th....  but i also need to add  that after looking at some of the stuff in readme at the nvidia site   also said to run it like this sh ./NVIDIA-Linux-x86-256.53-pkg2.run and after that it said just this "ERROR: nvidia-installer must be run as root"   and  well  if  u could some how tell me how to turn it off,  that would be greatly appreciated lol   and with regards to Envy,  no  it cannot be run on Lucid,  i found that out earlier today,  and  said to use something else,  but  again since the PC  has no Net Ability, with no way of installing things from the net,  i have to use packages at least for now...

---

### Post by RedRat on 2010-09-05
> **toffuuu said:**
> I am not at all gonna be able to connect at least now, since i do not have an long enough ethernet cable, and yes it does have ethernet on the PC..   just right now, I do not have my own Net, but i will this coming 13th....  but i also need to add  that after looking at some of the stuff in readme at the nvidia site   also said to run it like this sh ./NVIDIA-Linux-x86-256.53-pkg2.run and after that it said just this "ERROR: nvidia-installer must be run as root"   and  well  if  u could some how tell me how to turn it off,  that would be greatly appreciated lol   and with regards to Envy,  no  it cannot be run on Lucid,  i found that out earlier today,  and  said to use something else,  but  again since the PC  has no Net Ability, with no way of installing things from the net,  i have to use packages at least for now...
Of course you are right about Envy, if you don't have an internet connection you couldn't run it. I believe that the kernel in 10.04 and graphic drivers are more tightly connected.

As to x-server, type in the command line 
```
man x-server
```
This will give all the info you need. 

It appears that in my 8.04 version, you have to use the sudo command and merely type "X", but before you do that, do some reading about the x-server. I have never done that, but I have seen others write about it here. My poor memory tells me that the command is something like "sudo x stop", but don't quote me on that. 

You might want to post your question in the "Installation & Upgrades" forum here. 

I am beginning to think that your installation my just be borked. What you might want to do is wait until you get an internet connection via Ethernet then try the installation all over again.

---

### Post by toffuuu on 2010-09-05
> **RedRat said:**
> Of course you are right about Envy, if you don't have an internet connection you couldn't run it. I believe that the kernel in 10.04 and graphic drivers are more tightly connected.

As to x-server, type in the command line 
```
man x-server
```This will give all the info you need. 

It appears that in my 8.04 version, you have to use the sudo command and merely type "X", but before you do that, do some reading about the x-server. I have never done that, but I have seen others write about it here. My poor memory tells me that the command is something like "sudo x stop", but don't quote me on that. 

You might want to post your question in the "Installation & Upgrades" forum here. 

I am beginning to think that your installation my just be borked. What you might want to do is wait until you get an internet connection via Ethernet then try the installation all over again.

hmm no manual page at all for my x-server??  lol   tried man x-server like how u said,  then tried man X-Server  no go!! lol

---

### Post by RedRat on 2010-09-05
> **toffuuu said:**
> hmm no manual page at all for my x-server??  lol   tried man x-server like how u said,  then tried man X-Server  no go!! lol
I am sorry, it should be "man xserver", sorry about that. Make sure that the manual is installed.

---

### Post by stanca on 2010-09-06
[PHP]sudo apt-get remove --purge xserver-xorg-video-nouveau[/PHP];)

---

### Post by toffuuu on 2010-09-07
> **stanca said:**
> [PHP]sudo apt-get remove --purge xserver-xorg-video-nouveau[/PHP];)

Is this for turning off xserver?   and i hope it doesnt need internet either...   cause im still netless  lol   and even now at home cause the wireless network is very wonky, that sometimes works but later wont, so now im using net available at a local coffee house!!

---

### Post by stanca on 2010-09-07
This command will purge the new default nouveau 2D video driver from your system so you won't have low resolution problem at the boot time anymore.Better than blacklist it.But be sure before you have current proprietary driver installed too.And yes,you don't need an internet connexion for that.;)

---

### Post by toffuuu on 2010-09-07
> **stanca said:**
> This command will purge the new default nouveau 2D video driver from your system so you won't have low resolution problem at the boot time anymore.Better than blacklist it.But be sure before you have current proprietary driver installed too.And yes,you don't need an internet connexion for that.;)


I already did tried this,  but  still having a hard time installing the proprietary driver tho,  still says i need to get rid of xserver..   and well  im stumped with it...  lol...

---

### Post by DJ Wings on 2010-09-07
YES.
[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup")
I followed the instructions, and I'm posting from Xubuntu 10.04. You have no idea how happy this makes me.

---

### Post by toffuuu on 2010-09-08
> **DJ Wings said:**
> YES.
[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)
I followed the instructions, and I'm posting from Xubuntu 10.04. You have no idea how happy this makes me.

I dont see how this code from this site will help me,  cause i am not at all using an LCD monitor..  im using a regular Dell CRT moniter altho i will be upgrading that some time in the future, so i can get higher resolution then 1024x768  lol.    but again im not exactly sure what my puter recognizes my screen as right now, but hold on,   just says "Monitor Dell 13"  "

---

### Post by Onthax on 2010-09-08
I was having the low-graphics issue where on reboot it wouldnt load the nvidia kernel module, unplugged vga port, used a DVI adapter, all working fine now

---

### Post by messiah5150 on 2010-09-09
I have an HP HDX18 1180CA...I had the problem that arizonagirl11 had... By a stroke of luck...I remedied the issue.

When I first installed, I had crappy gfx...low res, so Under hardware drivers, I had a choice of the 173 driver or the newer one. Instinctively, I went with the newer one, installed it and re-booted Ubuntu. Upon reboot...I was sorrily disappointed. No change, so I chose the Version 173 and rebooted. Voila! Hi-REZ GFX, but got the Nvidia X Server Error and no 3d Acceleration. Crap... Oh well...GFX look good.

Now, after reading this thread...I decided to try my luck. By this point, I've been running Ubuntu 10.04LTS since just after its release. I chose the Recommended Driver (which last time did not work). I activated the driver, rebooted and I almost cried as I had full Hi Rez GFX and Full 3d support and Nvidia support working. I dunno how...must have been a fluke of nature, but everything is working 100%. Now...the splash screens look like crap, but I don't care. Once the Login screen pops up, its at full 1920x1080 along with the rest of my desktop.

@ arizonagirl11: Try it...see what happens...just for kicks. It may or may not work. I haven't used any code that's been listed in the this tread...only read. I share(d) your frustration and hopfully this will work.

---

### Post by flodt22 on 2010-12-28
for what it's worth, I tried all of the fixes listed and none worked. as a hunch i looked up my monitor's HorizSync and VertRefresh. xorg.conf listed values outside of the recommended values. after a little bit of trial and error. I was able to get resolution rates greater than 640x480. I guess you can't always blame the drivers.

---

### Post by dennisra on 2011-01-02
I have been having similar problems with xubuntu 10.04 and an older nvidia card.  i've tried all of the solutions suggested above with no success.  Finally I downloaded nvidia-common and installed Version 96, and so far it's working after several reboots so I am cautiously optimistic.

---

### Post by bdalzell on 2011-01-12
> **Zarckon said:**
> Just wanted everyone in this thread to know that at least for me, I appear to have stumbled on to a solution. I did a search for Nvidia in Synaptic and found that the Nvidia-kernal-common was not installed. I installed that and have had my first error free boot in about a week. Why that would suddenly become necessary after years of perfect boots without it is a mystery to me, but the installation does appear to have corrected the problem of booting into low graphics mode.


I have been trying to get Lucid to work correctly for over a week since upgrading from Karmic using the Update Manager.

I had tried almost all of the fixes discussed in this thread - of course some of them may have been necessary to work towards the solution - but this one is the one that has finally made Lucid come up in my high resolution mode on my wide screen Acer monitor using the 32.27 kernel.

The current display is at 1680 x 1050 an 50 Hz.
However when I bring up the Monitor Preferences(System>Preferences>Monitors) I get the message:

> 
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead

I answer "NO" to this requestor and it closes and displays the Monitor Preferences gadget.

:KS

---

### Post by Henk Poley on 2011-09-10
Something odd happened. Some update broke the `nvidia` driver, and Ubuntu now runs failsafe. I don't know since how long. Probably not longer than a week, since the system only recently needed a gdb restart to actually show something on the screen.

Anyways, `sudo nvidia-xconfig -a` fixed it, and these are the changes:

```
--- /etc/X11/xorg.conf.backup	2011-09-10 20:38:48.000000000 +0200
+++ /etc/X11/xorg.conf	2011-09-10 20:38:48.000000000 +0200
@@ -29,7 +29,7 @@
 	# Keyboard settings are now read from /etc/default/console-setup
 	#	InputDevice    "Mouse0" "CorePointer"
     Identifier     "X.org Configured"
-    Screen      0  "Screen0" 0 0
+    Screen      0  "Screen0"
     InputDevice    "Keyboard0" "CoreKeyboard"
     InputDevice    "Mouse0" "CorePointer"
     Option         "Xinerama" "0"
@@ -80,27 +80,13 @@
 Section "Monitor"
     Identifier     "Monitor0"
     VendorName     "Unknown"
-    ModelName      "SONY TV"
-    HorizSync       14.0 - 70.0
-    VertRefresh     48.0 - 62.0
-    Option         "RenderAccel"
+    ModelName      "Unknown"
+    HorizSync       28.0 - 33.0
+    VertRefresh     43.0 - 72.0
+    Option         "DPMS"
 EndSection
 
 Section "Device"
-
-	#Option     "SWcursor"           	# [<bool>]
-	#Option     "HWcursor"           	# [<bool>]
-	#Option     "NoAccel"            	# [<bool>]
-	#Option     "ShadowFB"           	# [<bool>]
-	#Option     "UseFBDev"           	# [<bool>]
-	#Option     "Rotate"             	# [<str>]
-	#Option     "VideoKey"           	# <i>
-	#Option     "FlatPanel"          	# [<bool>]
-	#Option     "FPDither"           	# [<bool>]
-	#Option     "CrtcNumber"         	# <i>
-	#Option     "FPScale"            	# [<bool>]
-	#Option     "FPTweak"            	# <i>
-	#Option     "DualHead"           	# [<bool>]
     Identifier     "Device0"
     Driver         "nvidia"
     VendorName     "NVIDIA Corporation"
@@ -112,14 +98,6 @@
     Device         "Device0"
     Monitor        "Monitor0"
     DefaultDepth    24
-    Option         "TripleBuffer" "True"
-    Option         "UseEvents" "True"
-    Option         "XvmcUsesTextures" "false"
-    Option         "RenderAccel" "1"
-    Option         "NoLogo" "True"
-    Option         "OnDemandVBlankInterrupts" "True"
-	#	Option "CustomEDID" "DFP-1:/home/mythtv/edid-32W4000-no-exts.bin"
-    Option         "TwinView" "0"
     SubSection     "Display"
         Depth       24
     EndSubSection
```

Maybe somebody can enlighten me why this caused a "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)" line in /var/log/Xorg.failsafe.log

Laterally: the first step of the Linux boot sequence now has a blinking cursor instead of the bootlogo, later on it appears again. How do I repair the bootlogo?

---

### Post by DeadJackal on 2012-02-24
I know this is an older thread but I found myself stopped cold by Nvidia display problems in 10.04 I spent several days working on it and eventually was able to get it fully operational just a few minutes ago. 

Maybe what I post here will not be of much use but maybe someone will find it useful. 

I found that the new driver set 295.20 seems to run just fine on this system. I was able to easily download this from Nvidia.com 
[http://www.geforce.com/Drivers/Results/41580](http://www.geforce.com/Drivers/Results/41580)

I first tried to use Synaptic package manager to install these drivers none worked and no modification seemed to either. I had to completely remove the installation files and then stop X and run the new drivers from Nvidia as root 
( sudo sh NVIDIA-Linux-X86-295.20.run ) or ( sudo sh NVIDIA-Linux-X86_64-295.20.run )
after setting up xconfig and restarting everything worked perfectly. 

I am very new to Ubuntu and Linux and this was my first big rise to using the OS but  I am enjoying it and I hope this helps someone else that may be having trouble as well.

---

