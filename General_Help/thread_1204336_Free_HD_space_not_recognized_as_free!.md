---
title: "Free HD space not recognized as free!"
date: 2009-07-04
forum: General Help
---

### Post by bcn17 on 2009-07-04
I have a server that has been filling up. So I recently moved about 50GB of data to another computer. I then deleted the data from the server. If I ssh the server and type:

df -h

It tells me that Size=117G Used=109G Avail =2.4G

This is the same that the GUI says is available through the GUI.

I should have at least 50 G available. 

Now when I go to / and type sudo du sh *

it says that my /data folder has 54G total. This seems about right. But why is the other ~60G not showing up as free space. 

Oddly enough I do not have a ~/.Trash folder on my server. I typed 

sudo rm -rf ~/.Trash/* 

anyways though. 

It seams as if when I delete things through the GUI and sftp the files appear on my non-server Trash, which I deleted from their too. (although there is no file transfer time so its hard to believe they are actually transfered to my other computers trash)

Help me get my HD space back!

---

### Post by moster on 2009-07-04
In default Ubuntu 9.4 you have already installed little app in menu application > Accesories > Disk usage analyzer  He should tell you size of you particular folders so you can see what is eating your disk.

edit:
now, you discover that you have 50GB+ of PORN in "downloads" folder ;)

---

### Post by michy99 on 2009-07-04
If you deleted a lot of stuff as root, it may be in root's trash. To get rid of it:```
sudo rm -r /root/.local/share/Trash
```

---

### Post by bcn17 on 2009-07-04
Monster- that is a cool tool thanks

michy99 - for some reason I don't have a .local in my root - after you told me this I was pretty sure it would solve my problem, but no cigar.

I did fix the problem though! Reboot...

However, I have my server running different things and rebooting is not something I want to do when I want to clear up space. It shouldn't seam necessary... I wonder if there is some process I can use to recheck space like a:

/etc/init.d/"soemthing here" restart

But rebooting is at workable fix.

---

### Post by moster on 2009-07-04
When I read your post second time I relised you are running server. Well, I guess what I said is not possible. My mistake.

But maybe somebody else would find himself in my post :)

---

### Post by geirha on 2009-07-04
Try the following:
```
sudo du -mx --max-depth=1 / | sort -g
```

It will show the space (in mebibytes) the files and directories in / use, sorted in ascending order by disk usage. Replace / with the folder that uses the most to see what takes up space inside there. Repeat until you find the sinner.

---

