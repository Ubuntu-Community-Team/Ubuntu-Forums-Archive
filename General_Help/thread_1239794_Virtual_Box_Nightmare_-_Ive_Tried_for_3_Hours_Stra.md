---
title: "Virtual Box Nightmare - Ive Tried for 3 Hours Straight to Get Working - No Results."
date: 2009-08-13
forum: General Help
---

### Post by therocco2k on 2009-08-13
:(

I Really need help -- Please take the time to help me, It's really important to test windows 7 while i'm coding in Ubuntu Jaunty. Not to sound desperate, but PLEASE help.

I Downloaded the .deb Package for Linux Host of Virtual Box AMX64 from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), Then Followed the instructions on the next page, here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

I've created a Monster (I installed VB the first time I had Ubuntu Installed my First Try. I Forgot where I followed the tutorial but NOW - I've tried for literally 3 hours to fix this and get this program working. It never shows up under Applications>System Tools - It Always has problems, and It's from one of the times I Tried to install it - It Messed with the Kernel and now I cannot get ANY installation of VB working on my machine. It wont Load, or anything.

I'm really at a lost of what to do. I think the Virtual Box Kernel is F'd up.

Can somebody please tell me how to Remove all traces of Virtual Box from software, kernel, purges, etc... and get my computer back to how it was before I Followed the wrong tutorial, and then get a Link or Some help getting this program Installed Correctly?

I've tried to install virtualbox3.0, virtualbox-ose, virtualbox2.2 - Nothing Works, installation terminal shows that things fail around the kernel and what not.

So, besides from reinstalling Ubuntu - What am I looking at here? I've uninstalled all the Previous Virtual Box Attempts and retried with the synaptic package manager and it still doesnt work. 

If you need me to get you any information, I'll be willing to do anything.

Much Thanks, - much Love.. Get me through this please.

---

### Post by esalnoj on 2009-08-13
Removing the package from synaptic doesn't remove all the bits  installed.

Go places>search and type "vbox" without qoutes, hit enter, and see what comes up.

Then open terminal and follow this technique EXACTLY, inserting your specific file paths into "filepath/just/above/file" and your folder or file into "folder or file":
```
cd "filepath/just/above/file"
sudo rm -rf "folder or file"
```

If this technique isn't followed exactly, YOU WILL DESTROY YOUR SYSTEM AND HAVE TO DO A FRESH INSTALL!

Then search "virtualbox" and repeat the above technique.

---

### Post by therocco2k on 2009-08-15
Thank you - I've got Virtual Box Running.

---

