---
title: "could not write bytes: Broken pipe"
date: 2011-11-08
forum: General Help
---

### Post by steve7777777 on 2011-11-08
A family member has an Acer netbook, 10.10 32bit installed. She turned it on today and it hung on the following message, black screen and:

**[SIZE=3]could not write bytes: Broken pipe[/SIZE]**

We think that she "accidentally" upgraded to 11.04. After this she'll let me use Clonezilla...

I searched for solutions to this, seems like an older AMD CPU is the culprit. 

I think I can do one of two things:
1. Try to get 11.10 working
2. Do a clean install - 10.04 LTS this time around

She can't do without the Netbook, this is a real headache and we need to get it up and running asap   :(  

Thanks in advance for your help!!!!!!

---

### Post by matt_symes on 2011-11-08
Hi

Before you do anything, boot into a LiveCD/USB and back up her files to an external hard drive.

It may be easier to reinstall if she needs to be up and running quickly.

LTS is a good solution if she wants the look and feel she is used to and not Unity. If she is prepared for change then 11.10 may be the way to go.

It has only recently come out though and, although i have not had any problems, there may still be bugs that need to be ironed out. You may want to wait for 11.10.1. If the processor and GPU is older it may also struggle with Unity.

Personally i like Unity but don't let my opinion sway you. I use both 10.04 and 11.10 on my computer.

When do you get that broken pipe message ? When booting up the PC ? Can you take a photo and upload it here ?

Kind regards

---

### Post by steve7777777 on 2011-11-08
> **matt_symes said:**
> Hi

Before you do anything, boot into a LiveCD/USB and back up her files to an external hard drive.

It may be easier to reinstall if she needs to be up and running quickly.

LTS is a good solution if she wants the look and feel she is used to and not Unity. If she is prepared for change then 11.10 may be the way to go.

It has only recently come out though and, although i have not had any problems, there may still be bugs that need to be ironed out. You may want to wait for 11.10.1. If the processor and GPU is older it may also struggle with Unity.

Personally i like Unity but don't let my opinion sway you. I use both 10.04 and 11.10 on my computer.

When do you get that broken pipe message ? When booting up the PC ? Can you take a photo and upload it here ?

Kind regards

Thanks for your reply. Yes, the first thing that I'll do tonight is backup the HOME directory to the SAMBA server or external hard drive.

The machine is two years old, so not ancient but my "uneducated" guess is it had a hardware problem with 11.10.

The netbook boots into a black screen, "could not write bytes: Broken pipe" It hangs. Pressing ENTER does nothing.

On a related note - how can the option to "Upgrade to 11.10" be removed? I told her not to, but it was bound to happen sooner or later, I guess.

---

### Post by matt_symes on 2011-11-08
Hi

> **steve7777777 said:**
> Thanks for your reply. Yes, the first thing that I'll do tonight is backup the HOME directory to the SAMBA server or external hard drive.

Good call. You may also consider booting into a live cd, chrooting into her install and trying to get a list of the installed applications using dpkg --get-selections. You can then use dpkg --set-selections and dselect to install them on the new install.

> The machine is two years old, so not ancient but my "uneducated" guess is it had a hardware problem with 11.10.Try a liveCD/USB version of 11.10 and see how it copes with the computer. That will, at least, give an indication of how it will behave.

> 
The netbook boots into a black screen, "could not write bytes: Broken pipe" It hangs. Pressing ENTER does nothing.There could be a whole host of things causing this. I don't often suggest this but in this case, as she wants her computer up and running quickly, reinstall.

> 
On a related note - how can the option to "Upgrade to 11.10" be removed? I told her not to, but it was bound to happen sooner or later, I guess.You show be able to do this from software sources. On the updates page, set release upgrade to none or LTS. This works on 10.04. Not sure about 11.10.

Kind regards

---

### Post by steve7777777 on 2011-11-09
Thanks again for the advice! Everything back up and running, and will back up an image using Clonezilla tonight, once the rest of the apps are reinstalled.

A few things...

* I connected to the ethernet cable to the netbook during install. I'm sure nearly everyone knows this but I mention this because it is important during the install.

* I needed to use the CHOWN command so the HOME directory could be copied to the SAMBA machine.

* For the Mozilla - hidden directory, I renamed the new install Mozilla with a ".bak " suffix and copied the backed up Mozilla to the restored machine. So bookmarks are all there.

To prevent unintentional upgrade to 11.10, I made the following change:
Software Sources->Updates tab->Release upgrade - Show new distribution releases: changed to "never"

Thanks again!!!

---

