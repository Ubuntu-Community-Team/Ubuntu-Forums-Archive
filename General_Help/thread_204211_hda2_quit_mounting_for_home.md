---
title: "hda2 quit mounting for /home"
date: 2006-06-26
forum: General Help
---

### Post by primlantah on 2006-06-26
I was using sbackup this morning(to make a backup...not restore one).  shortly after the backup started everything gui started quiting unexpectedly.  I restarted my system and hda2(which was being used as /home) isnt mounted.  I booted up into the live desktop and can access all partitions fine.  What file do i need to edit to get hda2 back /home?  

incase it makes a difference im running Ubuntu6.06 kernel 2.6.15-25-386 on hda1.

---

### Post by aysiu on 2006-06-26
You need to edit the /etc/fstab file. Assuming you've mounted your system partition at /recovery in the live CD... ```
sudo cp /recovery/etc/fstab /recovery/etc/fstab_backup
sudo nano /etc/fstab
``` Make sure this line is in there: ```
/dev/hda2 /home ext3 nodev,nosuid 0 2
``` Save (Control-X), confirm (Y), and exit (Enter).

---

### Post by primlantah on 2006-06-26
oh....ok thanks.  I thought it was something like that but i wasnt positive if i should be messing with fstab.

---

### Post by primlantah on 2006-06-26
this is how fstab looks with the system broken

/dev/hda2       /home           ext3    defaults        0       2

could you explain the difference between this and what you are suggesting please?

---

### Post by mlind on 2006-06-26
[QUOTE=primlantah]this is how fstab looks with the system broken

/dev/hda2       /home           ext3    defaults        0       2

could you explain the difference between this and what you are suggesting please?[/QUOTE]

My mount for /home on /etc/fstab is exactly the same, so that should work alright.

Mount manual explains the other parameters for ext3 filesystem
```

man mount

```

---

### Post by primlantah on 2006-06-26
[QUOTE=mlind]My mount for /home on /etc/fstab is exactly the same, so that should work alright.
[/QUOTE]

it dosent seem to work.  anyone have anythoughts about what could be happening?
When the system boots it takes me to the terminal login instead of the gui thatused to come up.  it wont let me log in because it says it cannot find /home/username.  I checked hda2 and everything is as it should be.  are there any error logs or anything i could check to find out more information about what went wrong?

---

### Post by mlind on 2006-06-26
[QUOTE=primlantah]it dosent seem to work.  anyone have anythoughts about what could be happening?
When the system boots it takes me to the terminal login instead of the gui thatused to come up.  it wont let me log in because it says it cannot find /home/username.  I checked hda2 and everything is as it should be.  are there any error logs or anything i could check to find out more information about what went wrong?[/QUOTE]

dmesg or /var/log/messages should contain something about the problem.

edit your /boot/grub/menu.lst and disable splash booting
```

# defoptions=nosplash

```

and see what happens when /home filesystem is being mount at boottime

---

