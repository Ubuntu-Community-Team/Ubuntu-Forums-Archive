---
title: "Sometimes boot problem"
date: 2010-07-25
forum: General Help
---

### Post by FrostBlue on 2010-07-25
Hi everyone,
My alienware laptop doesn't boot sometimes to the login screen. It doesn't move on from kubuntu screen (the one with the animated dots). 

This happens only sometimes. When this happens if I press the power button once,the dots start moving and machine shuts down.

I also have a nvidia card and don't know if the bug has been sorted where it doesn't show proper resolution during the kubuntu dots screen.

Thanks guys.

---

### Post by linux18 on 2010-07-25
-choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-then type xinit
-when xinit starts type: metacity & - for ubuntu OR compiz & - if you have it OR flux/openbox & - if you have it OR fvwm & - for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-lastly type nm-applet & -for networking

you may need to install fluxbox and skip paneling, but doing this will almost guarantee the next few boot work properly

---

### Post by FrostBlue on 2010-07-25
So is this a kde problem or ubuntu issue.
From what you have written it seems if I change desktop env I should be fine.

---

### Post by linux18 on 2010-07-25
Its an unknown problem that effects any version of ubuntu ( gnome, xfce, lxde, openbox, kde ) ( 8.04, 8.10, 9.04, 9.10, 10.04 ) no one knows the answer ( there are over 5 threads devoted to this one issue ) any "solution"  could just be a placebo, but I'm pretty sure mine works.

---

### Post by FrostBlue on 2010-07-26
hmmm,interesting. Thanks linux18 , I will give it a shot.

---

### Post by bmullan on 2010-07-26
> **linux18 said:**
> -choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-then type xinit
-when xinit starts type: metacity & - for ubuntu OR compiz & - if you have it OR flux/openbox & - if you have it OR fvwm & - for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-lastly type nm-applet & -for networking

you may need to install fluxbox and skip paneling, but doing this will almost guarantee the next few boot work properly

I've had this _same_ problem on my AMD based machine, 4cpu, gigabyte Mobo machine, 8GB mem, two 2 terabyte HDs.

One thing I've found is that ANY kernel **AFTER 2.6.32-17**
has this *randomness* at boot time whether the system will completely boot or not.

For instance just today I downloaded and installed **2.6.32-24**

It fails to boot (I've tried cold boot, warm boot).   
Running its repair also fails to completely boot.   

My experience is that if I keep trying it "may" eventually boot but
[I]I believe there was some change after 2.6.32-17-generic
that's causing the problem.[/I]

As with 2.6.32.23...  which also fails to complete bootup many times... eventually my guess is that 2.6.32.24 will also boot "sometimes".

But why does 2.6.32.17 _always_ boot for me?   Something changed.

---

### Post by bmullan on 2010-07-26
> **linux18 said:**
> -choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-then type xinit
-when xinit starts type: metacity & - for ubuntu OR compiz & - if you have it OR flux/openbox & - if you have it OR fvwm & - for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-lastly type nm-applet & -for networking

you may need to install fluxbox and skip paneling, but doing this will almost guarantee the next few boot work properly

In my experience with this problem.... often times you can not get to a command prompt... its like its hung

---

### Post by FrostBlue on 2010-07-26
I dont have a problem like yours.My system just doesnt go from Kubuntu screen with the dots not moving.This happens like on every 8th or 15th boot,who knows.When I press the power button once,the dots move and shutdown.
Yours sounds a bit serious.
I also have nvidia car and the Lucid release notes mentioned an issue during boot with nvidia drivers I think.

I am going to try this

Scott James Remnant wrote on 2010-03-18:  Re: X server starts before Plymouth   #2  The problem here is the graphics drivers; on your system they're taking longer to load than it takes to check and mount the filesystem - so there's no reason to start the splash screen, since we can already start X.
On HDD-based systems this is worse because we do the ureadahead phase before loading drivers; thus it can take a long time for a splash to appear.
One "solution" is to use the initramfs and start plymouth as a critical step:
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
But that introduces a significant delay into boot just to get the splash screen up for the rest of it.

---

