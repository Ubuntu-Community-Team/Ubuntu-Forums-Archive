---
title: "Media"
date: 2009-10-19
forum: General Help
---

### Post by PcBoyGeorge on 2009-10-19
So what is the best music player for ubuntu just to play like mp3 files.

And how do I make my other hard drives appear. Like I have music on a different partition of my hard drive and when I go to file and find file it only shows the linux part and desktop. Will not let me choose to browse the other drives for my music. I can get to it by going through but I want to by doing it in the problem. Any help?

---

### Post by ram2500 on 2009-10-19
In my opinion, Noatun is great once you get it configured, but it's much a headache. Rhythmbox comes by default, but I like Amarok as well. 

About accessing a NTFS partition, it can be done simply by going to terminal and entering as follows: sudo mount /media/devicename. Even easier is adding the Disk Mounter tool to your panel and your disks should appear. Click on the corresponding disk and choose "Mount". 

I am assuming that it is an NTFS (Windows) partition, but it will work with native ext partitions (of course) as well as FAT as well.

What media player are you using? You usually have a "Places" pane on the side with your home folder, desktop folder, etc as well as the mounted drives when you go to Open File dialogs in most programs...it has to be mounted to appear on the pane. If not, it would be easier to copy the folder over to your Linux partition and open it within the partition, as your particular application probably doesn't have this feature.

---

### Post by PcBoyGeorge on 2009-10-19
VLC. The drive is mounted. And it appears if i do open directory but I want it to when I do open file

---

### Post by ram2500 on 2009-10-19
Some programs may not have all drives available in the side pane, if it has one at all. I am not familiar with VLC, but if there is a side pane, it may or may not have these options available. If it is critical to add a folder to the media player, perhaps you can create a shortcut on your desktop from your music folder on the other partition and link from there, or copy it over.

---

