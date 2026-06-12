---
title: "Windows opening on startup"
date: 2010-09-30
forum: General Help
---

### Post by rmcellig on 2010-09-30
When I start up my machine and it gets to the desktop, windows automatically open for all of my external USB drives cluttering my desktop. How can I prevent this from happening. Before restarting my machine, there are no windows or applications running.

---

### Post by sanderd17 on 2010-10-01
maybe you can add them to your /etc/fstab file.

---

### Post by luvshines on 2010-10-01
Did you ever reboot the machine in that state ??

Maybe your previous session has been saved and it is being loaded.

---

### Post by rmcellig on 2010-10-01
No all windows and apps are closed before restarting. Why is this happening in the first place. I am beginning to think that there is something wrong with my installation of 10.04. I have it installed dual boot on my Mac.

---

### Post by luvshines on 2010-10-01
Have you checked the settings in  System->Preferences->Removable Drives and Media for automount and auto-open ?

---

### Post by rmcellig on 2010-10-01
I don't see that in my menu.

---

### Post by luvshines on 2010-10-01
Oh!! I just saw that it came in my PC by thunar-volume-manager

They have removed gnome-volume-manager from some previous releases and shifted most of the functionality to nautilus->edit->preferences->media itself

---

### Post by rmcellig on 2010-10-01
Should I install thunar-volume-manager?

---

### Post by uRock on 2010-10-01
Close everything that you do not want starting on startup, then go to System> Preferences> Startup Applications, then click the Options tab, then click the Remember Currently Running Application button.

---

### Post by rmcellig on 2010-10-01
That didn't work, when I restarted 12 nautilus windows from my my USB drives opened up. This is what I don't want am an not sure what is causing this.

---

### Post by kDDs on 2010-10-01
Can you post the contents of /etc/fstab?

Go to the terminal (Applications > Accessories > Terminal) and enter the following:

```

gedit /etc/fstab

```

Then copy and paste the lot here.

---

### Post by rmcellig on 2010-10-01
Here you go:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=2b1d3b2c-768b-45f3-a76d-2d956f974b67 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5682e182-295d-42bc-8330-f5a20e074337 none            swap    sw              0       0

---

### Post by luvshines on 2010-10-01
Did you check the settings in nautilus edit->preferences->media ?

---

### Post by rmcellig on 2010-10-01
Here you go.

---

### Post by luvshines on 2010-10-02
Maybe shooting in the dark, but have a look at the Automounting section and check your registry keys:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

