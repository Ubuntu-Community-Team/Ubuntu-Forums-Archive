---
title: "PXE boot live CD"
date: 2010-06-24
forum: General Help
---

### Post by vader95 on 2010-06-24
Does anybody know how to boot a live cd through PXE and to have the server be Windows.  I have a program and have booted the installer, now i would like to know if it is possible to boot a live CD.


Thanks,
vader95

---

### Post by vader95 on 2010-06-27
ok, i got the main kernel to boot up until it searches for the file system.  Any ideas?

thanks,
vader95

---

### Post by Digimer on 2010-06-28
I'm trying to sort this out, also, and I've got the same problem. It boots to the point where it kernel panics with the error:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

I'm trying to mount the 10.04 x86_64 CD. The ISO files are mounted and accessible from the PXE server via HTTP. Thanks for any help/pointers!

Digi

---

### Post by idrocas on 2010-10-10
Hello my friends

Well I like to know what happened with your livecd netboot

I'm trying the same thing but I'm stuck

Can you help me?

ROC@S
MEXICO

---

### Post by vader95 on 2010-10-19
I now have a working boot server.

I will post the procedure in a couple of days, once I get it fixed.

---

### Post by idrocas on 2010-10-20
Thank you my friend,

That is good news, I just can tell you I'm stuck with my server I'm trying to boot from Windows XP Pro SP3 + TFTPD + NFS but the Ubuntu 10.04 LiveCD takes forever to boot and never shows the desktop.

I already try some other guides from the internet but untill today nothing is working to me.

I'll wait for your directions.

Have a great day!

---

### Post by vader95 on 2010-10-20
> **idrocas said:**
> Thank you my friend,

That is good news, I just can tell you I'm stuck with my server I'm trying to boot from Windows XP Pro SP3 + TFTPD + NFS but the Ubuntu 10.04 LiveCD takes forever to boot and never shows the desktop.

I already try some other guides from the internet but untill today nothing is working to me.

I'll wait for your directions.

Have a great day!

Unfortunately, the tutorial I have is from a linux server, and from what I hear, you have to use a linux server. I got my tutorial from

[HTML]http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/[/HTML]but i found a couple of issues, and was going to fix it and post it here.

You would also need a DHCP server by the way.

You also have a great day.

---

### Post by vader95 on 2010-10-21
Here are the links I used.  It is going to take me a little longer to put together the whole tutorial.

[HTML]  http://www.jonathanmoeller.com/screed/?p=1677
   
  http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/
   
  http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/
   [/HTML]




If you run into any errors, please let me know and I will see what I can do.  If you need to please feel free to PM me if I don't respond.


Also, if you give me your XP setup, I'll see what I can do here because I have some spare xp machines.




vader95

---

