---
title: "Win7 keeps on deleting grub, Ubuntu 11 04"
date: 2011-08-18
forum: General Help
---

### Post by pasha811 on 2011-08-18
I have a dual boot system which I made from scratch Win7 and then Ubuntu 11.04.
After installation all worked fine but each time I have to run Win7 (starting it from Grub2) 
when I shut it down and restart the laptop, grub2 is not there anymore and Win7 starts with its bootloader.
To get back to Natty I have to go through the Live CD and install Grub + Boot Repair and run it.
I'm lost.  I attach the boot info results. 

- Thank you very much for help!
- Best Regards
- Pasha811

---

### Post by allwimb on 2011-08-18
Could be that you have installed something on Windows that check the MBR and reinstall it if it has been changed ?

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by LowSky on 2011-08-18
Hi welcome to the forums. Your issue is something I have never experienced in a dual boot scenario. I ran Windows just the other day.

the Windows MBR would have to be installed over Grub to do what it is doing... unless you install the Windows MBR or Grub on your second drive and your BIOS is somehow swapping the drive order at boot up and you have an MBR on both drives.... Yeah that's the only way this makes sense.

Try disconnecting the second drive and see what happens. Or use the BIOS drive selection option at boot to check out each drives behavior if you select it to boot.

---

### Post by pasha811 on 2011-08-18
Thanks for reply.
The second drive you mention is the LiveCD USB from Natty.
Removing it or not does not make any difference.
It's like something actually rewrites the MBR with Win7 infos.
That's weird. I'll check if some corporate software or antivirus is doing that.
As a fallback strategy can Ubuntu 11 04 be booted from Win7 Bootloader using the usual
Install Grub2 into Ubuntu partiton and then peel off the first 512bytes, copy it in Win7 C:
and then edit Win7 bootloader? I'd like to avoid that but if it's the only way to get Natty...

:roll:

---

### Post by mintpenguin20 on 2011-08-18
I think you should just make the switch to ubuntu or distro of your choosing  completely and take windows out of the picture . You could try [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) 

but I doubt wubi will be that much of a difference but hey it might just work out .

If you REALLY need to run windows try virtualbox or wine but that isnt good enough for some people if you really need top performance , you can install virtualbox or wine in the Ubuntu Software Center .

---

### Post by pasha811 on 2011-08-18
> **mintpenguin20 said:**
> I think you should just make the switch to ubuntu or distro of your choosing  completely and take windows out of the picture . You could try [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) 

but I doubt wubi will be that much of a difference but hey it might just work out .

If you REALLY need to run windows try virtualbox or wine but that isnt good enough for some people if you really need top performance , you can install virtualbox or wine in the Ubuntu Software Center .

I have to run both. For the moment I will not boot Win7 until forced to do so.
I have a quick fix that takes 5 minutes so I can live with that .:cool:
In the meantime I enjoy my brand new Natty!

---

### Post by pasha811 on 2011-08-18
I have found the offending software!

McAfee Endpoint Encryption. Everytime Win7 Shutsdown EPE writes the MBR in its old Redmond glory...
So it's not Win7 but a security software. I'm trying to disable that or find a workaround to have security and Ubuntu at the same time.

---

### Post by kansasnoob on 2011-08-18
> **pasha811 said:**
> I have a dual boot system which I made from scratch Win7 and then Ubuntu 11.04.
After installation all worked fine but each time I have to run Win7 (starting it from Grub2) 
when I shut it down and restart the laptop, grub2 is not there anymore and Win7 starts with its bootloader.
To get back to Natty I have to go through the Live CD and install Grub + Boot Repair and run it.
I'm lost.  I attach the boot info results. 

- Thank you very much for help!
- Best Regards
- Pasha811

Your RESULTS.txt was sadly unhelpful at troubleshooting this problem, other than showing me that your Ubuntu is on /dev/sda5, but please read this recent post of mine:

[http://ubuntuforums.org/showpost.php?p=11156991&postcount=3](http://ubuntuforums.org/showpost.php?p=11156991&postcount=3)

Probably one of the easiest ways to fix this would be to use the "super-grub2-disk" to boot into Ubuntu and then install grub to the PBR of the Ubuntu partition by running:

```
sudo grub-install /dev/sda5
```

Then boot into Windows and download EasyBCD 2.1, it's free for personal use (bottom of page):

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

You can then read their documentation on how to set it up to boot both Win and Ubuntu:

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=0F6E4F5173EF08F250ED94F4B65C7827](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=0F6E4F5173EF08F250ED94F4B65C7827)

---

### Post by pasha811 on 2011-08-18
> **kansasnoob said:**
> Your RESULTS.txt was sadly unhelpful at troubleshooting this problem, other than showing me that your Ubuntu is on /dev/sda5, but please read this recent post of mine:

[http://ubuntuforums.org/showpost.php?p=11156991&postcount=3](http://ubuntuforums.org/showpost.php?p=11156991&postcount=3)

Probably one of the easiest ways to fix this would be to use the "super-grub2-disk" to boot into Ubuntu and then install grub to the PBR of the Ubuntu partition by running:

```
sudo grub-install /dev/sda5
```Then boot into Windows and download EasyBCD 2.1, it's free for personal use (bottom of page):

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

You can then read their documentation on how to set it up to boot both Win and Ubuntu:

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=0F6E4F5173EF08F250ED94F4B65C7827](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=0F6E4F5173EF08F250ED94F4B65C7827)

Thank you.
In the meantime I have discovered that McAfee End Point Encryption has two services, called Safeboot (one is a service the other a startup item) that can be disabled. Their aim is to copy back the original MBR at shutdown to protect your environment. By disabling this I am now able to boot & reboot without problems between the two!
Bad Karma for McAfee guys who did not care about dual boot systems...](*,)

- Best Regards
- Pasha

---

