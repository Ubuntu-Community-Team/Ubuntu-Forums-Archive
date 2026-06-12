---
title: "Slow Downloads"
date: 2012-02-17
forum: General Help
---

### Post by LifeWithoutWindows on 2012-02-17
When Im running my Dual-Boot Machine on Windows, I get considerably faster download speeds than when running Ubuntu 11.10
[http://www.speedtest.net/result/1778410501.png](http://www.speedtest.net/result/1778410501.png)

I know for a Fact on Windows I get over 20 Meg down and About the same speed upload.

I think this may be a driver problem, but I cant seem to find a Driver for Ubuntu 11.10

[[Motherboard]("http://www.asus.com/Motherboards/AMD_AM3Plus/M5A97/#specifications")]

---

### Post by tomsn2 on 2012-02-17
**[B][SIZE=1]I came across this so I thought I would post it here.  I don't have that problem so I haven't tried what's in the post.  I hope it works.  If so, Kudos to BigWhale.[/SIZE]**
[/B]

[B]
[/B]

[B]Repost from BigWhale on Three Wise Men
[/B]

[B]
[/B]

**[Realtek RTL8168/8111E and Ubuntu Linux]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/")**

Posted by BigWhale on October 10th, 2011 in [Linux]("http://www.twm-kd.com/category/linux/") | [21 comments]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/#comments")
 

If  you are using Ubuntu (and probably other distributions too) and you  have an on board Realtek RTL8168/8111E PCI Express network adapter you  might find your network not working as it should. Slow connections or no  connection at all and your logs full of messages like these:
Oct 02 09:[COLOR=#000000]13[/COLOR]:[COLOR=#000000]25[/COLOR] machine kernel: r8169 0000:04:[COLOR=#000000]00.0[/COLOR]: eth0: [COLOR=#c20cb9]**link**[/COLOR] up Oct 02 [COLOR=#000000]12[/COLOR]:[COLOR=#000000]45[/COLOR]:[COLOR=#000000]17[/COLOR] machine kernel: r8169 0000:04:[COLOR=#000000]00.0[/COLOR]: eth0: [COLOR=#c20cb9]**link**[/COLOR] up Oct 02 [COLOR=#000000]12[/COLOR]:[COLOR=#000000]45[/COLOR]:[COLOR=#000000]20[/COLOR] machine kernel: r8169 0000:04:[COLOR=#000000]00.0[/COLOR]: eth0: [COLOR=#c20cb9]**link**[/COLOR] up Oct 02 [COLOR=#000000]13[/COLOR]:[COLOR=#000000]15[/COLOR]:[COLOR=#000000]12[/COLOR] machine kernel: r8169 0000:04:[COLOR=#000000]00.0[/COLOR]: eth0: [COLOR=#c20cb9]**link**[/COLOR] up Oct 02 [COLOR=#000000]13[/COLOR]:[COLOR=#000000]15[/COLOR]:[COLOR=#000000]13[/COLOR] machine kernel: r8169 0000:04:[COLOR=#000000]00.0[/COLOR]: eth0: [COLOR=#c20cb9]**link**[/COLOR] up Oct 02 [COLOR=#000000]13[/COLOR]:[COLOR=#000000]22[/COLOR]:[COLOR=#000000]13[/COLOR] machine kernel: r8169 0000:04:[COLOR=#000000]00.0[/COLOR]: eth0: [COLOR=#c20cb9]**link**[/COLOR] up

Read on if you want to know why this happens and how to solve the problem.
 
 Driver that is included in vanilla Linux kernel is actually a driver  for a different network adapter, but works with 8111E too. Sort of  works. Realtek made new official driver that fixes the problem, but  disables the old driver. Which could be a problem for you if you have  RTL8169/8110 and RTL8168/8111[1]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/#footnote_0_5237").
First you will need the latest driver for your network adapter. Get it [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false"). You will have to extract it and compile it. Current version is 8.025.00.
$ [COLOR=#c20cb9]**tar**[/COLOR] [COLOR=#660033]-xvjf[/COLOR] r8168-8.025.00.tar.bz2 $ [COLOR=#7a0874]**cd**[/COLOR] r8168-8.025.00 $ [COLOR=#c20cb9]**make**[/COLOR] modules

If  you are running Ubuntu 11.10 Oneiric Ocelot then you can ignore the  README file and autorun.sh script. The script is broken and the  information in the README is obsolete. For other distributions and  kernels autorun.sh might work. When make is complete you will have to  get rid of the old module and replace it with the new one. Do this,  while you’re still in the r8168-8.025.00 directory.
$ [COLOR=#7a0874]**cd**[/COLOR] src $ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**cp**[/COLOR] r8168.ko [COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]modules[COLOR=#000000]**/`**[/COLOR][COLOR=#c20cb9]**uname**[/COLOR] -r[COLOR=#000000]**`/**[/COLOR]kernel[COLOR=#000000]**/**[/COLOR]drivers[COLOR=#000000]**/**[/COLOR]net[COLOR=#000000]**/**[/COLOR] $ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**mv**[/COLOR] [COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]modules[COLOR=#000000]**/`**[/COLOR][COLOR=#c20cb9]**uname**[/COLOR] -r[COLOR=#000000]**`/**[/COLOR]kernel[COLOR=#000000]**/**[/COLOR]drivers[COLOR=#000000]**/**[/COLOR]net[COLOR=#000000]**/**[/COLOR]r8169.ko [COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]modules[COLOR=#000000]**/`**[/COLOR][COLOR=#c20cb9]**uname**[/COLOR] -r[COLOR=#000000]**`/**[/COLOR]kernel[COLOR=#000000]**/**[/COLOR]drivers[COLOR=#000000]**/**[/COLOR]net[COLOR=#000000]**/**[/COLOR]r8169.ko.old $ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**depmod**[/COLOR] [COLOR=#660033]-a[/COLOR]

Now, all you need to do is to take care that the driver will load on boot.
$ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#7a0874]**echo**[/COLOR] [COLOR=#ff0000]"r8168"[/COLOR] [COLOR=#000000]**>>**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]modules

Wouldn’t it be wise to test if the new driver is working at all, before you reboot? Easier than eating pancakes!
$ [COLOR=#c20cb9]**sudo**[/COLOR] modprobe [COLOR=#660033]-r[/COLOR] r8169 [COLOR=#666666]*# At this point your network will stop working*[/COLOR] $ [COLOR=#c20cb9]**sudo**[/COLOR] modprobe r8168 [COLOR=#666666]*# And now network manager should pick up the new connection*[/COLOR]

Oh, and if you are annoyed that now your network interface is *eth1* instead of *eth0* as it used to be, remove the two lines from */etc/udev/rules.d/70-persistent-net.rules* that end with NAME=”eth0&#8243; and NAME=”eth1&#8243;.

---

