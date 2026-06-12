---
title: "Ubuntu won't start up! Nooooo!"
date: 2011-02-01
forum: General Help
---

### Post by picapacapopo on 2011-02-01
So about a month ago I got Windows 7. I installed it clean on harddrive. After that I installed Ubuntu with Wubi. I have a 64 bit machine, but I'm not sure if Ubuntu is 64 bit. I'm not sure if it's 10.04 or 10.10. 

Anyways, just a few minutes ago I had an update in my update manager. I remember it was about 79 megabytes. I updated it, and it said it needed a restart to complete. I was like whatever, I'll restart later. I did the required restart, and choose the Ubuntu option at GRUB or whatever. (Win7 or Ubuntu screen..) 

I left to go get some apples.

I came back and it was in Windows 7 so I was like MAN WTF! Haha. I restarted and choose Ubuntu and watched what happened. A few seconds after choosing Ubuntu my computer restarts. I tried it a few times and that always happens, so basically my only option is Windows 7. 

What should I do in this case scenario?


Thanks guys,
Alex

---

### Post by bcbc on 2011-02-02
See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") problem #2 solution #1. After getting it booting apply the permanent fix.

---

### Post by picapacapopo on 2011-02-02
Thanks for the reply dude, but I don't know what that stuff means? 

Thanks,
Alex

---

### Post by bcbc on 2011-02-02
This is a link to an Explorer like utility for Windows that gives you read-only access to your data stored on Ubuntu: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Download, run it, and point it at the file C:\ubuntu\disks\root.disk and then recover your important data. Then reinstall Ubuntu, but this time go into Synaptic (System, Administration, Synaptic) and select package grub-pc, then click on menu Package, Lock Version. Do the same for grub-common.

If you have spent a lot of time customizing Ubuntu and don't want to reinstall (because everything unsaved will be deleted) then you need to get an Ubuntu CD you can boot from in what's called Live CD mode (Try without installing). Then you can edit the bad file and get it booting that way - the Wubi Megathread explains it all - I know it's long and involved but I believe it's quite clearly written. 

Or of course you could install to partition, not using Wubi.

Up to you which way to go.

---

### Post by Rubi1200 on 2011-02-02
picapacapopo,
if there is something in particular you do not understand or a command that is not working for you, let us know so we can try and walk you through it.

---

