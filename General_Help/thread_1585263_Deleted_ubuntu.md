---
title: "Deleted ubuntu"
date: 2010-09-30
forum: General Help
---

### Post by onetwothreecool on 2010-09-30
I accidently deleted the 'Ubuntu' folder that was viewable from windows. I did a permanent delete. Now, I am unable to boot ubuntu. It prompts me to a black screen and shows a list of possible commands available like ls lsmod help boot etc. I have data in ubuntu that are very important. What do i do?

---

### Post by drs305 on 2010-09-30
The Windows bootloader and boot.ini still contains a reference to Ubuntu, which is why you still see it in the menu. By deleting the ubuntu folder, you deleted the root.disk file which 'contained' all your Ubuntu folders in a Windows file.

As far as recovery, if there is an opportunity to recover a folder that is 'permanently' deleted you will have to do so from within Windows. I no longer know much about Windows so I can't help you recover them. 

Others on this forum may be able to help you, and you can go to a Windows forum as well, since what you need to do is recover a deleted Windows folder. It really is independent of Ubuntu.

If you find you can't recover the file and want to remove the Ubuntu menu item, go to Add/Remove programs and uninstall 'Ubuntu'.

Best of luck.

---

### Post by dnguyen1963 on 2010-09-30
> **onetwothreecool said:**
> I accidently deleted the 'Ubuntu' folder that was viewable from windows. I did a permanent delete. Now, I am unable to boot ubuntu. It prompts me to a black screen and shows a list of possible commands available like ls lsmod help boot etc. I have data in ubuntu that are very important. What do i do?

Since you deleted your Ubuntu folder from Windows you might be in luck.  There are some software that would allow you to undelete a file or folder.  Try this one...
[http://www.winundelete.com/?rid=google&kid=wu0401](http://www.winundelete.com/?rid=google&kid=wu0401)

Good luck.

---

### Post by sidzen on 2010-09-30
Start here
[http://en.wikipedia.org/wiki/Undeletion](http://en.wikipedia.org/wiki/Undeletion)

---

### Post by onetwothreecool on 2010-09-30
what i actually did was delete it when i was working in ubuntu. Not while using the windows os

---

### Post by dnguyen1963 on 2010-09-30
> **onetwothreecool said:**
> what i actually did was delete it when i was working in ubuntu. Not while using the windows os

I was going to ask you how you get Windows to see Linux folders let alone deleting it.  I do not know how to recover deleted files in Linux.  Hopefully, someone else can help you out.

---

### Post by drs305 on 2010-09-30
I'm not sure what folder you deleted from inside Ubuntu. If the /ubuntu/disks/root.disk file still exists in Wubi you may be able to mount it from the LiveCD to view or save the contents.

From a LiveCD, mount the Windows partition (assuming Windows is on sda1):

```

sudo mkdir /mnt/windows && sudo mount /dev/sda1 /mnt/windows
sudo mkdir /mnt/wubi && sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi

```

Then open a browser to inspect the contents:
```
nautilus /mnt/wubi
```

---

### Post by onetwothreecool on 2010-09-30
I remember now. There is a folder that contains these Wubi etc right? Now, when i view from windows, I do not find this one. When i viewed this from ubuntu, i thought it was an image that i had saved, i did not know it would be the actual working one.

---

### Post by drs305 on 2010-09-30
> **onetwothreecool said:**
> I remember now. There is a folder that contains these Wubi etc right? Now, when i view from windows, I do not find this one. When i viewed this from ubuntu, i thought it was an image that i had saved, i did not know it would be the actual working one.

The Windows folder for the Wubi install is /ubuntu

The file with your Ubuntu data in it, such as your HOME folder, is contained in the Windows file /ubuntu/disks/root.disk

You can mount the root.disk with the procedures I mentioned earlier, but if you deleted the /ubuntu folder you deleted the root.disk file as well and will need to use Windows deletion recovery methods to (hopefully) restore it.

---

### Post by onetwothreecool on 2010-09-30
I will definitely try what you said. But should i use any software for recovery in Windows? and will it work since i wasn't using Windows OS when i deleted it..

---

### Post by drs305 on 2010-09-30
> **onetwothreecool said:**
> I will definitely try what you said. But should i use any software for recovery in Windows? and will it work since i wasn't using Windows OS when i deleted it..

You have a point. You deleted the folder within Ubuntu but now can't get to that Ubuntu OS since it's been deleted. A vicious circle! I'm going to install the latest version of Wubi, try to delete the same folder, and see if I can come up with something.

Wherever you can find it, the file you really want to locate (in Trash, the original ubuntu/disks folder, etc) is *root.disk*. If you can find this file, we might at least be able to recover any data files you need.

---

### Post by drs305 on 2010-09-30
In my experimenting, I need to know how you 'permanently' deleted the Ubuntu folder.

Was the folder name 'ubuntu'? 
Had you mounted your Windows partition to see it?
If not, how were you accessing the folder you deleted? When I run Wubi by default I see only the normal Ubuntu folders. 

How did you delete it? (DEL, SHIFT-DEL, rm command)

And while I'm testing things, in Windows I would recommend you do a search of your computer for "root.disk" to see if it exists anywhere on your system.

---

### Post by bcbc on 2010-09-30
Try /host/ubuntu

---

