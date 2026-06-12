---
title: "Ubuntu 10.4 Lucid Lynx OS wont boot - BLINKING CURSOR"
date: 2010-05-05
forum: General Help
---

### Post by sevenX on 2010-05-05
Hey folks, I love ubuntu so much and have been using it for 3-4 months now.  I've never had problems on my home computer or netbook with any distro. Well minor issues are always quickly solved through the help of the Ubuntu forums and its a big reason I've come to love this distribution so much is because of the community support. Now the problem I'm having is as follows...

PROBLEM: Installed UNR 9.10 on daughters (ACER Aspire One) netbook. It ran fine for a couple of months, than would not boot past splash screen.  So I re-installed UNR 9.10 again! It installed fine than soon as I updated and reboot it goes to blinking cursor and wont load anything... no grub screen, no logo splash... nothing.  So I tried to install Lucid Lynx and same thing happened.  BLINKING CURSOR! So I tried MINT... and same thing... THAT BLINKING CURSOR! So I tried install UNR 9.10 and upgrade to 10.4 in update manager and a couple hours later... reboot and voila! BLINKING CURSOR! I guess its this computer but I would really love to install the new 10.4 desktop edition on this netbook and I'm sure there is a solution to doing this with some help here at the forums.  I am still very new to linux but have a basic grasp on how to handle things here... If someone could walk me through this I would be so thankful. :p CHEERS!

---

### Post by sevenX on 2010-05-05
The computer is:

ACER Aspire One D250-1773
Intel Atom CPU N270 @ 1.60GHz

Thats about all I know ;)

---

### Post by sevenX on 2010-05-05
Could a mod move this to hardware/laptops maybe?  Or a more appropriate category.

---

### Post by flurios on 2010-05-05
same problem with [toshiba s500]("http://ubuntuforums.org/showthread.php?t=1249884"), maybe the screen?

---

### Post by sevenX on 2010-05-05
Hey Flurious I just installed 10.4 again it all goes fine and dandy... reboot and wtf it magically booted!! after maybe 20 seconds of blinking cursor but I am just updating now and reboot again see if this screws it up AGAIN! So yah... try rebooting a few times!!!

---

### Post by sevenX on 2010-05-05
yep update screws it up !!!! never mind... feeling hopeless... back to blinking cursor...

---

### Post by wwwil on 2010-05-05
Are you able to boot from the Ubuntu live CD and run Ubuntu just off the disc?

---

### Post by sevenX on 2010-05-05
I am trying to boot from 9.10 cd and I get the following error:

This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - Please use a kernel appropriate for your CPU.

---

### Post by wezell on 2010-05-05
I have to say the 10.04 'LTS' (does it mean long-term because that's how long it will be until it works?) upgrade has been a complete disaster for me. I've been using Ubuntu for years. This particular machine started with Hardy Heron and has been updated regularly with no problems. I applied the 10.04 update Monday and nothing has worked since. The blinking cursor-blank screen is certainly one symptom, but here's the full blow-by-blow:

After the update, couldn't log in. Poking around in recovery mode, libpam seems to be totally hosed. Uninstalled, reinstalled. Can now log in... for a few seconds until the kernel eats itself and panics. A few days of head-banging, and it seems the ATI Radeon (I have one, of course) driver is totally unstable. Remove the ATI, no more kernel panics.

BUT.... no desktop. More digging. Of course, the built-in graphics chip is an i810. The Intel drivers won't even load, even though they are officially part of the distribution. Drop to vesa mode. Ok, now I can start X, but still, just the damn blank screen. At least the system is running, which is really fortunate since it's my mail server, dhcp server, dns server, web server, etc.

From looking at logs, it looks like libpam is still not happy; the smbpass and gnone-keyring .so's are gone, along  with a few others. I'm one really unhappy camper right now. And no, doing a clean install is not an answer (especially since it doesn't seem to fix the problems either). That's what I expect to hear from Micro$oft, not for a Linux distro. I would have to spend days more reconfiguring a clean system. If I have to do that, I won't be doing it with Ubuntu, that's for sure.

To make matters even worse, some of these problems have been reported by many people for days now; I don't see any useful fixes coming from Ubuntu.

End of rant. At least, until I have to go spend a few more hours on this turkey. Oh yes, HELP!

---

### Post by wwwil on 2010-05-06
From the error it sounds like your trying to run Ubuntu 64 bit on a 32 bit CPU but if the disc worked before that really wouldn't make sense.

Is the 9.10 disc your using now the netbook version?

---

### Post by wezell on 2010-05-06
My upgrade was via the update manager from 9.10, and it is (was?) a 32 bit installation. I didn't select any special options, just clicked the upgrade button. Very frustrating. I just noticed that since the libpam smbpass so isn't there, samba doesn't work anymore.

---

### Post by wezell on 2010-05-06
Well, I seem to have solved the problems I've been having. It took quite a bit of fiddling. Here are the steps I took (and the problems they solved):

Kernel completely unstable using Radeon graphics card - kernel would panic within seconds to minutes. 10.04 loads a pile of Nvidia stuff. Removing all of it (apt-get purge 'nvidia*') seems to have fixed that. (fix mentioned in another thread)

Blank screen after splash screen, can't log in (the problem mentioned in this thread) - reinstalled all of the installed libpam modules, and installed gdm-desktop-environment. This is strange, because it was already installed. But, an apt-get install gdm-desktop-environment worked anyway. After these two steps, I can magically log in  and the desktop comes up. Fantastic! (the gdm-desktop-environment fix I found in another thread)

Reinstalling libpam also seems to have fixed samba not working.

I had a random collection of other issues, all related to the upgrade apparently deciding I didn't really want all the services I had running before to run in 10.4. For example, sshd was no longer being started. I suspect this set of problems is related to the upstart conversion for various services. (why this was a good idea escapes me just now)

---

### Post by wezell on 2010-05-06
Well, I seem to have solved the problems I've been having. It took quite a bit of fiddling. Here are the steps I took (and the problems they solved):

Kernel completely unstable using Radeon graphics card - kernel would panic within seconds to minutes. 10.04 loads a pile of Nvidia stuff. Removing all of it (apt-get purge 'nvidia*') seems to have fixed that. (fix mentioned in another thread)

Blank screen after splash screen, can't log in (the problem mentioned in this thread) - reinstalled all of the installed libpam modules, and installed gdm-desktop-environment. This is strange, because it was already installed. But, an apt-get install gdm-desktop-environment worked anyway. After these two steps, I can magically log in  and the desktop comes up. Fantastic! (the gdm-desktop-environment fix I found in another thread)

Reinstalling libpam also seems to have fixed samba not working.

I had a random collection of other issues, all related to the upgrade apparently deciding I didn't really want all the services I had running before to run in 10.4. For example, sshd was no longer being started. I suspect this set of problems is related to the upstart conversion for various services. (why this was a good idea escapes me just now)

---

### Post by DeeWhy2099 on 2010-05-06
Hmmm. Similar issue for me after upgrading last night. 

There were a few errors that flew past that I couldn't read in time before they disappeared during the installation, but all seemed to completely normally. 

As soon as the computer rebooted to restart, I got a quick flash on the screen of the splash login screen, seeming as though it was about to ask me for login details, then the screen went black and wouldn't complete the startup.  

Now, to make matters worse, when starting Windows on the machine (dual boot) after a few minutes I get a BSOD (which I've never seen on this computer in the four years I've had it. Toshiba Satellite A50.)

Last upgrade I did to V9 worked perfectly with no issues.  

Now all I get is black screen. If I go to Low Res bootup it works just fine -- even appears as though it's in normal res mode. SO, just need a way to automatically boot into 'Low Res' mode and it works fine... A bit odd really.

---

### Post by CoreyB. on 2010-05-07
> **sevenX said:**
> The computer is:

ACER Aspire One D250-1773
Intel Atom CPU N270 @ 1.60GHz

Thats about all I know ;)

The N270 is 32-bit, i686 only, you cannot use an x86-64, 64-bit, AMD64 version of Ubuntu on your netbook.

---

