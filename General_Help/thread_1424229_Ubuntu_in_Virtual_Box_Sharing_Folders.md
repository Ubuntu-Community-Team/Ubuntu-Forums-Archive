---
title: "Ubuntu in Virtual Box Sharing Folders"
date: 2010-03-07
forum: General Help
---

### Post by Tomination on 2010-03-07
Hi guys, im a complete ubuntu novice, i used to dual boot between windows 7 and ubuntu 9.10 but windows kept moving the stuff from ubuntus drive and stopping it from booting :(

So i now installed Virtual box and ubuntu inside and WOW, i have ubuntu and Windows running together in seamless mode, its not even a box now, its more like a hybrid computer system!

Even though it looks just like its one OS i still cant move my files into or out of my virtual box, i dont understand any of the methods i found on the net using terminal i keep getting messages saying things like "must be root"

does anybody know how i can share my folders so i can access my windows files in ubuntu and vice versa?

Thanks! Tom

---

### Post by howefield on 2010-03-07
There are a few ways, but what have you done so far ?

Do you have guest additions installed ?

Here's a short video showing you how..

[http://showmedo.com/videotutorials/video?name=3650000&fromSeriesID=365](http://showmedo.com/videotutorials/video?name=3650000&fromSeriesID=365)

---

### Post by switch10 on 2010-03-07
Install Guest additions.  I believe its under devices in VirtualBox while it is running.

---

### Post by Tomination on 2010-03-07
yeah i installed guest additions thing, i have tried to share a folder from windows and called it "Transfers" but i dont understand what to do in ubuntu, people keep using these terminal things and they dont work for me.

i tried those videos this morning but they answer my question backwards unfortunately. ubuntu is my guest, windows 7 is my computers main operating system

---

### Post by switch10 on 2010-03-07
Yes, Ive only had to do this backwards as well. 

If you go to Places>Network, is there a guest additions folder?

---

### Post by Tomination on 2010-03-07
nope i just have "Windows Network" and when i try to open it i am told i cannot mount it :(

---

### Post by switch10 on 2010-03-07
This tells you how to do it.  [http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/](http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/)

You have to actually make a mount point and mount the shared folder.  I don't know how you are going to do this without a terminal.  Luckily, these instructions a very easy to follow.  and its only 2 steps.  I think you can figure them out.

---

### Post by Tomination on 2010-03-07
Hi, thanks for your reply again :)

i did this earlier but wasnt sure if it had worked or not, i created the mouse point and i didnt get an error, so i did the next line using /media/windows-share

i didnt get an error again, but if i go to Computer / Media / 

there isnt a folder called windows share there

am i being stupid? or did it not work?

PS: My terminal works fine, just the stuff i put in them always gave me an error :)

---

### Post by dcstar on 2010-03-07
> **Tomination said:**
> 
........
does anybody know how i can share my folders so i can access my windows files in ubuntu and vice versa?


If you go to the Virtualization forum all of this is covered in the threads at the top of the forum.

---

### Post by switch10 on 2010-03-07
Did you install Guest Additions as root?  Apparently you need to, in order for this to work.

---

### Post by Tomination on 2010-03-07
> **switch10 said:**
> Did you install Guest Additions as root?  Apparently you need to, in order for this to work.

I cant seem to do anything with guest additions now, im assuming i installed it right cos now my mouse doesn't have to be captured, my clipboard syncs and i can run in fullscreen mode. But when i try to use the guest additions setup again everything gives me errors like "you cant use this archive"

I will have to share my files over my website using FileZilla as i have spent all day doing this and got nowhere :(

Thanks for your help regardless. It is almost a shame because if Ubuntu could use itunes, paint.net and a few other programs it would be so much better than Windows

---

