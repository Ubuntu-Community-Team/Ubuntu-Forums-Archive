---
title: "Boot up and shut down screens have ugly terminal text"
date: 2010-05-04
forum: General Help
---

### Post by Dave M G on 2010-05-04
My home desktop computer upgraded to Ubuntu Lucid Lynx 10.04 without any problems.

However, after all was said and done, the boot up and shut down screens look like crap. They are all in terminal text, and without any graphics.

I have attached pictures of what they look like.

This can't be right. Is there a way I can set the system to use the proper graphics when booting up and shutting down? I like my computer to be pretty.

This is what it does for most of the boot process:
[ATTACH]155401[/ATTACH]

It does this just before the screen where I enter my password.
[ATTACH]155402[/ATTACH]

This is how it looks when it shuts down:
[ATTACH]155403[/ATTACH]

---

### Post by jschille on 2010-05-04
I had a similar issue.  
Are you using Grub2, Legacy, or still Grub 1?

[FONT=monospace]grub-install -v

Edit: Im heading off to bed.  If you don't have Grub2 follow these instructions (they worked for me).  Basically you will upgrade to Grub2 and then change some screen resolutions for your boot screen.

[/FONT]     Code:
     sudo apt-get remove grub
    sudo apt-get install grub-pc
    sudo grub-install /dev/sda
    sudo update-grub2 

After running that last command, you should see your linux and windows  install listed in the terminal output

     Code:
     sudo apt-get install v86d
    gksu gedit /etc/default/grub 

Look for the line that says:
     Quote:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"                                 
and replace it with:
     Quote:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset  video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"                                 
Then, look for the line that says:
     Quote:
     #GRUB_GFXMODE=640x480                                 
and replace it with:
     Quote:
   GRUB_GFXMODE=1280x1024  
                               
Save the file and exit gedit.

Next, run the following command:
     Code:
     gksu gedit /etc/initramfs-tools/modules 

and add this line at the end of the file:
     Code:
     uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap 

Save the file and close gedit.

Then, run this command in a terminal:
     Code:
     echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash 

Finally, run the following two commands:
     Code:
     sudo update-grub2
     sudo update-initramfs -u 

The above worked for me

---

### Post by Dave M G on 2010-05-04
Thank you for posting those great instructions before heading to bed. I appreciate you taking the time.

The issue might be something else, though, as my situation has only changed slightly.

Now, I still get similar screens as before, except that they are now in 1280x1024 resolution.

Also, there is now a new error message on boot that flickers too fast for me to see what it is. Perhaps it was there before and was too fast for me to notice. I had to take many shots with my camera to even catch a blurry hint of it.

First, I think I've upgraded to GRUB 2 as per your instructions.

```
$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu6)
```

Now when it boots, it no longer says "Starting up...", it stays on this black screen with just a flashing underline cursor for a loooooooong time:
[ATTACH]155407[/ATTACH]

Then I get the now-higher-resolution spash screen, still with no graphics, and now with a (possibly) new and too-fast-to-read error message
[ATTACH]155408[/ATTACH]

And on shut down, it seems the same, except higher resolution.
[ATTACH]155409[/ATTACH]

Any advice would be much appreciated.

---

### Post by DasFox on 2010-05-04
If you're looking and listening Canonical, the bootup and restart Splash is a BIG MESS!

I've never seen such a sloppy bootup and restart screen.

The whole idea of this mess was to hide the terminal so you don't have to see the startup and shutdown processes but it doesn't work, you always see junk spewing all over the screen and the splash screens also looks like a mess.

This bootup and restarting of Ubunto looks like some amatuer hobbyist playing with making their own Linux distro. Not only this, but it makes me wonder if anyone has, or might get damage to their video and YES software can wreck hardware and I've seen this bootup really make a mess out of my screen at times to wonder.

Really terrible Canonical, I'm sorry to say, someone really needs to get on this and get this squared away.

---

### Post by Dave M G on 2010-05-04
Just so it's clear, as the original poster, I have had no problems with boot or splash screens before this, and I just want to get this current problem resolved.

Unlike DasFox, I've generally thought the Ubuntu boot up processes were sleek and, as of Jaunty, reasonably quick.

DasFox is entitled to his opinion, but I hope this thread can stay on the topic of resolving this issue.

Thanks to everyone for their support.

---

### Post by isbiyanto on 2010-05-08
i have same problem. help me.... please

---

### Post by abgalphabet on 2010-05-12
I've the same problem when I shutdown my laptop, it jumps to a console showing strange text before a success shutdown. However, the boot experience is perfect for me.

---

### Post by notbitmonk on 2010-05-12
Dave, you mentioned that you upgraded.  Did any of the computers were freshly installed?  The first times around Ubuntu, I had to do a lot of tweaking and when I upgraded some things got messed up, though not anything as what you are experiencing.  After several times of the same thing happening, I decided that every upgrade is done via a fresh install.  Is a hassle backing things up and reinstalling software but to me is a better alternative.

EDIT: reinstalling is not the answer to this post, is just a workaround.

---

### Post by mojo2012 on 2010-05-12
I get this ugly terminal messages even on a freshly installed Lucid.
Maybe my ATI Radeon X800 PCI-e graphics cards is incompatible ... who knows?

I have such strange terminal messages and flickery boot screens since Jaunty. I remember, i was really confuse ... being a mac user ... I simply never saw such ugliness ;-)
Now 2 years later ... still the same ugliness ;-( ...
Even WinXP didn't flicker so much, and it's 10 years old! Come on Canonical, you can do better.

---

### Post by Darkdelusions on 2010-05-12
I just fixed a similar issue by following the steps posted here

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

---

### Post by tjeremiah on 2010-05-12
you can download startup manager in the Ubuntu Store. That program has an option to remove "text."

---

### Post by mojo2012 on 2010-05-14
I exactly followed the guide ... and rendered my system unbootable ...

But tjeremiah worked - at least partly. INstead of ugly terminal output I now just see a blackscreen (flickers between ubuntu logo and nothing).

On shutdown I still see ugly terminal output before the ubuntu logo is shown ...

> **Darkdelusions said:**
> I just fixed a similar issue by following the steps posted here

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

---

### Post by Dave M G on 2010-06-22
Unfortunately, none of the solutions offered here have worked, so I have reported this as a bug on Launchpad:

[https://bugs.launchpad.net/ubuntu/+bug/596182]("https://bugs.launchpad.net/ubuntu/+bug/596182")

---

### Post by Dave M G on 2011-05-10
This issue was solved by reinstalling Plymouth... or at least that's how I remember solving it.

I have since upgraded to 11.04 with a fresh install, and all boot graphics are perfectly fine.

---

