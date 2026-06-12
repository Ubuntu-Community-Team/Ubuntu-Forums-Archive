---
title: "Can't enable graphics effects in 2.6.34-020634rc6 kernel"
date: 2010-07-13
forum: General Help
---

### Post by gaalaaant on 2010-07-13
Running lucid in wubi and had issues with a wiggling screen on the 2.6.32 kernel.  To solve it, a poster suggested i update to 2.6.34-020634rc6.  The wiggling stopped, but now I can't get even the normal setting to work (goes straight to "searching for drivers").  Help would be much obliged.

---

### Post by Twitch6000 on 2010-07-13
> **gaalaaant said:**
> Running lucid in wubi and had issues with a wiggling screen on the 2.6.32 kernel.  To solve it, a poster suggested i update to 2.6.34-020634rc6.  The wiggling stopped, but now I can't get even the normal setting to work (goes straight to "searching for drivers").  Help would be much obliged.

This is because of lack of a stable api. The drivers are not updated for that kernel. So you have two choices go back and try something else to solve the problem. Or install a different kernel version. 2.6.33 should work fine.

---

### Post by gaalaaant on 2010-07-13
could you please explain how to install 2.6.33?  Will 2.6.33 bring back the wiggle possibly? 


PS: Doubt you would know this but just in case: was the problem with 2.6.32 that 33 fixed graphics-wise widespread?

---

### Post by Twitch6000 on 2010-07-13
> **gaalaaant said:**
> could you please explain how to install 2.6.33?  Will 2.6.33 bring back the wiggle possibly? 


PS: Doubt you would know this but just in case: was the problem with 2.6.32 that 33 fixed graphics-wise widespread?

I would not know if 2.6.33 will bring your old problem back,but I know it will fix your new problem.

The download for 2.6.33 is found here - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

---

### Post by clhsharky on 2010-07-13
gaalaaant

Kernel 2.6.34.1 stable is out, here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.1-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.1-maverick/)

Sharky

---

### Post by gaalaaant on 2010-07-13
thanks sharky.  

EDIT: whups twitch didn't see your post. Will try both.  Big thanks to both of you.

EDIT 2:  Sharky I assume I download 	linux-headers-2.6.34-02063401-generic_2.6.34-02063401_i386.deb?

EDIT 3: Tried that, wouldn't let me.  Installed the headers one titled ALL.  Restarted.  No difference.  Will try installing source.

---

### Post by gaalaaant on 2010-07-14
did not work.  will try .33 in the morrow.

---

### Post by gaalaaant on 2010-07-14
34.1 does not solve issue, .33 brings back old issue.  Any other tips guys?

---

### Post by Twitch6000 on 2010-07-14
> **gaalaaant said:**
> 34.1 does not solve issue, .33 brings back old issue.  Any other tips guys?

Okay can you tell me about your old issue. It will probably be easier fixing it.

---

### Post by gaalaaant on 2010-07-14
It was a horizontal wiggle most likely caused by an issue with my graphics card (ATI Radeon X130)

---

### Post by Twitch6000 on 2010-07-14
> **gaalaaant said:**
> It was a horizontal wiggle most likely caused by an issue with my graphics card (ATI Radeon X130)

Are you using the open source drivers or closed source? I am not an ati user so I will only be able to help so far.

for the up to date driver try here - [http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)

---

### Post by gaalaaant on 2010-07-14
Which SHOULD I be using?  I hear the open source is better in some ways.  Also, do i have to purge my old driver or can I just install this?

---

### Post by Twitch6000 on 2010-07-14
> **gaalaaant said:**
> Which SHOULD I be using?  I hear the open source is better in some ways.  Also, do i have to purge my old driver or can I just install this?

I always suggest the closed source version. The open source one is being used by default. You can just install it,it will do the work for you atleast the nvidia one does.(I use nvidia :P )

---

### Post by gaalaaant on 2010-07-14
I was always suggested to use open (fglrx I think? or something) but Ill give this a try.

EDIT: Can't open the download for some reason.  Says gedit can't open the .run file. 


> gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

---

### Post by Twitch6000 on 2010-07-14
> **gaalaaant said:**
> I was always suggested to use open (fglrx I think? or something) but Ill give this a try.

EDIT: Can't open the download for some reason.  Says gedit can't open the .run file.

You need to save it to your desktop. 

open a terminal and run - sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

you will be on a terminal.

cd to the directory you put the driver.

then run - 

sudo sh *file name*

If you forget the file name just type what you remember and press tab. It will put it in for you. From there press enter and follow the guides.

---

### Post by gaalaaant on 2010-07-14
When it took me to the black terminal screen, I enter cd /home/dan/Downloads and then nothing happened.  Should I just have waited because I waited a good like 3-4 minutes.

---

### Post by gaalaaant on 2010-07-15
I tried multiple times to install it after stopping gdm but none worked , so I just ran sudo sh ati.run from the normal terminal and an install window came up.  Heres hoping it works.


EDIT:  Installed, then restarted gdm.  It stopped saying "searching for available drivers" when I click normal or extra effects, but still says "desktop effects could not be enabled." I guess that's a step forward, but does that mean no driver can help me?Can I roll back to an old driver for it to work?  It worked in 9 fine.

EDIT 2:  After a restart, it had reverted to a different resolution, but I fixed that, though afterwards, it again started returning "searching for available drivers" which it had stopped after a restart gdm.  It also seems to be cutting off the top and left edge of my screen a little.  The tops of my panel icons are shaved off and my show desktop button has been cleaved in two. any help?

---

### Post by Twitch6000 on 2010-07-15
Sorry for the late post.

I have three questions.

When did the wiggle problem start.

Can you state clearly what you did when trying to install the driver?

Which version of ubuntu are you using.

I cannot help you any further since this is an ati problem. However answering those three questions should make it possible for someone else to fix it for you.

---

### Post by gaalaaant on 2010-07-15
I am using Lucid in Wubi, the wiggle started when I upgraded to Lucid in Wubi from Karmic, possibly because of the update of the kernel or whatever the 2.6.32 thing is.  The wiggle is present in 33 but not in 34.  I installed the drive by doing everything you suggested except for stopping gdm because when I tried it did that same thing it does when I put it to sleep: it went to a totally white text-black screen thing, and no dan@ubuntu$ thing showed up and froze if I tried a command.  I did all the other steps, which launched a graphical installer, in which I chose default install.  I then restarted gdm, which removed the "searching for available drives" dialogue, but still returned "cannot enable gfx effects."  After I restarted the computer, my res reset, and when enabling effects, the old "searching" thing came back.  Also, the top of my top panel is now shaved off a little. Barely noticeable but I had it on my old install too.

Hope that wasn't too long-winded or poorly worded

---

### Post by gaalaaant on 2010-07-16
bumping for desperation!

---

### Post by gaalaaant on 2010-07-19
The lifehacker community tried to help on this but weren't too successful.  Please help

---

### Post by clhsharky on 2010-07-19
gaalaaant

1 There is no reason to be using kernel 2.6.34.rc7 now that stable kernel 2.6.34.1 is released. Install the stable release.

2 Your card ATI Mobility Radeon(X1xxx) is not suported with fglrx in Lucid. If you tried to install fglrx follow this and purge fglrx
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
After purging fglrx notice
> If you want desktop effects (compiz or KDE) you'll need the glx module loaded. This will not work even after purging fglrx since a hanging libglx.so file is left around. Both fglrx and xserver-xorg-core provide this file so to replace it with the correct version you'll need to reinstall xserver-xorg-core as well.
```
sudo apt-get install --reinstall xserver-xorg-core
```

3 After searching the last time I helped you I found that Compiz
cant accelerate the second monitor with OSS drivers. I dont know if has been resolved in Compiz or newer OSS drivers or not. 
You could shut off laptop monitor which you don't use any more and use your VGA monitor only.
 I'm not sure how to configure xorg.conf to do that with out more info and research.
Maybe someone could help you with that, I will try to get back to you to see how you are doing(I've been busy).

If you want to try newer OSS drivers to see if it corrects problem add this PPA and update
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

Good luck
Sharky

---

### Post by gaalaaant on 2010-07-20
Thanks for the help man.  Did all the previous stuff just adding PPA right now.  The only problem I have is that my laptop monitor IS actually off, which is why I can't  figure out the issue because I have seen issues with second monitors not working but not primaries.  Will post back after PPA update.

EDIT: Not much change after PPA update.  Icons still cut off, no effects, but now some tabs in chrome load, but dont show a tab above, though that may just be a one time issue.

---

### Post by clhsharky on 2010-07-20
gaalaaant

How is your 3D now,just wondering.

```
glxinfo | grep OpenGL
glxinfo | grep -i render
```

Sharky

---

### Post by gaalaaant on 2010-07-20
```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

```

```
glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 

```


There it is.

---

### Post by gaalaaant on 2010-07-31
Have tried multiple other fixes, still no results.  Have there been any new drivers released?

---

### Post by clhsharky on 2010-07-31
gaalaaant

Software Rasterizer is still a problem with your sys, probable making a issue with compiz

Lets check your grub cmd line is at default
```
sudo gedit /etc/default/grub
```
Should look like this
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Save
```
sudo update-grub
sudo update-initramfs -u
```
Reboot

This also register's radeon modules and hopefully no fglrx is still hanging around.

Moving up to the kernel 2.6.35 should be good for your laptop with better power management, newer DRI for OSS drivers and more. Should be a good kernel for laptops with OSS.
2.6.35.rc6 is latest, stable will be out next weak.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Sharky

---

### Post by gaalaaant on 2010-08-02
Sorry, been out of town for a bit.  Did both, but the grub line was already set to quiet splash so I guess all is well there.

---

### Post by clhsharky on 2010-08-02
gaalaaant

Kernel 2.6.35 stable version is out to day.

Link in previous post.

Sharky

---

### Post by gaalaaant on 2010-08-06
I think I installed it correctly, but it never said that a restart was required.  Is that bad?

---

### Post by dino99 on 2010-08-06
better to have a real install, instead of this joke: wine= linux inside a windoz file :o

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by gaalaaant on 2010-08-06
What? That doesn't seem to be the issue.  The issue is my laptop's card isn't supported properly I think.

---

