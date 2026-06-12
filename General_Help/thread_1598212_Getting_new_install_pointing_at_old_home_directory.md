---
title: "Getting new install pointing at old home directory?"
date: 2010-10-16
forum: General Help
---

### Post by Torqumada286 on 2010-10-16
I am having to reinstall 10.10 and putting on it's own drive.  Even though I can't get my system to boot properly, my old home directory is still intact on a different drive.  How can I get the new install to point at the old home directory?  I have read the tutorials, but it just isn't clicking for me.

Torqumada

---

### Post by nothingspecial on 2010-10-16
Have you aiready reinstalled?

If not, when you get to the partitioning bit choose manual.

Select your /home partition, choose to "use it as" whatever file system it is, choose amount point of /home but DO NOT check/tick the format box.

If you have already installed, then you are going to have to edit /etc/fstab which I can help with if you wish.

---

### Post by nothingspecial on 2010-10-16
Reading again, I see you have already installed.

You will have to edit /etc/fstab

First, find the uid of /home
```

sudo blkid
```

Figure out which random collection of letters and numbers is the uid of your home partition.

Then edit /etc/fstab

```
gksudo gedit /etc/fstab
```

Add a line like this

[COLOR=blue]
[/COLOR]```
UUID=1302e997-0120-45c0-aa5b-84c5117ce410  /home  ext4  nodev,nosuid,relatime  0  2
```

Change the uid for the correct id and change ext4 to the correct file system. Everything else should be correct.

---

### Post by Torqumada286 on 2010-10-16
I haven't reinstalled yet, so I can use the first option during the installation process?

Torqumada

---

### Post by nothingspecial on 2010-10-16
During the partitioning bit, choose manual.

Select your / partition

Choose to use as an ext4 (or 3 if you like) journaling file system.

Choose a mount point of /

Check the format box.

Select your /home partition

Choose to use as an ext4 journaling file system (Or what ever it is - [COLOR=Red]If you choose a file system that it isn`t it will format it and you will loose your data so beware[/COLOR])

Select a mount point of /home

[SIZE=4][COLOR=Red]DO NOT[/COLOR][/SIZE] check/tick the format box.

Leave everything else alone

---

### Post by Torqumada286 on 2010-10-16
The mount point is just selecting the proper drive?  If I am putting the system files on a 500gb drive, that's my mount point?

Torqumada

---

### Post by nothingspecial on 2010-10-16
If your old drive is connected during the install process, the partitioner will see it and you will be able to select it as /home............

........... or do you want to copy it to the new drive first?

---

### Post by Torqumada286 on 2010-10-16
The drive that the home directory is currently on is a 300gb drive.  The one I want to install the system files to is 500gb.

Torqumada

---

### Post by nothingspecial on 2010-10-16
So, do you plan on keeping the 300g drive as your /home? If so, you will be able to select it during the install.

Have a go, if you are not happy, abort it and post back here.

Congratulations \\:D/ You are the recipient of my 4000th support post =D>

---

### Post by Torqumada286 on 2010-10-16
> **nothingspecial said:**
> So, do you plan on keeping the 300g drive as your /home? If so, you will be able to select it during the install.

Have a go, if you are not happy, abort it and post back here.

Congratulations \\:D/ You are the recipient of my 4000th support post =D>

I feel so honored.:P    I'm keeping the 300gb as the /home directory.  Thank you for the help.  I'll let you know what happens.

Torqumada

---

### Post by Torqumada286 on 2010-10-16
Hmmm didn't quite work.  I'm still having the same problem booting up as before.  I am guessing there is a setting in my /home directory that isn't playing nice with 10.10.  I get a blank screen with a ful boot, use recovery to get to the GUI and then get stuck in the log in loop, where it keeps asking for my password.  I guess I'll do another full install on the 500gb drive for both / and /home directories and go from there. At least my data is still safe on the 300gb drive.

Torqumada

---

### Post by nothingspecial on 2010-10-16
```
sudo chown -R username:username  /home/username
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 /home/username/.dmrc
```

---

### Post by Torqumada286 on 2010-10-16
What will that allow me to do?

Torqumada

---

### Post by nothingspecial on 2010-10-16
Sorry, 

It`s just that your /home may not have the correct permissions.

Restart and hold down the shift key.

When you get to the menu, choose root recovery shell (or whatever they call it atm)

Then issue those commands. You will not need the sudo.

---

### Post by Torqumada286 on 2010-10-16
I think I found part of the problem.  The boot is still seeing my upgrade install of 10.10 as the primary install of the system.  It's on the 300gb drive with the home directory, instead of the 500gb drive where I just did the install.  Let me see if I can fix that.

Torqumada

---

### Post by Torqumada286 on 2010-10-16
Well, it sort of worked. I can see and access my old home file, but it is a home file within a home file.  Is that how it's supposed to be?

Torqumada

---

