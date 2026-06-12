---
title: "I Reinstalled Xp now I cant boot into ubuntu"
date: 2011-06-08
forum: General Help
---

### Post by Chris Psycho on 2011-06-08
Hey guys, I had ubuntu and linux mint running with xp, then I had to reinstall xp.

Now I can't boot into ubuntu/mint as GRUB is missing if I am correct?

I looked at AutoSuperGrubDisk, but all I can find to download is super grub disk and super grub2 disk?

I do have my ubuntu disk still, can I do it from there, if so how?

Thanks for your time and have an awesome day :)

---

### Post by Mark Phelps on 2011-06-08
Window OSs automatically rewrite the MBR whenever they are installed/reinstalled.  So, that killed off access to GRUB during your boot process.

To reinstall GRUB from an Ubuntu CD, read the link below:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by seawolf167 on 2011-06-08
Here is the GRUB [re-installation guide]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2").

---

### Post by Chris Psycho on 2011-06-11
Thanks guys!

By the way, where is the solved button?

---

### Post by seawolf167 on 2011-06-11
Thread tools -> mark as solved

---

### Post by Chris Psycho on 2011-06-14
I'm back... Grr...

Ok so after looking through 'The GUI Way: Using the Alternate/Install CD and Overwriting the Windows bootloader', - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

At step 4: mount the appropriate linux partitons? How do I do that exactly?

All I find is an option like 'use this partion as...' swap/ext4 file system/ntfs, there are another 2 swap partitions and yeah....................................

I had ubuntu and linux mint installed to make things even less complicated... (joke)..

---

### Post by seawolf167 on 2011-06-14
That method is for Grub legacy - see [this section ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")about reinstalling Grub2 the GUI way and see if you have any problems with it.

---

### Post by Chris Psycho on 2011-06-14
Ok :D hopefully I nail it!

---

### Post by Chris Psycho on 2011-06-15
Right... I'm back...........................................................

That update command is updating the whole ubuntu right? Well =/ I don't have allot of internet bandwidth. If I leave it out, it doesn't seem to install?...

Should I just delete the whole thing and start over?

---

### Post by seawolf167 on 2011-06-15
> **Chris Psycho said:**
> Right... I'm back...........................................................

That update command is updating the whole ubuntu right? Well =/ I don't have allot of internet bandwidth. If I leave it out, it doesn't seem to install?...

Should I just delete the whole thing and start over?

What update command do you mean?

```
sudo update-grub
```

or

```
sudo apt-get update
```

---

### Post by Chris Psycho on 2011-06-15
> **seawolf167 said:**
> What update command do you mean?

```
sudo update-grub
```or

```
sudo apt-get update
```

sudo apt-get update

---

### Post by seawolf167 on 2011-06-15
The command 

```
sudo apt-get update
```

only updates the package list in /etc/apt/sources.list

the command

```
sudo apt-get upgrade
```

actually downloads and installs the new and updated packages/programs

---

### Post by Chris Psycho on 2011-06-15
> **seawolf167 said:**
> The command 

```
sudo apt-get update
```only updates the package list in /etc/apt/sources.list

the command

```
sudo apt-get upgrade
```actually downloads and installs the new and updated packages/programs

So sudo apt-get UPDATE only updates the required packages? So I have to retry that?

Whats a reasonable size that boot-repair would take? I mean as in 1-100mb?

---

### Post by seawolf167 on 2011-06-15
> **Chris Psycho said:**
> So sudo apt-get UPDATE only updates the required packages? So I have to retry that?

Whats a reasonable size that boot-repair would take? I mean as in 1-100mb?

the *update* command only update the package list. the *upgrade* command actually downloads and installs the updates.

to repair your boot menu by reinstalling GRUB you need to follow the instructions in the link I posted earlier - these commands will not fix your boot menu, reinstall grub or update the grub menu

---

### Post by Chris Psycho on 2011-06-15
> **seawolf167 said:**
> the *update* command only update the package list. the *upgrade* command actually downloads and installs the updates.

to repair your boot menu by reinstalling GRUB you need to follow the instructions in the link I posted earlier - these commands will not fix your boot menu, reinstall grub or update the grub menu

??? 

I'm confused.

In order to repair GRUB2 I have to install Boot-Repair right?
Now according to here: [https://help.ubuntu.com/community/Boot-Repair#Getting%20Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting%20Boot-Repair)

I should run: 

[LIST]
[*]sudo add-apt-repository ppa:yannubuntu/boot-repair
[*]sudo apt-get update && sudo apt-get install boot-repair-ubuntu
[/LIST]

I'm guess the second point is two commands?

---

### Post by seawolf167 on 2011-06-15
See my [post #3]("http://ubuntuforums.org/showpost.php?p=10916425&postcount=3"). The [link again]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files"). Just put in your live cd (which you installed Ubuntu with), mount your partition, then run the proper grub-install command.

---

### Post by WorMzy on 2011-06-15
You don't need to download anything extra. The tools you used to install grub the first time will suffice to reinstall it now. By the first time, I mean the CD/USB stick you used to install Ubuntu or Mint; only this time, you don't need to install Ubuntu or Mint to get grub back. You can use the graphical tool you're trying to install if you want, but there are other methods listed on that page.

---

### Post by Chris Psycho on 2011-06-16
Yes it worked! Thank you for everyones patience! 

:p

---

### Post by seawolf167 on 2011-06-16
Glad you got it working! :D

---

