---
title: "Is the new kernel broken? (2.6.15-25)"
date: 2006-06-15
forum: General Help
---

### Post by Jucato on 2006-06-15
A few hours ago, most of us were probably informed that there are new updates available. This was for the upgrading the kernel from 2.6.15-23 to 2.6.15-25. It seems to be related to a security issue mentioned here: [http://www.ubuntuforums.org/showthread.php?t=197181](http://www.ubuntuforums.org/showthread.php?t=197181)

Automatic installation and upgrade (via Synaptic and Adept Updater) went without problems. The problem starts to creep in upon restarting. I've searched the forums and it seems that some people, including me, are also experiencing different problems after updating to this new kernel. So I was wondering if anyone else is having trouble with the kernel upgrade.

My own problems are both in Ubuntu and Kubuntu. 

1. Ubuntu: mouse doesn't work in the new kernel, but it reaches the GDM login screen. However, the keyboard does work. This is a fresh install, no other packages except the kernels were installed, only upgraded. This happened both to the k7 kernel I installed (using AMD) and the 386 kernel that was installed by default. No amount of dpkg-reconfigure xserver-xorg seems to work.

2. Kubuntu: Doesn't even reach KDM login, just freezes at the bootsplash (but I can still open a virtual terminal). This isn't a very fresh install, and I have installed nvidia-glx and the linux-restricted-modules for k7. I have not tried reconfiguring xserver, for fear of messing it up and not being able to log in to the older kernel version I still have.

I also noticed that the security bulletin I linked to above recommends that linux-restricted-modules-2.6.15-23-k7 be upgraded to linux-restricted-modules-2.6.15-25-k7 2.6.15.11-2, and that linux-restricted-modules-k7 2.6.15.22 be upgraded to linux-restricted-modules-k7 2.6.15.23. The problem is, none of these packages exist in the repositories, and in packages.ubuntu.com.

Is anyone experiencing problems with the new kernel, too? Is there any news/announcement regarding this?

---

### Post by fargoth on 2006-06-15
sorry to hear about your misfortune
what mouse are you using?

i just updated, and it went smoothly enough.
i got my mouse =)
maybe the shutdown bug was finally fixed? (going to check it out now)

you might want to report the bug your having here
[https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/)

---

### Post by DancingSun on 2006-06-15
I have problems with the new kernel too!

Apparently it doesn't have the evdev module installed and my mouse would not initialize, and this would cause Xserver to not load.  I had to boot up using the default mouse config in xorg.conf

On a side note, the upgraded kernel was a generic one, whereas my old kernel K-8 kernel did not get the upgrade.

---

### Post by Jucato on 2006-06-15
[QUOTE=fargoth]sorry to hear about your misfortune
what mouse are you using?

i just updated, and it went smoothly enough.
i got my mouse =)
maybe the shutdown bug was finally fixed? (going to check it out now)

you might want to report the bug your having here
[https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/)[/QUOTE]

My mouse is just a generic PS/2 mouse. This is really, really strange. In Kubuntu, I don't even have a GUI! Good thing I kept my old 2.6.15-23 kernel...

---

### Post by BobBlum on 2006-06-15
Something is definitely broken.  I always logged in automatically to my personal account.  After updating to the new kernel a few hours ago, I am asked for a password.  This is ridiculous!  Hope someone in charge is reading this.

---

### Post by xXx 0wn3d xXx on 2006-06-15
[QUOTE=BobBlum]Something is definitely broken.  I always logged in automatically to my personal account.  After updating to the new kernel a few hours ago, I am asked for a password.  This is ridiculous!  Hope someone in charge is reading this.[/QUOTE]
I have this problem too. Other then that nothing is wrong with it for me.

---

### Post by kvonb on 2006-06-15
Me too with the broken "automatic" login!  I get a black background with a theme-less crusty old login box asking for my password, if I purposely mess up the first attempt, it then loads the themed login window!

---

### Post by DancingSun on 2006-06-15
ok, I fixed my problem by installing the newest kernel for AMD (probably not needed, but I would be installing it anyway), installing the latest restricted kernel modules, reinstalling evdev driver for X, reinstalling the nvidia module and driver.

---

### Post by jnev on 2006-06-16
it worked for me on both my desktop and laptop without issue... guess I got lucky :-$

---

### Post by Jucato on 2006-06-16
I guess I'll try again in a while. I can understand my case with Kubuntu, as I installed the nvidia drivers, so I probably need to reinstall it. But I can't understand the case with Ubuntu, as it was a very, very fresh install. 

*sigh* just the little things that get to you. Add this to the not-so-very-nice Kubuntu Breezy-Dapper upgrade experience. :(

---

### Post by JSVH on 2006-06-16
I am also having problems. Automatic login is broken, and my wireless card no longer works. It was rigged through some form of ndiswrapper I think. Either way it was a Broadcom card and was a pain to setup I would really like to not do it again.

---

### Post by raffytaffy on 2006-06-16
worked ok on my instalation

---

### Post by hajk on 2006-06-16
[QUOTE=Fenyx]

1. Ubuntu: mouse doesn't work in the new kernel, but it reaches the GDM login screen. However, the keyboard does work. This is a fresh install, no other packages except the kernels were installed, only upgraded. This happened both to the k7 kernel I installed (using AMD) and the 386 kernel that was installed by default. No amount of dpkg-reconfigure xserver-xorg seems to work.

[/QUOTE]

Same here, but another reboot fixed the mouse problem!

---

### Post by Bokonon on 2006-06-16
No problems so far on my lappy.  I installed the kernel on my AMD64 machine, but have yet to come home to test it.

---

### Post by Jucato on 2006-06-16
[QUOTE=hajk]Same here, but another reboot fixed the mouse problem![/QUOTE]

You're lucky. I've rebooted numerous times, and still no mouse. I see the cursor, but it doesn't move. It only works in the old 2.6.15-23-386 kernel...

In both Kubuntu and Ubuntu, I've tried every possible solution. I have no idea how to make the mouse work in Ubuntu, and have no idea how to get X up in Kubuntu.

... I give up. I guess I'll stick to the old kernel for a while. But I want a k7 kernel in Ubuntu. Unfortunately, the only k7 kernel available now in the repositories is the new one...

---

### Post by tseliot on 2006-06-16
[QUOTE=Fenyx]2. Kubuntu: Doesn't even reach KDM login, just freezes at the bootsplash (but I can still open a virtual terminal). This isn't a very fresh install, and I have installed nvidia-glx and the linux-restricted-modules for k7. I have not tried reconfiguring xserver, for fear of messing it up and not being able to log in to the older kernel version I still have.[/QUOTE]
Please, read the part of my guide where it says "WHAT HAPPENS IF YOU CHANGE YOUR KERNEL OR IF YOUR KERNEL IS UPDATED":

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by mym on 2006-06-16
I have low performances since this update on my laptop (Pentium M 2Ghz, ATI X700 with Free drivers, 1024Mo DDR2).
'top' doesn't reveal any app taking a lot of resources but my system is globaly less reactive, videos are choppy, even animated gif with firefox play with some lags.
I don't know from where it comes.

---

### Post by Jucato on 2006-06-16
[QUOTE=tseliot]Please, read the part of my guide where it says "WHAT HAPPENS IF YOU CHANGE YOUR KERNEL OR IF YOUR KERNEL IS UPDATED":

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")[/QUOTE]

Thank goodness you dropped by. Maybe you could help me solve at least Kubuntu's X problem. 

I have read that and tried to do it. Guess what? The only linux-restricted-modules available are linux-restricted-modules-**2.6.15-23-k7**, while the upgrade installs linux-image-**2.16.15-25-k7**. I'm guessing that this is causing the problem for Kubuntu, since the nvidia-glx relies on the the restricted modules right?

But I'm still clueless on what to do with the mouse in Ubuntu...

---

### Post by tseliot on 2006-06-16
[QUOTE=Fenyx]Thank goodness you dropped by. Maybe you could help me solve at least Kubuntu's X problem. 

I have read that and tried to do it. Guess what? The only linux-restricted-modules available are linux-restricted-modules-**2.6.15-23-k7**, while the upgrade installs linux-image-**2.16.15-25-k7**. I'm guessing that this is causing the problem for Kubuntu, since the nvidia-glx relies on the the restricted modules right?

But I'm still clueless on what to do with the mouse in Ubuntu...[/QUOTE]
```
sudo apt-get update
```

and try again.

If the restricted modules for your kernel aren't available yet I suppose it's because they are still uploading them to the servers in your nation.


A quick fix:
Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then
```
sudo /etc/init.d/gdm start (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm start (if you use KDM)
```

If "nv" doesn't work you can try with "vesa"

---

### Post by yaztromo on 2006-06-16
I changed my Xorg.conf a long time ago to use evdev for the mouse. Does this mean that if I reboot now and use the new kernel my mouse will be borked?

---

### Post by nuzzy on 2006-06-16
looks like the kernel update is now being held back in the repos...

---

### Post by mtron on 2006-06-16
my system is totally broken, after updating the kernel, and removing usplash, the next reboot ended with 

Uncompressing Linux ... ok, booting the kernel
/scripts/init-premount/udev: 24: /sbin/udevd: not found
/scripts/local-top/udev: 30: /sbin/udevplug: not found

dam...

---

### Post by Jucato on 2006-06-16
@tseliot. thanks for the pointers. I found the root of my problem in Kubuntu. it seems that the restricted component for dapper-security is not included by default, and it was there where the linux-restricted-modules-2.6.15-25-k7 was located. (I presumed it was in dapper restricted or dapper-upgrades restricted. Shouldn't it be?) Anyway, adding that solved the problem regarding nvidia.

But now I'm back to the same problem that Ubuntu has: the mouse is not functional. What should I do? I have no idea with this "evdev", and this is the first time I actually encountered a non-functional mouse. Is this related to xorg.conf? I'm getting a bit frustrated... 

Thanks again, tseliot. :D

---

### Post by tseliot on 2006-06-16
[QUOTE=yaztromo]I changed my Xorg.conf a long time ago to use evdev for the mouse. Does this mean that if I reboot now and use the new kernel my mouse will be borked?[/QUOTE]
I guess not. The xorg.conf is not changed by the kernel.

---

### Post by tseliot on 2006-06-16
[QUOTE=Fenyx]@tseliot. thanks for the pointers. I found the root of my problem in Kubuntu. it seems that the restricted component for dapper-security is not included by default, and it was there where the linux-restricted-modules-2.6.15-25-k7 was located. (I presumed it was in dapper restricted or dapper-upgrades restricted. Shouldn't it be?) Anyway, adding that solved the problem regarding nvidia.

But now I'm back to the same problem that Ubuntu has: the mouse is not functional. What should I do? I have no idea with this "evdev", and this is the first time I actually encountered a non-functional mouse. Is this related to xorg.conf? I'm getting a bit frustrated... 

Thanks again, tseliot. :D[/QUOTE]
I can't help you with your mouse.

Try with a:
```
sudo dpkg-reconfigure xserver-xorg
```
and select the mouse you need to use.

---

### Post by yaztromo on 2006-06-16
[QUOTE=tseliot]I guess not. The xorg.conf is not changed by the kernel.[/QUOTE]

[quote=dancingsun]Apparently it doesn't have the evdev module installed and my mouse would not initialize, and this would cause Xserver to not load. I had to boot up using the default mouse config in xorg.conf[/quote]

No but it would seem to remove evdev and cause a problem. I'll reboot my machine anyway and find out.

---

### Post by Jucato on 2006-06-16
[QUOTE=tseliot]I can't help you with your mouse.

Try with a:
```
sudo dpkg-reconfigure xserver-xorg
```
and select the mouse you need to use.[/QUOTE]

I tried, I really did. No effect. Thanks, anyway. You've been a great help.

I guess I'll have to stick to the older kernel. :(

---

### Post by tseliot on 2006-06-16
[QUOTE=Fenyx]I tried, I really did. No effect. Thanks, anyway. You've been a great help.

I guess I'll have to stick to the older kernel. :([/QUOTE]
File a bug on Launchpad (it's an easy thing to do) so that they fix the problem ASAP.

---

### Post by frodon on 2006-06-16
No problem for me with this update (i have the restricted modules installed).

---

### Post by l4v4_f10w on 2006-06-16
No i dnt think so, i do believe the evdev that comes with the update supposed to be broken, so i still use the older version which works fine and just lock it, just upgraded my kernel too and had problems with my graphics im using atiX800.
What i did was just uninstall all fglrx packages and reinstall them, works fine now like before. So if anyone has any problems im thinking reinstalling ur graphic package should solve the problem.

---

### Post by Jucato on 2006-06-16
[QUOTE=tseliot]File a bug on Launchpad (it's an easy thing to do) so that they fix the problem ASAP.[/QUOTE]

I guess I should. But I'm not even sure if it's a bug, or just something that I did wrong. It also seems that others who had an almost similar problem were able to resolve the problem just by rebooting (again and again...). I also don't know how to file bugs... but I guess there's always a first time... :D

---

### Post by Princey on 2006-06-16
So far, no problem with the updates. In fact, one nagging issue regarding my display drivers was fixed. Used to get a grey/black/white screen for 2 seconds before the login prompt to kdm came up. This seems to be gone with the upgrade. Note, I'm using the amd k-k8 kernel. One thing I've noted though is that the default 64bit kernel and my previous k8 kernel all remained (I just said update via adept when it prompted me) and are all listed as part of the grub menu when I rebooted. Wireless still works flawlessly.

---

### Post by Jucato on 2006-06-16
[QUOTE=Princey]Used to get a grey/black/white screen for 2 seconds before the login prompt to kdm came up. [/QUOTE] I think that's just the X server setting itself up. It's natural, though. When you have a faster system, it doesn't appear that long.

>  One thing I've noted though is that the default 64bit kernel and my previous k8 kernel all remained (I just said update via adept when it prompted me) and are all listed as part of the grub menu when I rebooted. Wireless still works flawlessly.
That's the default behavior. New or updated kernels are added the GRUB menu. You can remove the older kernels by uninstalling them if you want. But you can safely leave one of the older, perfectly working kernels, just in case the newer ones get messed up.

---

### Post by Princey on 2006-06-16
[QUOTE=Fenyx]I think that's just the X server setting itself up. It's natural, though. When you have a faster system, it doesn't appear that long.


That's the default behavior. New or updated kernels are added the GRUB menu. You can remove the older kernels by uninstalling them if you want. But you can safely leave one of the older, perfectly working kernels, just in case the newer ones get messed up.[/QUOTE]

Thanks Fenyx, I won't touch anything. Doesn't bother me even if grub goes 2 pages long. However, I do have a decent system (AMD 64 X2 3800+, 1GB dual channel DDR RAM, SATA 250 GB [running linux] 80GB [running windows], ATI X600 250MB with X600 secondary tv tuner). I had previous issues installing a fresh install with Dapper and had to opt for the live CD booting using the limited graphics options. I think that's was my problem. I've read similar problems with the ATI cards.

---

### Post by Princey on 2006-06-16
A quick question for you, Fenyx, did you have any issues upgrading to KDE 3.53? Even with the system wide updates, I still notice that I have KDE 3.52. What are the advantages with 3.53? Yes, I've read the changelogs but it's nice to hear from those actually using it.

---

### Post by Jucato on 2006-06-16
I see, it might be an issue for ATI cards (I'm using NVIDIA). One of the biggest changes that I've experienced in KDE 3.5.3 is KDE loading 2x faster than previous KDE versions. Also it seems a bit faster, too. There were very minimal "visible" changes, and I haven't checked on the changelogs for KDE 3.5.3 so I couldn't really confirm or deny them. All I can say is that it's faster.

---

### Post by BobBlum on 2006-06-16
But is anyone having success getting rid of the password prompt during autologon?  Never encountered this before.  Things were working very well before this update.

---

### Post by yostral on 2006-06-16
[QUOTE=BobBlum]Something is definitely broken.  I always logged in automatically to my personal account.  After updating to the new kernel a few hours ago, I am asked for a password.  This is ridiculous!  Hope someone in charge is reading this.[/QUOTE]
This is not the new kernel...

I'm still with the old one, and I have that too. I think it's because of gdm's update (Gnome has been updated too...)

---

### Post by dngpng on 2006-06-16
I have problem with this new kernel too!

After upgrade, my thinkpad t43 (with an ATI card) cannot sleep normally as before anymore, using either the "ati" driver or the "fglrx" one. 

It just goes into the sleeping procedure and beep, then like having been in a sleep mode except the cpu fan is still on. No matter what key you hit afterwards, nothing good happens.

---

### Post by Princey on 2006-06-16
[QUOTE=Fenyx]I see, it might be an issue for ATI cards (I'm using NVIDIA). One of the biggest changes that I've experienced in KDE 3.5.3 is KDE loading 2x faster than previous KDE versions. Also it seems a bit faster, too. There were very minimal "visible" changes, and I haven't checked on the changelogs for KDE 3.5.3 so I couldn't really confirm or deny them. All I can say is that it's faster.[/QUOTE]

Thanks, I'll give that a go later. Got some machines to clear from the shop before the owners come grumbling :-({|=

---

### Post by givré on 2006-06-16
[QUOTE=yostral]This is not the new kernel...

I'm still with the old one, and I have that too. I think it's because of gdm's update (Gnome has been updated too...)[/QUOTE]
Yeah you're right, and because it was a big update, i think it is just a one time test. Did anyone encouter this problem again after a reboot?

---

### Post by Kallethen on 2006-06-16
Hmmm... Any reason why the ACX firmware drivers for wireless cards were removed from the new kernel?  That's going to bugger my wireless card over. :sad:

---

### Post by givré on 2006-06-16
[QUOTE=Kallethen]Hmmm... Any reason why the ACX firmware drivers for wireless cards were removed from the new kernel?  That's going to bugger my wireless card over. :sad:[/QUOTE]
Do you have the linux-restricted-modules-2.6.15-25 for your arch?

---

### Post by Bloch on 2006-06-16
After the suite of updates I got this morning, I confirm that I too no longer have automatic login. I get a small rectangle with "Automatic Login" and a field to type my password in.

Login Window Preferences has "Enable automatic log-in" ticked, as it always did. 
If a wrong password is entered I am sent to the normal gdm login screen, as if automatic login was not enabled.

Some people previously suggested the blame lies with the update to the gdm, and not the update to the kernel. I simply don't know enough, but I thought I could at least confirm what's happening,

---

### Post by Hebus95 on 2006-06-16
I updated today.
Same problem with login.
Another problem with the quit menu of gnome that does't longer have the shutdown and reboot button.

---

### Post by givré on 2006-06-16
[QUOTE=Hebus95]I updated today.
Same problem with login.[/QUOTE]
That's a gdm problem. I think it's a one time test, reboot to be sure (i don't done it yet)
[QUOTE=Hebus95]
Another problem with the quit menu of gnome that does't longer have the shutdown and reboot button.[/QUOTE]
You probably have xgl/aiglx. To work well, they hack gnome-session, but because the update replace the gnome-session from the xgl/aiglx/compiz repository, you have to wait until they have a new gnome-session in the xgl/aiglx/compiz repository (that shouldn't be too long)
Fix for the moment : exit with the terminal : sudo halt or sudo reboot

---

### Post by BobBlum on 2006-06-16
For those having trouble with the autologon password:  more attention seems to be given to this problem at [http://ubuntuforums.org/showthread.php?t=197738&highlight=gdm+update](http://ubuntuforums.org/showthread.php?t=197738&highlight=gdm+update)

The problem seems to be coming from the recent update to gdm, rather than the kernel.

I sure wish a solution would appear in the Ubuntu Update Manager.

---

### Post by givré on 2006-06-16
It's fix [https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940](https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940) :D

---

### Post by Kallethen on 2006-06-16
[QUOTE=givré]Do you have the linux-restricted-modules-2.6.15-25 for your arch?[/QUOTE]
That fixed it, thanks.

---

### Post by Lizzy on 2006-06-16
I face some troubles as well, i don't have automatic login, but when i reach the log-in screen, my keyboard doesn't work. The only thing i can do is to reboot 3 times until the keyboard works again :-)... All good things are 3 :D

---

### Post by bruce89 on 2006-06-16
Works fine for me - Linux Scooby-Doo 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64 GNU/Linux

---

### Post by Hebus95 on 2006-06-16
[QUOTE=Hebus95]
Another problem with the quit menu of gnome that does't longer have the shutdown and reboot button.[/QUOTE]
[QUOTE=givré]
You probably have xgl/aiglx. To work well, they hack gnome-session, but because the update replace the gnome-session from the xgl/aiglx/compiz repository, you have to wait until they have a new gnome-session in the xgl/aiglx/compiz repository (that shouldn't be too long)
Fix for the moment : exit with the terminal : sudo halt or sudo reboot[/QUOTE]

That's true i have xgl with compiz installed, but i don't actually use them.
Anyone know where is the conf file to make shutdown and reboot menu back?
Thanks

---

### Post by givré on 2006-06-16
[QUOTE=Hebus95]That's true i have xgl with compiz installed, but i don't actually use them.
Anyone know where is the conf file to make shutdown and reboot menu back?
Thanks[/QUOTE]
Even if you switch to metacity before, the problem is not there, wait a little to have the new gnome-session , it shouldn't be too long know (it's already there for aiglx)
Check this to now when it's ready
[http://xgl.compiz.info/pool/main/g/gnome-session/](http://xgl.compiz.info/pool/main/g/gnome-session/)

---

### Post by snellgrove on 2006-06-16
2.6.15-25 definately is crap for me - just had a black screen after a while, took probably less than an hour or something.

running 23 all day today - 17.5 hrs of uptime and probably could do a crapload more :razz: 2.6.15-23-386 is a good kernel :)

---

### Post by siriusnova on 2006-06-16
The new kernel update borked suspend and hibernate on my IBM Thinkpad T30, apparently im not the only one having this problem

[https://launchpad.net/distros/ubuntu/+bug/50029](https://launchpad.net/distros/ubuntu/+bug/50029)

im reverting to version 23 till they fix this

---

### Post by givré on 2006-06-16
[QUOTE=snellgrove]2.6.15-25 definately is crap for me - just had a black screen after a while, took probably less than an hour or something.

running 23 all day today - 17.5 hrs of uptime and probably could do a crapload more :razz: 2.6.15-23-386 is a good kernel :)[/QUOTE]
If you have an ATI or an nvidia graphic card, be sure that you upgrade also the restricted module
To do it automaticly at all update of the kernel, install
```
sudo apt-get install linux-386 (or 686 or k7, etc., according to your architecture, which you can check out by typing "uname -r")
```
see there for more info :[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by jhlaros on 2006-06-16
[QUOTE=dngpng]I have problem with this new kernel too!

After upgrade, my thinkpad t43 (with an ATI card) cannot sleep normally as before anymore, using either the "ati" driver or the "fglrx" one. 

It just goes into the sleeping procedure and beep, then like having been in a sleep mode except the cpu fan is still on. No matter what key you hit afterwards, nothing good happens.[/QUOTE]


I am also having trouble with suspend. It worked as of  2.6.15-23-386 and stopped working with 2.6.15-25-386, any progress with yours?

---

### Post by kevlarman on 2006-06-16
strange, for me, it was the other way around: 2.6.15.23 would randomly panic when i used the nv or nvidia drivers, but 2.6.15.25 magically fixed everything

---

### Post by siriusnova on 2006-06-16
[QUOTE=jhlaros]I am also having trouble with suspend. It worked as of  2.6.15-23-386 and stopped working with 2.6.15-25-386, any progress with yours?[/QUOTE]

it's a confirmed bug..

[https://launchpad.net/distros/ubuntu/+bug/50031](https://launchpad.net/distros/ubuntu/+bug/50031)

---

### Post by BaffledMollusc on 2006-06-16
[QUOTE=Kallethen]Hmmm... Any reason why the ACX firmware drivers for wireless cards were removed from the new kernel?  That's going to bugger my wireless card over. :sad:[/QUOTE]
I have an acx111 chipset, and the latest kernel (2.6.15-25-amd64-k8 ) broke my wireless too. Going back to the previous kernel (2.6.15-23-amd64-k8 ) restored it.
[QUOTE=givré]Do you have the linux-restricted-modules-2.6.15-25 for your arch?[/QUOTE]
Yes, I do. I know that fixed Kellethen's problem, but it doesn't fix mine. The latest kernel just does not work with my acx111 wireless chipset. It's very irritating, and I can't figure out why.

Sigh. I hoped that big slew of updates would fix some of the bugs I'm having, not introduce new ones :(

---

### Post by BaffledMollusc on 2006-06-17
[QUOTE=BaffledMollusc]I have an acx111 chipset, and the latest kernel (2.6.15-25-amd64-k8 ) broke my wireless too. Going back to the previous kernel (2.6.15-23-amd64-k8 ) restored it.

Yes, I do. I know that fixed Kellethen's problem, but it doesn't fix mine. The latest kernel just does not work with my acx111 wireless chipset. It's very irritating, and I can't figure out why.

Sigh. I hoped that big slew of updates would fix some of the bugs I'm having, not introduce new ones :([/QUOTE]
Okay, replying to my own problem with the solution in case it helps other people.

After lots of searching various bug reports that have been filed over the past few months, I added the following line to my /etc/modprobe.d/options file:

options acx firmware_ver=1.2.1.34

As near as I can tell, this instructs the acx driver to use the 1.2.1.24 version of the firmware rather than the default 2.3.1.31 version (found in /lib/firmware/acx). Why this is necessary in the new kernel and not the old one is a mystery to me, if indeed this change is doing what I think it's doing.

Still, my wireless appears to work now.

---

### Post by zarej on 2006-06-17
When I update to kernel 2.6.15-25, in programs which uses open sound system like beep and mplayer there is an error occured during start process and sound is disabled. Alsa emulation for oss is enabled (I saw that from Volume Control where I can switch device to oss). It's like some program alredy use oss, but all programs are closed exept beep or mplayer. My sound card is CMI-8738-MC6 and I must use OSS becouse with every other option there are minor latency and movie not synchronized. Note that on 2.6.15-23 OSS works fine. Please help!!!

P.S.  Sorry for my english

---

### Post by NewDisciple on 2006-06-17
After reading various issues like these I'm glad that I have not updated yet.  I think I'll just sit on it until it's fixed.

---

### Post by Paul Gilster on 2006-06-17
My problem with the new kernel is that on bootup, I get as far as 'Loading hardware drivers' before the system freezes. I dropped back to 2.6.15-23 and operate without any problems at all, so it's got to be that new kernel. Has anyone else run into this one?

---

### Post by xXx 0wn3d xXx on 2006-06-17
The automatic login problem appears to be fixed. I booted my system this morning and everything worked. I think it is because a few packages were upgraded yesterday such as GTK and some other things.

---

### Post by Shonkin57 on 2006-06-17
The updates seemed to come in two boatloads. The first set flummoxed my system, causing it (kdm and kubuntu running) to lock up both keyboard and mouse, forcing me to reboot. Twice or thrice this happened. Then after the next load these behaviors seemed to go away. I'm keeping my fingers crossed.

---

### Post by Roostey on 2006-06-17
My OSS sound is also broken with this update.  System sounds are OK, but I no longer get audio from Warcraft (changed to ESD in winecfg for a temoporary solution) or WinXP under VMWare (which is reporting that /dev/dsp is busy).

---

### Post by darkpark on 2006-06-17
i had the restricted kernel modules listed in synaptic, of course I also enabled several "source" repos.  Actually, i have every repository enabled... every repo that comes with a fresh install of ubuntu 6.06.  
by default, the s/w updater download the 386 kernel, but i also selected the k7 kernel and restricted modules.  after a reboot, everything worked.  my usb mouse and keyboard work and so does my nvidia 7800GS card.

---

### Post by Jucato on 2006-06-17
I was able to fix my display problem in Kubuntu (by added the restricted component in dapper-security, which is not even included by default). Now both Kubuntu and Ubuntu doesn't have working mice.

I will just probably remove the new kernels, and wait for things to subside a little. This situation has made me very sad, specially after experiencing a number of difficulties upgrading to Dapper. :(

---

### Post by nix4me on 2006-06-17
new kernel is fine for me.

nix4me

---

### Post by blimpyboy on 2006-06-17
[QUOTE=Paul Gilster]My problem with the new kernel is that on bootup, I get as far as 'Loading hardware drivers' before the system freezes. I dropped back to 2.6.15-23 and operate without any problems at all, so it's got to be that new kernel. Has anyone else run into this one?[/QUOTE]


I get as far as 'mounting files systems' (the second message displayed on the splash screen).

Booting in recovery mode shows there some issue with udev and make_queue (can't create /dev/.udev/xxx ... no such file or directory).

One in 20 reboots it gets further.

---

### Post by digimars on 2006-06-17
I have an AMD X2 4400+ dual core, and I wanted to actually go with a dual core kernel so that I could use both cores (ever since I installed Dapper about 2 weeks ago I have been running off of the default 2.16.23-386 kernel).

However, I did update to the 2.6.15-25 386 kernel and have had no problems whatsoever (I'm using this kernel now).

But I tried to install the k7-smp kernel (so that I could use both cores on my AMD), and after about 2-5 minutes of use, my entire computer locks up.  I rebooted and tested this about 5 times, and always after a couple of minutes my computer just locks up completely, can't move mouse, keyboard doesn't accept input.

So I tried to go to the previous kernel (2.6.15-23-k7 smp) and Synaptic and apt-get won't let me.  I have to take the old kernel with the new restricted modules.  So when I reboot, X craps out on me and I can't use the previous kernel.

Thinking maybe something was wrong with the k7-smp kernel, I tried the 686-smp kernel (also a 2.6.15-25 kernel), but it crashed quicker.  Then I thought maybe dual core kernels are broken with Ubuntu, so I tried a regular k7 kernel, only to have the same thing happen.

So here I am, using a 386 2.6.15-25 kernel, hoping to eventually use both of my cores.

---

### Post by Neil Crighton on 2006-06-18
I'm also having sound problems with the new kernel.  Skype no longer works (it says 'problem with sound device' or something similar when I try to call someone).  It's definitely the 25 kernel update, because if I reboot with the 23 kernel the problem goes away.

---

### Post by digimars on 2006-06-18
[QUOTE=Neil Crighton]I'm also having sound problems with the new kernel.  Skype no longer works (it says 'problem with sound device' or something similar when I try to call someone).  It's definitely the 25 kernel update, because if I reboot with the 23 kernel the problem goes away.[/QUOTE]

Are you using a non 386 kernel?  (such as a k7 or 586, 686 kernel)  I can use the 25 kernel, but only the 386 one.  If I boot into a k7, k7-smp (I have a dual core processor) or a 686-smp, my entire computer locks up after about 2-5 minutes of use.

---

### Post by Neil Crighton on 2006-06-18
[QUOTE=digimars]Are you using a non 386 kernel?  (such as a k7 or 586, 686 kernel)  I can use the 25 kernel, but only the 386 one.  If I boot into a k7, k7-smp (I have a dual core processor) or a 686-smp, my entire computer locks up after about 2-5 minutes of use.[/QUOTE]

No, I'm using the 2.6.15-25 386 kernel.  I'm not having the more serious probems that others are describing, just a problem with the sound device.

---

### Post by linuxmad on 2006-06-19
Yep.. my toshiba m-70 122 ... doesn't boot it hangs during boot......:(

---

### Post by linuxmad on 2006-06-19
Ok .. If I try with acpi=off I am able to boot ... anyone else??

---

### Post by givré on 2006-06-19
So to sum up.

- Don't forget to install the restricted module of your kernel. to do it automaticly install ```
sudo apt-get install linux-386 (or 686, 686-smp, k7, k7-smp ...depending on your arch)
```
- Recompile the driver or the module you compiled by yourself for the new kernel (ex: vmware, ...)

- If your cumputer is slow at startup, try the 386 kernel

- If your cumputer hangs during boot, try to add acpi=off in your kernel boot line

Share your tips.

---

### Post by ticool on 2006-06-19
I got the same problems with this new k7 kernel images
I have also nvidia-glx installed, i think there seems to be problem!

---

### Post by givré on 2006-06-19
did you see my post just before :wink:

---

### Post by Athropos on 2006-06-19
I upgraded to 2.6.15-25 too on three different systems. Two of them are desktop computers, and I didn't notice any problem.
The last one is my laptop, which is slow as hell with this new kernel : it feels the same as if I was logged on a remote machine and not on a local one. Everything is fine if I boot on the #23 kernel.

---

### Post by timetunnel on 2006-06-19
For me, 2.6.15-25 is broken, definitely. I still have both kernels 2.6.15-23 and -25 installed, and all of the following problems don't exist in 2.6.15-23 (This is all on a IBM Thinkpad R52):
[LIST]
[*]DVD and video playback is choppy / jerky
[*]Rhythmbox hangs very often when starting (while checking the music library)
[*]When you start an app from the panel, there's this short little animation of an extending frame. This animation needs almost 2 seconds (instead of maybe a quarter of a second) to finish and is jerky as well.
[/LIST]
Seems to be a general performance issue somewhere.

The laptop of a colleague (Samsung X20) doesn't recognize his USB stick anymore since he did the update.

This is really annoying and disappointing, because Dapper was so good so far.

I'll stick with the -23 kernel for a while. :(

---

### Post by MrEricSir on 2006-06-19
I installed restricted modules (it got uninstalled with the kernel update for some reason) and then ran the nvidia glx enabler script.

But having X die without displaying an error and then going back to the Kubuntu bootsplash screen is going to confuse a lot of people.  It looks like Kubuntu got stuck booting, which isn't exactly true.

What needs to happen to fix the Nvidia packages so this doesn't happen in future upgrades?

---

### Post by gaatmx on 2006-06-19
Issues also:
I reach the gdm screen but no mouse and no keyboard... after 20 seconds the systems freezes!
i am using the amd64-k8 kernel, restricted modules, nvidia drivers..... booting with -23 work!.
using -23 until further notice.
G

---

### Post by Hoffmann on 2006-06-19
I got NO problem here.
It is working perfectly since the upgrading.

---

### Post by handy on 2006-06-20
I upgraded about 4 hours ago, after the notification when I booted up.

Everything seemed fine until I rebooted, finding I could not start GDM.

So, I rebooted into the previous kernel, changed the** xorg.conf** line -*** driver "nvidia"***  to ***driver "nv"*** & rebooted into the new kernel no problems.

I then ran Automatix & reinstalled the nVidia drivers.

Rebooted, with no other problems found so far!

It will be easier next time! :KS

---

### Post by JamesB on 2006-06-20
[QUOTE=mym]I have low performances since this update on my laptop (Pentium M 2Ghz, ATI X700 with Free drivers, 1024Mo DDR2).
'top' doesn't reveal any app taking a lot of resources but my system is globaly less reactive, videos are choppy, even animated gif with firefox play with some lags.
I don't know from where it comes.[/QUOTE]

I've also had a performance reduction on a dell 2200 and an acer 3613. Everything is slower. I too have no idea why:confused: I hope they sort this in the next one and quickly...

---

### Post by givré on 2006-06-20
Always the same response, 
- be sure you have the new linux-restricted-module for your arch, 
- recompile the drivers and the module you compiled yourself for the new kernel.

EDIT : we should make a thread to sum up the TODO list after a new kernel
          99,99 % of the error reported here are due because people forget to upgrade the linux-restriced-module, this is not automatic until you install the   associet metapackage

---

### Post by gaatmx on 2006-06-20
I am runing amd64-k8 kernel. 
After the big updates the following problems occured:
- When booting.- It could reach the gdm screen (the nvidia logo shows up before as usual) however, the mouse and the keyboard do not respond. I could see the cursor blinking in the login prompt but after 20 seconds it stops. the only solution is hard-reboot; I could not even get ctrl-alt-f1 to work for a console.
My mouse has a little led that turns on as soon as the system is turned on, I realize that this led turned off while booting this new kernel (while booting the previous kernel, the led keeps on all the time).
I already confirmed that the restricted modules pack is installed, as well as the new nvidia-glx one.

All these issues are not present when booting the previous kernel.

Any other hint?

BTW: I am using Xgl.

---

### Post by givré on 2006-06-20
- did you compile things for XGl (ex: DRI...)
- You have the linux-restricted-module, but the new one for your arch? (just to be sure :cool: )
- Try to reconfigure xorg
```
sudo dpkg-reconfigure xserver-xorg
```
- Try to see what is the problem and fill a bug (hurry up, the last kernel update for dapper will be soon)

---

### Post by bruce89 on 2006-06-20
Every update seems to break stuff for some people, but is fine for most people.  I have never had any issues, and most breakages occur because somebody installed something manually, or changed something they mabye shouldn't have.

---

### Post by handy on 2006-06-21
[I]Quote:

Every update seems to break stuff for some people, but is fine for most people. I have never had any issues, and most breakages occur because somebody installed something manually, or changed something they mabye shouldn't have.

End Quote:
__________________
[/I]

[B]So, how do we prepare the average Ubuntu user for this often VERY stressful problem?

So that in the future they (we) are well prepared for the multitude of possible problems?

This is not an easy to pass by question![/B]

---

### Post by dale.novak on 2006-06-21
I too am having problems with kernel 2.6.15-25-386 on my Sony PCG-GRT260G laptop.  After the upgrade, I lost my video.  Xorg errored out.  Changed nvidia driver to nv driver solved that problem. Then after a successful gnome login, I discovered that the wireless no longer worked.  I reset the menu.lst to instruct grub to default back to kernel 2.6.15-23-386 and also set xorg.conf to use the nvidia driver.  All is well now, I guess I will just have to wait for a newer version of the kermel.
:(

---

### Post by Jucato on 2006-06-21
If you installed the nvidia driver and the wireless connection by installing linux-restricted-modules-2.6.15-23-386, you need to also update that package and reinstall nvidia. However, the update for the restricted modules is not immediately available, since it is located in the restricted component of the dapper-security repository. So you have to add "restricted" to the dapper-security lines in your sources.list.

Hope that will solve your problems with the new kernel.

---

### Post by scottylans on 2006-06-22
[QUOTE=Fenyx]A few hours ago, most of us were probably informed that there are new updates available. This was for the upgrading the kernel from 2.6.15-23 to 2.6.15-25. It seems to be related to a security issue mentioned here: [http://www.ubuntuforums.org/showthread.php?t=197181](http://www.ubuntuforums.org/showthread.php?t=197181)

Automatic installation and upgrade (via Synaptic and Adept Updater) went without problems. The problem starts to creep in upon restarting. I've searched the forums and it seems that some people, including me, are also experiencing different problems after updating to this new kernel. So I was wondering if anyone else is having trouble with the kernel upgrade.

My own problems are both in Ubuntu and Kubuntu. 

1. Ubuntu: mouse doesn't work in the new kernel, but it reaches the GDM login screen. However, the keyboard does work. This is a fresh install, no other packages except the kernels were installed, only upgraded. This happened both to the k7 kernel I installed (using AMD) and the 386 kernel that was installed by default. No amount of dpkg-reconfigure xserver-xorg seems to work.

2. Kubuntu: Doesn't even reach KDM login, just freezes at the bootsplash (but I can still open a virtual terminal). This isn't a very fresh install, and I have installed nvidia-glx and the linux-restricted-modules for k7. I have not tried reconfiguring xserver, for fear of messing it up and not being able to log in to the older kernel version I still have.

I also noticed that the security bulletin I linked to above recommends that linux-restricted-modules-2.6.15-23-k7 be upgraded to linux-restricted-modules-2.6.15-25-k7 2.6.15.11-2, and that linux-restricted-modules-k7 2.6.15.22 be upgraded to linux-restricted-modules-k7 2.6.15.23. The problem is, none of these packages exist in the repositories, and in packages.ubuntu.com.

Is anyone experiencing problems with the new kernel, too? Is there any news/announcement regarding this?[/QUOTE]



Add me to the list, 
[http://www.ubuntuforums.org/showthread.php?t=201544](http://www.ubuntuforums.org/showthread.php?t=201544)

Ubuntu 6.06 32bit with Nvidia 7800GT, gnome won't even fire up anymore! :(
Sad panda.

EDIT:

DAMNIT and I've since run dpkg-reconfigure xserver-xorg at that dude's suggestion, I think that has ALSO killed my install under the older -23 kernal! :(
I totally forgot I could've just chosen that but now both are hosed! :(

---

### Post by Athropos on 2006-06-22
It seems that, in my case, using #25-386 solves the problem, only #25-686 is awfully slow...

---

### Post by givré on 2006-06-22
Check your linux-restricted-module,
Check your linux-restricted-module,
Check your linux-restricted-module,

1kernel <-> 1 linux-restricted-module

---

### Post by Athropos on 2006-06-22
[QUOTE=givré]Check your linux-restricted-module,
Check your linux-restricted-module,
Check your linux-restricted-module,

1kernel <-> 1 linux-restricted-module[/QUOTE]

They are installed, exactly the version which corresponds to the kernel.

---

### Post by homersbrain on 2006-06-22
The new 386 kernel has caused jerky playback of tv through my tv card. It drops many frames, so I'm just using the old kernel. Anyone else had this?

---

### Post by handy on 2006-06-22
[QUOTE=homersbrain]The new 386 kernel has caused jerky playback of tv through my tv card. It drops many frames, so I'm just using the old kernel. Anyone else had this?[/QUOTE]

Are you using nVidia?  If so reinstall the drivers, It could be the problem.  I do it with [**Automatix**]("http://ubuntuforums.org/showthread.php?t=138405"), because I am lazy & the [**Automatix**]("http://ubuntuforums.org/showthread.php?t=138405") team are not! :KS

---

### Post by Megatog615 on 2006-06-22
I have had performance(FPS, mainly) drops with the new kernel.

---

### Post by timetunnel on 2006-07-11
Just updated to 2.6.15-26 and still have the same problems as in 2.6.15-25 (jerky video/DVD playback). Will stick with 2.6.15-23 until this issue is resolved.

---

### Post by givré on 2006-07-11
did you read that
[http://www.ubuntuforums.org/showthread.php?t=213420](http://www.ubuntuforums.org/showthread.php?t=213420)
If it does not solve your problem, fill a bug

---

### Post by majed on 2006-07-11
i updated.. all seems ok here.. didn't notice any difference, but i was not having issues anyways!

---

### Post by timetunnel on 2006-07-11
> **givré said:**
> did you read that
[http://www.ubuntuforums.org/showthread.php?t=213420](http://www.ubuntuforums.org/showthread.php?t=213420)
If it does not solve your problem, fill a bug

Thanks for that link, I hadn't read it before. But I don't have anything compiled by myself and the metapackages are there, so the update via Synaptic should do.

I filed a bug now:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52703](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52703)

---

### Post by givré on 2006-07-11
I hope you will be heared. But to be sure of that, i think you should add that you have linux-686 install and so linux-image & linux-restricted-module were upgrade at the same time. That will eliminate the possibility they will first think

---

### Post by timetunnel on 2006-08-05
Light at the end of the tunnel. Something (maybe the latest kernel update?) must have fixed the video playback problem. It's working fine now in 2.6.15-26.  :D

So now, 2.6.15-26 is *almost* usable for me. Only 3D stuff like Google Earth still doesn't work - might be related to the "mesa issue" discussed in other threads. Still have to find out more about that.

---

### Post by timetunnel on 2006-09-18
The latest kernel update to 2.6.15-27 fixed the mesa issue on my machine, so everything is back to "normal" now and I'm happy with the "new" kernel finally.

---

