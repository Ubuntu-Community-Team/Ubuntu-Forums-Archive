---
title: "Creating an image of my system"
date: 2011-01-26
forum: General Help
---

### Post by Kivech on 2011-01-26
Hi all,

It's been a while since I used Ubuntu x64. In the past lots of hardware was not supported or did not work well, so I always ended up having to switch back to Windows just to have my system working properly.

Now however, it seems that everything is supported, including the on board RAID that I'm using, which is fundamental for me.

Now that I have my system the way I want it to, I would like to create some sort of image of my whole system, so that in the case of a HDD failure I can put everything back exactly the way I have it now.

I already have my /home on a seperate disk with a RAID 1 setup, as well as my backup directory. The system itself though, is running on a single disk, so it has to be backed up properly. Hence my question.

I also remember that there used to be ways to create a distribution disk out of the installed system that you have. Would that be an option for me as well?

Anyway, thanks in advance for any help and/or advice. Main thing for me is that I have my system and data secure in such a fashion that I can restore it all in as little time as possible if the need is there.

Kivech

---

### Post by Quarkrad on 2011-01-26
I'm a newbie so apologies for replying as I'm not exactly qualified.  However, I have asked this question and kept an eye on things. I found Clonezilla really good to copy/back up and restore but unfortunately for me, the showstopper was that the boot files are not honored.  So on a dual boot system if you restore the Ubuntu partition you suddenly lose visibility of the other OS. You then have to manually restore GRUB 2 to get the boot loader back which can be anything from very easy to 'tear your hair out'.  I am not aware of anything that can restore a specific partition but not touch the grub boot loader.

---

### Post by cipherboy_loc on 2011-01-26
*If* you just want to restore the files then either go with CloneZilla, or use a compression utility (I personally use mksquashfs because you can mount it and copy files off of it). If you go with mksquashfs then run the following off a Live CD, Live USB key, etc:

```

sudo apt-get install squashfs-tools
sudo mount -t foo /dev/bar0 /mnt
sudo mkdir /media/backups
sudo mount -t foo /dev/bar1 /media/backups
sudo mksquashfs /mnt/* /media/backups/current-backups.squashfs

```

The nice thing about squashfs images is that it preserves all the permissions, allowing you to do the following to restore:

```

sudo mount -t foo /dev/bar0 /mnt
sudo mount -t foo /dev/bar1 /media/backups
sudo mkdir /media/backups/mnt
sudo mount -o loop /media/backups/current-backups.squashfs /media/backups/mnt
sudo cp -prv /media/backups/mnt/* /mnt/

```

The key thing about the cp command that allows it to restore permissions is the arguments. -p for preserve, -r for recursive, and -v for verbose. This does not backup, nor restore GRUB, but it keeps all the grub (/boot/grub) files, such that you only need to restore the bootloader proper, not the configuration. 

There are better ways to run backups, but it works for me. 


As for another method, you could use dd to create a copy of your Ubuntu partition, but I don't know how to do that...

Cipherboy

---

### Post by ghostborg on 2011-01-26
Try putting this question to Robbie Ferguson's show Catergory5.tv
[http://www.category5.tv/]("http://www.category5.tv/")

From the web page menu select Interact and then "Ask a question"

The show is live on Tuesdays at 7pm est. double check that.
They have a topic but answer email and watch the chat room for questions.
During the show you can interact live with people all over in the chat room, people will offer there suggestions. Kinda neat.

---

