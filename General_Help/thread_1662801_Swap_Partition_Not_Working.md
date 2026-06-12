---
title: "Swap Partition Not Working ?"
date: 2011-01-08
forum: General Help
---

### Post by West201 on 2011-01-08
[B]How do fix my Swap Partition ? Last night I added unused space to the main Ubuntu partition. Now I noticed the Swap Partition is always at 0 bytes.
[/B]

I'm using a Sony Laptop, and have enclosed two screenshots. One of the Disk Utility and a system monitor.

Thanks :)

---

### Post by Verbeck on 2011-01-08
could you open a couple of youtube videos, openoffice, a movie and any other resource hogging app you could think of and run* free -m* from a terminal and post the out put here

---

### Post by West201 on 2011-01-08
> **Verbeck said:**
> could you open a couple of youtube videos, openoffice, a movie and any other resource hogging app you could think of and run* free -m* from a terminal and post the out put here

This is the output after having a ton of videos and apps running

---

### Post by drs305 on 2011-01-08
run this command and see if the UUID's all are identical:
```
sudo blkid -c /dev/null | grep swap && cat /etc/initramfs-tools/conf.d/resume && grep swap /etc/fstab
```

The commands return the UUID values reported by various system files that work with the swap function. They should match the first output if they disagree.

---

### Post by West201 on 2011-01-08
> **drs305 said:**
> run this command and see if the UUID's all are identical:
```
sudo blkid -c /dev/null | grep swap && cat /etc/initramfs-tools/conf.d/resume && grep swap /etc/fstab
```

The commands return the UUID values reported by various system files that work with the swap function. They should match the first output if they disagree.

This is what it displays after the command

---

### Post by drs305 on 2011-01-08
Since they don't match, you need to change your RESUME and fstab settings:

I can't capture the UUID from the thumbnail, but in the first command and in fstab change the xxxxx.. or UUID to the one that starts with [I][COLOR="Red"]8fbd...[/COLOR]
[/I]```

sudo swapoff
echo "RESUME=UUID=[COLOR="Red"]xxxxxxxxxxx[/COLOR]" | sudo tee  /etc/initramfs-tools/conf.d/resume
gksudo gedit /etc/fstab  # Open fstab to change the UUID of swap to the same value.
sudo update-initramfs -uk all  
sudo swapon -a    # Restore swap with new fstab settings
free -m   # Check swap
```

---

### Post by West201 on 2011-01-08
> **drs305 said:**
> Since they don't match, you need to change your RESUME and fstab settings:

I can't capture the UUID from the thumbnail, but in the first command and in fstab change the xxxxx.. or UUID to the one that starts with [I][COLOR=Red]8fbd...[/COLOR]
[/I]```

sudo swapoff
echo "RESUME=UUID=[COLOR=Red]xxxxxxxxxxx[/COLOR]" | sudo tee  /etc/initramfs-tools/conf.d/resume
gksudo gedit /etc/fstab  # Open fstab to change the UUID of swap to the same value.
sudo update-initramfs -uk all  
sudo swapon -a    # Restore swap with new fstab settings
free -m   # Check swap
```

I just changed the UUID, but the swap is still inactive. This is the new output I get after typing the command again. Thanks for you efforts to help BTW :)

---

### Post by drs305 on 2011-01-08
The swap line in /etc/fstab doesn't appear to have changed.

```
gksu gedit /etc/fstab
```

It should look like this, but with the correct UUID:
> # swap was on /dev/sda6 during installation
UUID=<uuid starting with 8fbd...>  none   swap    sw    0   0

Example, **but with wrong UUID**:
> # swap was on /dev/sda5 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none   swap    sw   0   0
Save the /etc/fstab file, then

Turn swap off and back on:
```
sudo swapoff -a && sudo swapon -a
```

Added: "free -m" may still show all zero's until you reboot and/or are using a lot of memory.

---

### Post by West201 on 2011-01-08
> **drs305 said:**
> The swap line in /etc/fstab doesn't appear to have changed.

```
gksu gedit /etc/fstab
```

It should look like this, but with the correct UUID:


Example, **but with wrong UUID**:

Save the /etc/fstab file, then

Turn swap off and back on:
```
sudo swapoff -a && sudo swapon -a
```

Added: "free -m" may still show all zero's until you reboot and/or are using a lot of memory.

This the output after running 4 videos, limewire, vlc, & openoffice.

Along with the updated UUI. Thanks Again !

---

### Post by drs305 on 2011-01-08
Edit: I misread your post. It is already working, it's just not needed yet.

Original:
I'd suggest running 
```
sudo update-initramfs -uk all  
```
once more and rebooting to see if that kicks it into operation. Other than that, I'll have to leave to others for further suggestions.

---

### Post by West201 on 2011-01-08
> **drs305 said:**
> Edit: I misread your post. It is already working, it's just not needed yet.

Original:
I'd suggest running 
```
sudo update-initramfs -uk all  
```once more and rebooting to see if that kicks it into operation. Other than that, I'll have to leave to others for further suggestions.

Problem solved then. :)

Thanks for your help.. Really appreciated it :).

---

