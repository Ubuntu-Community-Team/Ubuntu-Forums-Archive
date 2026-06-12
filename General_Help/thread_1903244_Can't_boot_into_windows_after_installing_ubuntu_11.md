---
title: "Can't boot into windows after installing ubuntu 11.10"
date: 2012-01-02
forum: General Help
---

### Post by arnold255 on 2012-01-02
I have just installed ubuntu 11.10 in my hp 620 laptop, every thing went fine untill I upgraded and installed some few packages,then rebooted into window 7 and then back to ubuntu, afterward when I wanted to boot into window I got a massage "GRUQ is missing press ctl+alt to restart" I did press the keys and restart this time no any massage displayed and the window 7 bootloader disappeared from the boot menu. Oops can't boot into window. Help please.

---

### Post by carl4926 on 2012-01-02
In a terminal try

```
sudo update-grub
```

---

### Post by Mark Phelps on 2012-01-02
HOW did you install Ubuntu:
1) Using Wubi -- from inside Windows
2) Booting from USB or CD -- to its own partition.

Also, did you boot into Win7, and were you able to use it AFTER the Ubuntu install but BEFORE the updates?

---

### Post by sherric1222 on 2012-01-02
How are you running windows 7 and ubuntu together, aren't they different operating systems?? I didn't know you could run them together.  I had Windows 7 and loved it until it crashed, then downloaded ubuntu and I have had nothing but trouble.  I don't like it and I'm waiting for Dell to send me a flash bit so that I can return to window 7.  I have a x64 and it's trying to run firefox, which is a 32 bit. So it keeps crashing. Any Ideas on how to download waterfox instead?

---

### Post by kalfusisagod on 2012-01-02
> **sherric1222 said:**
> How are you running windows 7 and ubuntu together, aren't they different operating systems?? I didn't know you could run them together.  I had Windows 7 and loved it until it crashed, then downloaded ubuntu and I have had nothing but trouble.  I don't like it and I'm waiting for Dell to send me a flash bit so that I can return to window 7.  I have a x64 and it's trying to run firefox, which is a 32 bit. So it keeps crashing. Any Ideas on how to download waterfox instead?

You can run Linux and Windows together for years now. You can dual boot with a bootloader like GRUB or you can even do a virtual machine. The only problem with dual booting is that if you can use only one OS at a time and sometimes whatever files you save on Linux will not be seen by windows so you'd have to save them to a thumbdrive or something. Another problem with dual booting is that if you install Linux first, and then Windows second, windows will wipe out the Linux partition because of monopoly reasons. There are other advantages and disadvantages to dual booting so Virtualization is the answer. I'm not sure what Dell is feeding you.

---

### Post by audiomick on 2012-01-02
> **kalfusisagod said:**
> if you install Linux first, and then Windows second, windows will wipe out the Linux partition because of monopoly reasons.

Not true. Windows does overwrite the MBR and remove grub, the bootloader, but does not remove Ubuntu unless you let the installer use the whole drive.

---

### Post by sherric1222 on 2012-01-05
Wow, didn't know that you can run both, thanks for the info.  I just prefer Windows over Ubuntu.  I guess it just takes getting use too.  I'm on Bigfish games and now I can't download any of there games, anybody know how to download games from other sites?

---

### Post by meetdilip on 2012-01-05
Same problem here. Installed Ubuntu 64 bit from CD using " alongside Windows " option over already installed Windows 7 Ultimate 64 bit. Ubuntu is in sda5 where as Windows is in sda 3. During startup it shows an option called " Windows loader sda3 " something. But when I choose that option, it says cannot read from disc or similar and shows option to use ctrl + alt + del and I use that to get into Ubuntu 11.10. 

Should I simply try the command in post no. 2 ?  I have only Ubuntu now, want to make sure that I have at least one OS. Thanks.

---

### Post by Mark Phelps on 2012-01-05
> **meetdilip said:**
> Should I simply try the command in post no. 2 ?  I have only Ubuntu now, want to make sure that I have at least one OS. Thanks.

First of all, I asked for more info DAYS ago ... and the OP hasn't bothered to grace us even with a reply.  So, without the details, there's little more that can be done.

Second, as to the windows not booting problem, different details require different solutions.  So, instead of tacking your request onto the end of this one, would be better to start your own thread on this.

That will allow us to deal with you directly.

thanks

---

### Post by meetdilip on 2012-01-05
Sure Mark. Thought making a new thread may not be welcome. Thanks for the reply.

---

### Post by Mark Phelps on 2012-01-05
> **meetdilip said:**
> Sure Mark. Thought making a new thread may not be welcome. Thanks for the reply.

Actually, new threads are welcome here.  It helps us support folks focus on the unique aspects of each situation, which works out better for the poster.

Note: already saw your new thread and responded.

---

