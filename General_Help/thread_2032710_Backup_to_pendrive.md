---
title: "Backup to pendrive"
date: 2012-07-24
forum: General Help
---

### Post by rekhyt73 on 2012-07-24
Hi, 
    Can anyone help me with creating a backup of a particular folder in my Ubuntu 12.04 system to an external hard-disk/pendrive using terminal commands.

   The fact is there is something wrong with my Ubuntu and it keeps starting in low graphics mode. So I am only able to use the terminal and nothing else.I need to create a backup of an important file before I get the system formatted, if needed.

Thanks for any help! Greatly appreciated.

---

### Post by Habitual on 2012-07-24
What directory do you wish backed up?

Stick your usb/removable media in, let it mount and  then open a terminal >
```
df -h
``` output here please.

But basically, the method I suggest is rsync in the following manner
```
rsync -avz /path/to/source /path/to/destination/
```Here's a nugget from my own rysnc script backing up my /home/jj directory to "Keepers", a 3T WD USB drive.

```
cd "$HOME" && rsync -avz . /media/Keepers --exclude ".cache/" --exclude "VirtualBox VMs/"
```NOTE: The above excluded the "VirtualBox VMs" directory. Omit it if you don't have any Vbox VMs to back up.

Hope That Helps.

---

### Post by rekhyt73 on 2012-07-24
Hi
I inserted the pendrive and let it mount. Then I typed df -h, and a list was displayed.

1. What do I do after that? 
2.I dont see any option indicating the external drive. (no sdb or 4GB option)
3. I tried /dev/sda5, but permission was denied, even as a root.

---

