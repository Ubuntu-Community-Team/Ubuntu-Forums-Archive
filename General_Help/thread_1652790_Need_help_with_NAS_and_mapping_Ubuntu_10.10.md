---
title: "Need help with NAS and mapping Ubuntu 10.10"
date: 2010-12-25
forum: General Help
---

### Post by helipilotx on 2010-12-25
Hi Guys, I need some help. I am fairly new to ubuntu and there are a few things I do not understand.

I have Ubuntu 10.10 and a D-Link NAS. If I browse the network I can see, browse and access the NAS. The NAS has NO password protection.

Now here a few things which drive me slowly insane. 

1. After Every freaking reboot I have to re-mount the NAS again.

2. I am NOT able to make shortcuts to the desktop like in Windows from a from a folder from the NAS. If I click the folder and say "Make Link" I get the message >Error creating link to i.e. My Files< >The Target deos not support symbolic links< 
WTH ??? That should be a basic basic basic feature. 
A user should not need to dig around with codes and crab to make such a simple thing work. 

3. Let's say a I'm in GMail and like to send a mail with an attachment. Why To h... I am not able to attach a file from the NAS? I mounted it, can access it but when I click on attach file I can only see the system but the the NAS. Why?

If someone has a SIMPLE solution which I am teach to my clients please let me know. I really would appreciate it.

Thanks, Mike

---

### Post by Morbius1 on 2010-12-25
>  1. After Every freaking reboot I have to re-mount the NAS again.Gigolo - it's a utility - it's in synaptic
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Of course you could also Bookmark it in Nautilus - then it will show up in Nautilus in the tree just like a mapped drive does in Windows but you will have to click on it to mount it. Gigolo will mount it automatically. Gigolo can even wait for the NAS to be powered on before it tries to mount it.

>  3. Let's say a I'm in GMail and like to send a mail with an attachment.  Why To h... I am not able to attach a file from the NAS? I mounted it,  can access it but when I click on attach file I can only see the system  but the the NAS. Why?The developers of this thing decided to play a practical joke and made the mount point of the remote share a hidden directory:
> /home/your-user-name/.gvfs

---

### Post by Ceiber Boy on 2010-12-25
> **Morbius1 said:**
> Gigolo - it's a utility - it's in synaptic
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Of course you could also Bookmark it in Nautilus - then it will show up in Nautilus in the tree just like a mapped drive does in Windows but you will have to click on it to mount it. Gigolo will mount it automatically. Gigolo can even wait for the NAS to be powered on before it tries to mount it.

The developers of this thing decided to play a practical joke and made the mount point of the remote share a hidden directory:

Thankyou these things were driving me mAd also

---

