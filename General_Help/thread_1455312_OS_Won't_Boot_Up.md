---
title: "OS Won't Boot Up"
date: 2010-04-15
forum: General Help
---

### Post by Kid Charlemagne on 2010-04-15
I'm running Ubuntu 8.04, or at least I was until it stopped working. The problem started when my anti-virus stopped working. I was told that avast wasn't working because there was a limit to how many updates it could receive due to some programming mistakes. I entered the code I was instructed to, but it didn't help. When I tried again I found my computer would no longer boot up. When I ran diagnostics the following error messages came up:

Error Code OFOO : 0244
Msg: DISK_0-Block 3319080: Can't read, replace disk or remove Write Protection.

Error Code: 0F00: 1A44

Is there a way to revert my hard drive to a point before all this started? Or some code that will get me back on track. Thanks for any help you could offer.

---

### Post by Monotoko on 2010-04-15
Why do you have an anti-virus..?
It also doesnt look to me like your anti-virus caused this...can you boot into recovery mode? (Should be the second option on your GRUB menu)

Then run: ```
fdisk -l
``` and paste the results here :)

---

### Post by Kid Charlemagne on 2010-04-15
The code I was given to repair the anti-virus caused the problem. Now when I try to boot up I get the following: "kernel.shmax" is an unknown key

---

### Post by Monotoko on 2010-04-15
Right...what was that code?
And have you tried booting the recovery kernal from GRUB?

~Daniel

---

### Post by Kid Charlemagne on 2010-04-15
I don't know how to boot into recovery mode or what a grub menu is, could you list the procedure one step at a time?

---

### Post by Monotoko on 2010-04-15
Sure,

Switch your computer on, wait for a "Press Esc to see options" or a menu screen.

At the top of the menu should be your current ubuntu build.
The second in the menu should be your recovery console.

And may i see the code you ran? This will help me solve your problem, please PM me it as it may be dangouras and i wouldnt want to see anyone else accidently running it.

---

### Post by Kid Charlemagne on 2010-04-15
Find code below:

1) open the terminal
2) a)type this command to open the file you need to edit:
Code:

sudo gedit /etc/init.d/rcS

b) type your password and hit enter

3) when the text file opens add the line:

Code:

sysctl -w kernel.shmmax=128000000

4) make sure the line you added is before:

Code:

exec /etc/init.d/rc S

5.- This is how it should look like:
Code:

#! /bin/sh
    #
    # rcS
    #
    # Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
    #

    sysctl -w kernel.shmmax=128000000

    exec /etc/init.d/rc S

6) save it

7) Reboot
AND THE NEXT TIME YOU RESTART -AVAST WILL WORK 100%

---

### Post by Monotoko on 2010-04-15
It looks genuine to me, do you have a LiveCD kicking around anywhere?

Boot it, mount your / partition, go to /etc/init.d/rcS and remove the code from it, then reboot and try again.

My advice then would be tyo uninstall Avast! as an antivirus for linux is not really worth it, and as you can see, causes more problems than its worth.

---

### Post by Kid Charlemagne on 2010-04-16
I have an Ubuntu recovery disk that came with my netbook. I just ordered an external optical drive so I can use it. I needed one anyway, but I couldn't put it off any longer given the current situation. There aren't any CD or DVD drives on my netbook.

Maybe you could give me a step by step breakdown once I have my external drive.

Incidentally the Esc key didn't take me anywhere. Maybe Dell uses a slightly different version of Ubuntu. I can get menus if I push 0 or 2 on start up, but no recovery console as far as I can tell. I used these screens to run diagnostics and listed the error codes in my initial post. Thanks for your help. I would value any additional advice you could offer me.

---

### Post by Monotoko on 2010-04-16
If you have another computer and a USB stick, you could make a Ubuntu LiveUSB

There are a few methods of doing so here:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

There is even a way to install from Windows :)

---

### Post by Kid Charlemagne on 2010-04-17
I went to that link but noticed the following :WARNING: Does NOT create persistent installs on Hardy (8.04 LTS). That is what I am currently running. When I put the recovery disk in is there a repair option or can I only reinstall? I'd hate to lose everything I have on my computer with a reinstall.

I don't really know how to "mount your partition" to remove the offending bit of code. I'm fairly new to Linux, so it would be great if you could list the steps one at a time. Would a general repair take that code out without me having to do it manually? Thanks again for all the help and information.

---

