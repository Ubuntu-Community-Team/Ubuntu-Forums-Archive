---
title: "Moving Files to a PenDrive using the command line"
date: 2009-07-29
forum: General Help
---

### Post by frs89 on 2009-07-29
Hi
I have ubuntu 8.04, and I've messed up the system when I uninstalled some essencial programs accidently (I didn't know that it was possible to uninstall things that would make the system unstable afterwards..). Then I ran the system recovery and now I can start Ubuntu only in command line.

Is there any way to recover the graphic environment?

I'm thinking to install the new ubuntu, but I need to save some stuff to a pendrive first, how do I copy files to a pendrive using the comand prompt? 

Thanks

---

### Post by jerome1232 on 2009-07-29
This is just a guess but maybe removing then installing the virtual package ubuntu-desktop will reinstall the packages you removed.

```
sudo apt-get remove ubuntu-desktop; sudo apt-get install ubuntu-desktop
```

To move files to a usb drive you just have to mount it and transfer. The below assumes you only have one internal disc. You might need to adjust it.

```
sudo -i
mkdir /mnt/tmp; mount /dev/sdb1 /mnt/tmp
cp -r /folder/where/files/are /mnt/tmp
```

---

### Post by Chronon on 2009-07-29
> **jerome1232 said:**
> This is just a guess but maybe removing then installing the virtual package ubuntu-desktop will reinstall the packages you removed.

I don't think the OP will even need to remove.  I removed a couple of packages during removal of Enlightenment recently.  They turned out to also be dependencies of the Kubuntu-desktop and I was greeted at my next login with the message that my previous session was no longer valid.  

I found that the package kubuntu-desktop was no longer listed as installed, so I reinstalled it and it restored the particular, necessary packages that had been removed.

---

### Post by c0mput3r_n3rD on 2009-07-29
You will also probably need to install xinit.
```

sudo apt-get install xinit

```

---

