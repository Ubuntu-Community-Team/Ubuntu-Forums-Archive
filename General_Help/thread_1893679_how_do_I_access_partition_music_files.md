---
title: "how do I access partition music files?"
date: 2011-12-10
forum: General Help
---

### Post by dlosey555 on 2011-12-10
My computer crashed and now it's fine.  I have windows 7 on one part and i just installed ubuntu yesterday.  My goal was to acces thousands of music files that i dont have anymore. My hard drive says its like 104 gb used up out of 230 gb but i cant find the files anywhere.  I was able to see my partitions from a command in the "run" program thing and i found one which was around 53 gb so i assume thats all my music and photos but i dont know how to access it . 

im not too computer savvy either. so if you can "dumb down" any answers it would be great!

thanks so much!!!:)

---

### Post by papibe on 2011-12-10
Regardless of efforts to recover the ability to boot again, you can access all partitions and files using an Ubuntu Live CD.

Boot your PC as you were to install Ubuntu using the CD or the USB stick, but instead of install, select 'Try Ubuntu'.

Note that the live CD is not the Wubi install but ISO version that you have to burn into a CD, or install on a USB stick.

Hope that helps.
Regards.

---

### Post by gennatolls on 2011-12-10
A good program to view your partitions would be Disk Utility which is installed by default. Just pull it up in the Dashboard, click on your drive and you can view your partitions on that drive. I'm guessing you had your music on windows 7 partition since you just set up ubuntu yesterday. You can mount your windows partition in Nautilus (the file browser with a Home Folder icon in the launcher) by clicking on it in the side window and choose your folder where the music is located. This all assuming the "crash" didn't do anything catastrophic to your files. Good luck and welcome to Ubuntu

---

### Post by dlosey555 on 2011-12-10
> **gennatolls said:**
> A good program to view your partitions would be Disk Utility which is installed by default. Just pull it up in the Dashboard, click on your drive and you can view your partitions on that drive. I'm guessing you had your music on windows 7 partition since you just set up ubuntu yesterday. You can mount your windows partition in Nautilus (the file browser with a Home Folder icon in the launcher) by clicking on it in the side window and choose your folder where the music is located. This all assuming the "crash" didn't do anything catastrophic to your files. Good luck and welcome to Ubuntu

i found the partitions folder but it says but i dont know what im exactly looking for. and i cannot find the Nautilus thing either

---

### Post by gennatolls on 2011-12-10
Ok I'm assuming you are running Ubuntu 11.10.

Press the Dash button on the top left of the screen (It is a grey and white ubuntu symbol). In the search bar type "Nautilus", it will pull up a "Files" and "Home" Icon. Click either one. The window that opens up is the Nautilus File browser. You will then see a "Devices section in the top left of the nautilus window" Assuming you are dual booting only windows and ubuntu, there will be xxGb Filesystem (where xx is the size of your windows partition) and a System Reserved partition. Choose the filesystem partition and navigate to /Users/Your-username/Music and your music will be there.

---

### Post by dlosey555 on 2011-12-10
> **gennatolls said:**
> Ok I'm assuming you are running Ubuntu 11.10.

Press the Dash button on the top left of the screen (It is a grey and white ubuntu symbol). In the search bar type "Nautilus", it will pull up a "Files" and "Home" Icon. Click either one. The window that opens up is the Nautilus File browser. You will then see a "Devices section in the top left of the nautilus window" Assuming you are dual booting only windows and ubuntu, there will be xxGb Filesystem (where xx is the size of your windows partition) and a System Reserved partition. Choose the filesystem partition and navigate to /Users/Your-username/Music and your music will be there.


i got to that part but all it says is "TI102763W0F" , thats all it says under "devices''. where else would it be?

thanks

---

### Post by gennatolls on 2011-12-10
Try that one. Where was your music originally located?

---

### Post by dlosey555 on 2011-12-10
i did.  it was originally located on my windows 7 part and under my itunes music.  i looked there and it doesnt have any of the music on my old itunes. I think it may have come from doing a windows update because i always put those off but finally did it and my computer kinda crashed. so my friend put a version of windows 7 on this and it works not its just none of my files are accessable but it says there is still lots of room used up on my hard drive.

---

### Post by gennatolls on 2011-12-10
Can you still play your music when booted into Windows 7? Also Apple digital media has DRM meaning you can only play it in a registered copy of iTunes, so if you bought all your music through iTunes you won't be able to play it in Ubuntu. The ubuntu Music store in Banshee is a very good place to purchase music. It has no restrictions on it so you can burn it to a million cd's as well as play it on as many computers as you want, not the five Apple allows.

---

### Post by dlosey555 on 2011-12-10
no i download all my music.  and i cant access it in windows 7 either.  i think its partitioned off somewhere but i dont want to format my hard drive because i see its still on there somewhere and i want to try and save it if i can.

---

### Post by nothingspecial on 2011-12-10
Open a terminal and post the output of

```
sudo fdisk -l
```

and 

```
mount
```

---

### Post by Ms. Daisy on 2011-12-10
> **dlosey555 said:**
> i did.  it was originally located on my windows 7 part and under my itunes music.  i looked there and it doesnt have any of the music on my old itunes. I think it may have come from doing a windows update because i always put those off but finally did it and my computer kinda crashed. so my friend put a version of windows 7 on this and it works not its just none of my files are accessable but it says there is still lots of room used up on my hard drive.
I'm not clear on this.  Did your friend reinstall/recover Windows 7 on your computer?  And subsequently you installed Ubuntu alongside Windows 7?  You can't access the music from any partition, right?  If that's the case then I would suspect that you overwrote the itunes music.

If you've got the music on an mp3 player(s) or CDs, then you can always recover the music back on to your computer from those sources.  If you google youtube videos, you can find a tutorial showing how to recover music from your mp3 player.  And I assume that you didn't back up itunes ever, right?

---

