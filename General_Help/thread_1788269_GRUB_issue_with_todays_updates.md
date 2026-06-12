---
title: "GRUB issue with todays updates?"
date: 2011-06-22
forum: General Help
---

### Post by eival on 2011-06-22
EDIT- figured it out, the issue is with grub2, i installed grub(1) and everything works fine now

i would still advise any devs who read this to follow up on the launchpad report i filed later in this thread cause im sure grub2 will be mandatory in the future and i dont wanna have to deal with this issue at that time
==============================================================


i just got the updates for today and im having a failure for 

grub-pc

it gives me an option to continue but it says my system may not startup properly

this is the exact text in the details terminal:

Setting up grub-pc (1.98-1ubuntu12)
/usr/sbin/grub-probe: error: not a directory.
Auto-detection of a filesystem module failed.
Please specify the module with the option '--modules' explicitly.

---

### Post by eival on 2011-06-22
if nobody knows this exact issue, is there a way i can just undo the install process, ill just uncheck the box and install it later once the issue is fixed

---

### Post by dino99 on 2011-06-22
the better way is to remove/purge ALL the installed grub packages from synaptic then reinstall grub-pc & grub-common

---

### Post by Dave_L on 2011-06-22
[Ubuntu 10.04]

This probably doesn't help, but I upgraded grub-common and grub-pc from 1.98-1ubuntu10 to 1.98-1ubuntu12 on Jun. 17, and didn't experience any problems.

---

### Post by eival on 2011-06-22
> **dino99 said:**
> the better way is to remove/purge ALL the installed grub packages from synaptic then reinstall grub-pc & grub-common

well how can i go about this NOW, lol cause right now the only option i have is to click "continue anyway" but is there a way to just cancel this update, or should i click continue then do as you said

im also assuming its going to prompt me to restart as soon as this update is done, so would u advise me to make those changes before restarting?

---

### Post by eival on 2011-06-22
> **Dave_L said:**
> [Ubuntu 10.04]

This probably doesn't help, but I upgraded grub-common and grub-pc from 1.98-1ubuntu10 to 1.98-1ubuntu12 on Jun. 17, and didn't experience any problems.

i normally dont even pay attention to the updates, i have it set to every day, so idk why i didnt get that same update as you

but i just wanna make sure i do what ever i gotta do before continuing cause i dont want it mess up my entire install:(

---

### Post by eival on 2011-06-22
apparently this is a grub2 issue cause it just set up a crash report and i submitted it to launchpad and it has that as the reason

but as of now, im wondering if ill even be able to boot if my computer shuts down

---

### Post by grahammechanical on 2011-06-22
You are not forced to shutdown and restart are you? The process does not automatically restart the machine unless you choose to restart. I often leave the restart until I usually switch off the machine at the end of my working period.

So, you can let the process finish and then purge and re-install GRUB2. Don't you think?

Regards.

---

### Post by eival on 2011-06-22
> **grahammechanical said:**
> You are not forced to shutdown and restart are you? The process does not automatically restart the machine unless you choose to restart. I often leave the restart until I usually switch off the machine at the end of my working period.

So, you can let the process finish and then purge and re-install GRUB2. Don't you think?

Regards.





well new issue, i purged those 2 packages but now i cant reinstall them

its essentially the same exact error i had

so what do i do now :(


ps, heres the crash report with all the extra detailed info

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/800690](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/800690)

it seems the only issue is that it can automatically detect my filesystem module and its telling me to manually specify it with that --module command

how can i do that?

---

### Post by strange_cathect on 2011-06-22
I just updated and upon reboot Ubuntu is giving me an error message that there is "no such device" and dumping me out to grub rescue prompt.

However, I never noticed any warning messages. I didn't even look. Perhaps I got them and didn't notice. 

Great.

Should I use a LiveCd to reinstall grub? Can I purge grub with the LiveCd somehow??

---

### Post by eival on 2011-06-22
> **strange_cathect said:**
> I just updated and upon reboot Ubuntu is giving me an error message that there is "no such device" and dumping me out to grub rescue prompt.

Great.

but you're posting now, so did it fix it?

or are u using another computer   D:

---

### Post by eival on 2011-06-22
this is really annoying, im now tying to use the Boot-Repair tool and it cant install it either...

---

### Post by strange_cathect on 2011-06-22
Still waiting. I'm using a laptop right now.

---

### Post by eival on 2011-06-22
i did some searches about this GRUB2 apparently others had similar issues, one issue seems to be not having your BIOS updated, which i never check, but obviously that would require shutting down to do.

but i dont think thats an issue cause i just restarted yesterday and never had any issues so worst case scenario i should be able to install the previous version but its not listed in synaptic

---

### Post by strange_cathect on 2011-06-22
I'm following this thread to reinstall grub2: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 

But I'm getting an error on the install command:
> sudo grub-install --root-directory=/mnt /dev/sdb

It says that "-root-directory=/mnt' is not a recognized option.

**UPDATE Must have mistyped something. Got it to install.

However, upon reboot I get: error: no such device . . . 

then,

grub rescue>

---

### Post by strange_cathect on 2011-06-22
I've successfully reinstalled GRUB2 using these directions: [http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

Problem remains.

---

### Post by strange_cathect on 2011-06-22
Eival,

Are you still working the problem? I'm still stuck.

---

### Post by eival on 2011-06-22
> **strange_cathect said:**
> Eival,

Are you still working the problem? I'm still stuck.

FIGURED IT OUT!

noticing in your link they mentioned grub and grub2 i simply ran a terminal code

sudo apt-get install grub

followed the steps and it installed

i then ran the sudo grub-update code

then i re-ran the grub boot repair tool and just answered Yes at the end and it was finished and gave me the "you can now restart your computer"

and im now typing this after restarting successfully

the issue is with grub2

---

### Post by eival on 2011-06-22
im really glad i got this done cause a storm just started rolling thru and i was worried the power was gonna go out:popcorn:

---

