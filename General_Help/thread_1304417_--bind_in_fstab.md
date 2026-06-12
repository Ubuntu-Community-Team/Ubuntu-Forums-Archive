---
title: "--bind in fstab"
date: 2009-10-29
forum: General Help
---

### Post by erikbjohn on 2009-10-29
I am trying to use mount --bind on an external usb drive (Terraone).  
When Ubuntu boots, it mounts this in 
```
/media/Terraone
```I can then use
```
mount --bind /media/Terraone /home/myhome/Terraone
```to create a mount. 
This works great.  However, I do not want to do this every time I log in, so I tried to edit the /etc/fstab with
```
/media/Terraone   /home/myhome/Terraone   none bind 0 0 
```But this does not work.  I think that somehow Terraone is not mounted by Ubuntu before I am attempting this bind. 

 Any suggestions?
 (I am not using ln for reasons that are not relevant)

Thanks

---

### Post by Giblet5 on 2009-10-29
If the drive automounts as /media/Terraone, then do this:

```
sudo unmount /media/Terraone
sudo mkdir /media/Terraone
sudo chmod 775 /media/Terraone
sudo chown $LOGNAME:$LOGNAME /media/Terraone
sudo ln -s /media/Terraone $HOME/Terraone
```

Now, unplug the drive, wait 5, plug it back in.

Ta da!

---

### Post by erikbjohn on 2009-10-29
I understand that I can use ln - and the drive is mounting fine.  However, I want to leave the drive plugged in and bind it to my home directory on boot.

---

### Post by Giblet5 on 2009-10-29
> **erikbjohn said:**
> I understand that I can use ln - and the drive is mounting fine.  However, I want to leave the drive plugged in and bind it to my home directory on boot.

My example achieves the same goal, but if you prefer 'mount -o bind', why not put it in /etc/rc2.d/S99rc.local?

That's where last-minute execution is supposed to occur and everything will be mounted by then.

```
mount -o bind /media/Terraone /home/YourHomeDir/Terraone > /dev/null 2>&1
```

in the "dostart" function should work well.

---

### Post by QLee on 2009-10-29
erikbjohn,
This would be a good time for you to review the manual page for fstab. It will show you the options and format for the various fields in fstab. Asking you to read this yourself makes more sense to me than trying to explain it all in a post.

"man fstab" in a terminal will give you info. Post any questions that come up for you in your reading.

I'm not sure why you want to "bind" (make it appear in two locations) instead of just mounting the partition where you want it to be.

---

### Post by Giblet5 on 2009-10-29
> **QLee said:**
> erikbjohn,
This would be a good time for you to review the manual page for fstab. It will show you the options and format for the various fields in fstab. Asking you to read this yourself makes more sense to me than trying to explain it all in a post.

"man fstab" in a terminal will give you info. Post any questions that come up for you in your reading.

I'm not sure why you want to "bind" (make it appear in two locations) instead of just mounting the partition where you want it to be.

+1

Just a guess: he's enamored with mount's "-o bind" functionality. I'm not EVEN going to mention mhddfs...

---

### Post by erikbjohn on 2009-10-29
Thanks for directing me to the manual.  

I am enamored of bind because it enables me to remotely read via ssh my media partition on my macbook.  Using ln-sf does not do this and I hate to play with the automount settings that seem to be reading my external drive well.  But really, thanks for the sarcasm.

---

### Post by QLee on 2009-10-29
[QUOTE=erikbjohn]Thanks for directing me to the manual.[/QUOTE]  

Sure, since you didn't post any questions about fstab mounting I assume you figured out why what you were trying didn't work.

[QUOTE=erikbjohn]I am enamored of bind because it enables me to remotely read via ssh my media partition on my macbook.  Using ln-sf does not do this and I hate to play with the automount settings that seem to be reading my external drive well.  But really, thanks for the sarcasm.[/QUOTE]

Well, you got no sarcasm from me, and I still don't understand why you wouldn't just remount that drive in the filesystem in your home where you want it to be. How does that preclude being able to access it remotely from your macbook or how does having it a bind mount (two locations) help with that? Note: I said nothing about links, I read your first post which stated that you don't want a link.

Perhaps you should reply to posters individually to make things less confusing.

---

### Post by victorhugo289 on 2011-02-13
I think the OP's questions were quite sincere and straight forward.
I have the same problem and I want to automount in Fstab using 'mount --bind'.
My system is pretty much a mess since I have Windows98 and Windows XP with files on one partition, programs on other, music, stuff. I managed to automount the partition on start up but I have to navigate to the folders and it's a little inconvenient. 
I really think the OP's question and the way he formulated the question was really well done and could totally relate to what he wants to do, I would appreciate any help about this thing.

----------------UPDATE, UPDATE, UPDATE:
I found a little solution to this problem, instead of using Fstab I'm using scripts!
I created a script with the following lines:
```

#!/bin/sh
mount --bind "FOLDER TO MOUNT" "DESTINATION"

```then I followed this steps:
```

**Re: run script on boot up?**             
To run your script on startup do as follow :
1- create a file under init.d : sudo gedit /etc/init.d/my_script
2- put your command lines/script in the file & save it
3- make the file executable : sudo chmod +x /etc/init.d/my_script
4- make it run on boot : sudo update-rc.d my_script defaults

That's all

```That's right, that's all! It works great.

---

