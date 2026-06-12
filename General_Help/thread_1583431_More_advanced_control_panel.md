---
title: "More advanced control panel?"
date: 2010-09-27
forum: General Help
---

### Post by helwitch on 2010-09-27
So I'd switched to OpenSuse around ubuntu 8.04, for a number of reasons. I thought I'd give (k)ubuntu another try, cos so much software gets released that's *ubuntu compatible these days, almost as much as is windows compatible. So far it's not bad, but I've got one gripe, that was one of the things that drove me away from kubuntu before.

All the advanced user graphical admin stuff is essentially hidden! In OpenSuse, you've got Yast2, which gives you absolutely all your admin stuff in one "control panel". Kubuntu used to have this, in kcontrol, but that's long since gone. Is there something like Yast2 for kubuntu?

As an example of something I could easily do in Yast2 and can't find an easily graphical way to do in kubuntu 10.04-I swapped out one of the hard drives in my system. Now every time I boot, the bootloader is looking for the now missing hard drive, and I have to tell it to skip it. I know I could manually edit the file, but I'd rather have a nice graphical config tool that lets me configure things. I can't seem to find such a thing anywhere in my kubuntu install tho.

Another example-there doesn't seem to be a gui partitioner installed. Yeah, I can just use parted from the command line, but like I said, I prefer a graphical interface. I installed partitonmanager, but still. A graphical partitioner seems like a pretty crucial thing to have in an OS. Maybe I just missed it someplace, but that comes back to my main point, which is that all the power user graphical stuff seems to be missing, or really well hidden; and it would be nice if all that stuff was in a single place.

So, can anyone suggest a control panel sort of app, that includes the sort of stuff Yast2 has on OpenSuse?

---

### Post by ankspo71 on 2010-09-28
Hi,
Are you referring to not being able graphically edit Grub2 or are you talking about a GUI to manage partition entries in fstab? or both? For the  editing of the fstab file, there is a package called 'pysdm'. It could be useful for someone who needs a GUI. As for Grub2, I use this link to install and update grub2. [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html) I know it's not even close a GUI editor, but I think it is easier than other online help that I have found. Edit: I gave you the link I use for specifically for Kubuntu Maverick Beta. Here is even an easier one for Grub2: [http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

If you are looking for distributions with control centers and/or more system tools included, you might want to consider trying out Mandriva One KDE, or PClinuxOS KDE. They can't use Ubuntu's growing number of packages though (they use RPMs as packages), but they do have all of the important things in their repos.

---

### Post by Old *ix Geek on 2010-09-28
> **helwitch said:**
> All the advanced user graphical admin stuff is essentially hidden! In OpenSuse, you've got Yast2, which gives you absolutely all your admin stuff in one "control panel". Kubuntu used to have this, in kcontrol, but that's long since gone. Is there something like Yast2 for kubuntu?I know absolutely nothing about Yast*, so I can't visualize what you're referring to. However, between "System Settings" and "System" and "Utilities," there's just about everything you need.
> there doesn't seem to be a gui partitioner installed.Sure there is:

Settings > System Settings > Advanced > Partition Manager

which allows you to "Manage disks, partitions and file systems."

Or you can install gParted which works fine in KDE, and/or you can use KDE Partition Manager, which you've already installed.

---

