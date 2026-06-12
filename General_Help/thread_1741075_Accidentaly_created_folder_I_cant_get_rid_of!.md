---
title: "Accidentaly created folder I cant get rid of!"
date: 2011-04-27
forum: General Help
---

### Post by indirestraits on 2011-04-27
Hey guys!

Been fooling around a bit with Deluge the past days without noticing I ended up having the program running twice at the same time. 
I'm guessing its due to that I started a new download without my hdd being fully mounted, have no idea why the program 
won't reach my hdd after a restart if I dont move in to that hdd... anyways.

Somehow I've managed to create a folder: index/media/DOWNLOADS

[http://img42.imageshack.us/i/screenshot3hf.png/](http://img42.imageshack.us/i/screenshot3hf.png/)

Where some stuff I DL'd happened to end up. My problem is that I cant remove it and I havent the slightest idea why.

Please help a fella out! :)

---

### Post by ppv on 2011-04-27
What does it say when you try to remove the folder.

In a terminal enter "rm -rf /path/to/the/folder" without the quotes and hit enter. This command will remove the folder so ensure that you have copied everything from the folder that you require. Also ensure the path and filename before giving the command.

---

### Post by WorMzy on 2011-04-27
You can't remove the folder because you don't have write privileges to it's parent directory (/media). You can remove it with

```
sudo rm -r /media/Downloads
```

However, make sure that this is definitely the folder that you want to remove; **the folder and all it's contents will be removed**. Copy any of the files you want to keep from the folder to another folder before running the command.

---

### Post by indirestraits on 2011-04-27
Great guys, thanks a bundle, worked out :D

So now, would you happen to know why I have to move into my hdd before deluge chooses to write to it after a restart?

And why did I end up with a folder there and how come I could'nt remove it without sudo-in' eh?

---

### Post by WorMzy on 2011-04-27
Have you ever set the Downloads partitions to automount at boot time? If so, you would have needed to create the /media/DOWNLOADS folder for it to work. Since then, it seems that you've removed the automount (either purposely, or accidentally), but failed to remove the /media/DOWNLOADS folder. Now you have to "move into" the partition to make Ubuntu mount it, but since there's already a folder called DOWNLOADS in /media, it mounts the partition to /media/DOWNLOADS_ instead.

You'll need to re-setup the automount if you don't want to "move into" the partition every time you want to use Deluge. :)

Edit fstab if that's what you want to do.

```
gksu gedit /etc/fstab
```

---

