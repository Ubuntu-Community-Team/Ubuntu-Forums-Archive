---
title: "Disc Clean up or defragmenter in Ubuntu 10.10"
date: 2011-03-02
forum: General Help
---

### Post by cblnchat on 2011-03-02
Is there an equivalent to the disc clean up and defregmenter in ubuntu?  Something that cleans up extra files and defrags the ubuntu protion of the computer (i dual boot with XP btw).


Thanks

---

### Post by garvinrick4 on 2011-03-02
## This is same as a chkdsk command in dos kernel
You can only fsck an unmounted partition.
Use live CD or another linux partition if available.
```
sudo e2fsck /dev/sdxy
```x being letter of drive and y being partition number such as sda5

---

### Post by Rasa1111 on 2011-03-02
Ubuntu/Linux file systems (ext3, ext4) do not need to be defragmented like windows.(NTFS)
 
 If you want to clean up files unused/unneeded files,
Simply type ```
sudo apt-get autoclean
``` into terminal.

```
sudo apt-get clean
``` is also used.

 But I usually just use the autoclean command.

---

### Post by jerome1232 on 2011-03-02
fsck (equivalent of chkdsk) get's run automatically during startup after so much time has expired since the last check (or after so many mounts depending on the settings)

Defragmenting is generally not necessary, I know they have an online defragmenter planned for ext4 but I don't know if one has come out yet or not.

---

### Post by holycow131415 on 2011-03-02
ubuntutweak has cleaning options along with other cool things to customize your ubuntu

---

### Post by JC Cheloven on 2011-03-02
In addition to the previous advice, to keep your system clean of unused files, you also can:

- Uninstall old kernels you don't use. You can use synaptic for that. Don't forget to run "update-grub" afterwards.

- Find and remove packages that the system don't use (orphaned package dependencies) Although "sudo apt-get autoremove" should work, in my experience the program gtkorphan does a better job. You can install it from synaptic.

- In /var/cache/apt, a bunch of .deb files are stored. They are the backup installers of everything you installed in the system. You can get rid of them if you want: "sudo apt-get clean"

- Of course, temp directories can grow a lot. Specially the web browser ones. You can empty that from the app (firefox of whatever you use).

Really all about saving some disk space, but hope it helps.

---

### Post by cblnchat on 2011-03-16
> **Rasa1111 said:**
> Ubuntu/Linux file systems (ext3, ext4) do not need to be defragmented like windows.(NTFS)
 
 If you want to clean up files unused/unneeded files,
Simply type ```
sudo apt-get autoclean
``` into terminal.

```
sudo apt-get clean
``` is also used.

 But I usually just use the autoclean command.

Sorry for the delay.  And i just tried to get autoclean, but it wont let me.  Every time i try to get it i get this
```

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

```
i havent tried it on anything else yet tho. Ill edit this when i do.
Thanks

---

### Post by Rasa1111 on 2011-03-17
Maybe make sure that nothing like synaptic package manager, 
or ubuntu software center is open when you try. 

 Only terminal. 

See if that helps. 

Usually when I get a message like that,
its due to more than one of them being open at once.

---

### Post by cblnchat on 2011-03-17
> **Rasa1111 said:**
> Maybe make sure that nothing like synaptic package manager, 
or ubuntu software center is open when you try. 

 Only terminal. 

See if that helps. 

Usually when I get a message like that,
its due to more than one of them being open at once.
Kay i got it to work.  But whats it supposed to do?  Does it just run when you press enter in Terminal?  Or does it intsall something?

---

### Post by 5149.5 on 2011-03-17
> **cblnchat said:**
> Kay i got it to work.  But whats it supposed to do?  Does it just run when you press enter in Terminal?  Or does it intsall something?

It cleans up old installation files that are no longer needed. The resources to do this are already installed.

---

### Post by Rasa1111 on 2011-03-17
> Kay i got it to work. But whats it supposed to do? Does it just run when you press enter in Terminal? Or does it intsall something?

the command just runs once you type it in (and enter password)
it doesn't install anything, just quickly and effortlessly cleans up all stuff no longer needed. 

There is also a good tool in Ubuntu Tweak, that allows you to easily clean up all old packages no longer used/needed, all old kernels, all old config files, etc. 

It can all be done through synaptic package manager also..
but Tweak just makes it a bit easier/more 'together'. lol

When you use the "apt-get autoclean" command,
and once you type your password in, 
it will list all things its cleaned up, then bring you back to a fresh command line, this means it's done it's job. 

If you need help with tweak, feel free to ask.

---

### Post by matt_symes on 2011-03-17
Hi

Have a look at BleachBit as well. That can automate a lot of jobs..

```
sudo apt-get install bleachbit
```

or get it from synaptic.

Kind regards

---

### Post by Rgibbons on 2012-02-07
If you are running these commands on the main drive from a live CD, how do you tell it which drive to run the command on?

---

### Post by matt_symes on 2012-02-08
Hi

> **Rgibbons said:**
> If you are running these commands on the main drive from a live CD, how do you tell it which drive to run the command on?

Chroot onto the drive.

Kind regards

---

