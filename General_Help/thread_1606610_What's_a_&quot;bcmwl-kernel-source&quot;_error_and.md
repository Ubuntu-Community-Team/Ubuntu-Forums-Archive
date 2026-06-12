---
title: "What's a &quot;bcmwl-kernel-source&quot; error and how to I fix it?"
date: 2010-10-26
forum: General Help
---

### Post by Ulysses1994XF04 on 2010-10-26
When I first got ubuntu, I had problem installing some programs on it; installation of a download would stop midway and the black box would come up and say "encountered error in bcmwl-kernel-source" or something like that. The same thing happens when I try to install updates.

Now I NEED to install GAIM on my ubuntu laptop, but I tried twice and it said the same "bcmwl-kernel-source" error. How do I fix this?

---

### Post by TBABill on 2010-10-26
> **Ulysses1994XF04 said:**
> When I first got ubuntu, I had problem installing some programs on it; installation of a download would stop midway and the black box would come up and say "encountered error in bcmwl-kernel-source" or something like that. The same thing happens when I try to install updates.

Now I NEED to install GAIM on my ubuntu laptop, but I tried twice and it said the same "bcmwl-kernel-source" error. How do I fix this?

It's the Broadcom driver. Are you having wireless issues, disconnects, etc?

---

### Post by Ulysses1994XF04 on 2010-10-26
> **TBABill said:**
> It's the Broadcom driver. Are you having wireless issues, disconnects, etc?

No, I get on and stay on the internet just fine. I can also download the entire programs and update packages. It's *installing *them that's giving me trouble.

Why would an internet connectivity issue affect program installations if the programs are fully downloaded?

---

### Post by TBABill on 2010-10-27
I really don't know the answer to that one. Like you said, the file is already downloaded so why would something conflict with the wireless driver? Unless something is corrupted somehow I'll have to let someone with a bit more depth of knowledge on background processes answer that one for you.

---

### Post by Ulysses1994XF04 on 2010-11-08
Here's an example. I tried looking up a way on these forums to download Youtube video to mp3. I found this thread. ([http://ubuntuforums.org/showthread.php?t=855433](http://ubuntuforums.org/showthread.php?t=855433))

I typed all the commands into my Terminal. Here's what I got. 

> steven@Ulysses:~$ sudo apt-get install ffmpeg youtube-dl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
youtube-dl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-25-generic
Building for architecture i686
Building initial module for 2.6.32-25-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6[B]
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

Any suggestions?

---

