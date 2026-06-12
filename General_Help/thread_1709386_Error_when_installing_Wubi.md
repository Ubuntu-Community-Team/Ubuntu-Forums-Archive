---
title: "Error when installing Wubi"
date: 2011-03-18
forum: General Help
---

### Post by Scunnered on 2011-03-18
I have tried to load Wubi with 10.04 LTS in Windows 7 only at the last gasp to have the following error displayed:

c:/users/ian/appdata/local/temp/wubi-10.04

and advising that I could check the error via the above path.

I attempted to follow the path only to find that on reaching /ian nothing resembling the appdata is revealed.

Can anyone offer guidance.

---

### Post by Rubi1200 on 2011-03-18
Try placing the wubi.exe file and the downloaded ISO image in the same folder and then running wubi.exe again.

Let us know if that helps.

---

### Post by bcbc on 2011-03-18
That folder is hidden, but you can get to it by entering %temp% in your windows explorer address bar. (Or unhide hidden folders).

If you are installing 10.04 Wubi, you need the 10.04.2 version of Wubi.exe. Or you need to --skipmd5check if you are running it off an older version of 10.04 (e.g. 10.04 or 10.04.1).

Note that if you install an older version it will prompt you to update to 10.04.2 anyway once you boot Ubuntu. You also MUST lock packages grub-pc and grub-common if you are installing an older 10.04 release. See the wubi megathread in Rubi1200's signature for details on how to do this.

PS the only way to get 10.04.2 wubi.exe right now is either off an 10.04.2 Ubuntu Desktop CD ISO or by downloading from here: [http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe)

---

### Post by Scunnered on 2011-03-19
My thanks to you all for your kind replies.

Followed the link provided by **bcbc** which worked a treat.

I will have my partner using Ubuntu yet.  Just one more problem to resolve.

Agaion thanks

---

### Post by Rubi1200 on 2011-03-19
Excellent! Glad you got it sorted out.

Don't forget to lock the grub-* packages as bcbc advised.

See the link to the Wubi Megathread at the bottom of my post.

---

### Post by Scunnered on 2011-03-19
**Rubi1200**

Thanks for your advice.  You now have me confused.  My reading of the post by **bcbc**was that by loading the link I would have the current 10.04.2 which would not require any further attention.

Are my thoughts right or have I got things confused ??

---

### Post by Rubi1200 on 2011-03-19
From what I understand, 10.04.2 should be okay. However, it won't affect the Wubi install negatively if you lock those packages and it is probably prudent to do so anyway.

---

### Post by bcbc on 2011-03-19
Wubi installs are breaking with grub updates. Currently - as far as I am aware - there are no grub updates for 10.10 and 10.04.2. Strictly speaking Wubi users are advised to lock grub-pc and grub-common anyway until the bugs are fixed since it's not possible to predict when the next grub update will be released.

With 10.04 and 10.04.1 it's a certainty that running updates will include grub, so that's what I meant. (But I should have just said you should lock them to protect from potential future updates).

---

### Post by Scunnered on 2011-03-19
Every time I think I am making progress the forum slings another curved ball.  One of these days I will make an immediate hit.

**bcbc**

Can you please detail what I need to do to "lock grub-pc and grub-common anyway" as this is another of these curved balls.

Thanks again for your assistance

---

### Post by bcbc on 2011-03-19
> **Scunnered said:**
> Every time I think I am making progress the forum slings another curved ball.  One of these days I will make an immediate hit.

**bcbc**

Can you please detail what I need to do to "lock grub-pc and grub-common anyway" as this is another of these curved balls.

Thanks again for your assistance

From the Wubi megathread:
> **Rubi1200 said:**
> 
Go to System > Administration > Synaptic Package Manager and select the grub-pc and grub-common packages. Click on Package > Lock Version.


---

### Post by Scunnered on 2011-03-20
**bcbc**

Many thanks for the information.  Once again my Ubuntu experience is expanded. For al the time I have been in and out of Synaptic I have never noticed this detail.

My sincere thanks.

---

### Post by bcbc on 2011-03-20
> **Scunnered said:**
> **bcbc**

Many thanks for the information.  Once again my Ubuntu experience is expanded. For al the time I have been in and out of Synaptic I have never noticed this detail.

My sincere thanks.

Hey you're welcome. Most things we find out on a 'need to know' basis. Wubi + Grub = need to know. 

The other thing I'd advise is to keep important data backed up or off the 'virtual disk' file. Files stored natively on the partition are more robust than those all stuffed onto the single virtual disk (plus you can access them easier). So consider perhaps creating a symlink to a directory on the ntfs /host to access and store pictures, instead of placing them on the root.disk. It's tidier, safer and you don't have to wonder later where you put them.

---

### Post by Scunnered on 2011-03-21
Again thanks for the advice.  If everything works the way that I hope then after trials via Wubi I suspect that a new laptop will be the order of the day and a proper dual boot.

The laptop that currently is in use will not work with the Linux kernel(s) so that is why I am looking at Wubi meantime.

---

### Post by bcbc on 2011-03-21
> **Scunnered said:**
> Again thanks for the advice.  If everything works the way that I hope then after trials via Wubi I suspect that a new laptop will be the order of the day and a proper dual boot.

The laptop that currently is in use will not work with the Linux kernel(s) so that is why I am looking at Wubi meantime.

Wubi installs are the same as normal installs, apart from the virtual disk (plus the install method and a different boot mechanism). So if it runs Ubuntu from Wubi it is capable of running a normal Ubuntu install.

---

### Post by Scunnered on 2011-03-21
> **bcbc said:**
> Wubi installs are the same as normal installs, apart from the virtual disk (plus the install method and a different boot mechanism). So if it runs Ubuntu from Wubi it is capable of running a normal Ubuntu install.

I wish that were so. I bought 2 identical systems in the UK with one haveing XP and the other without any OS.  It was my intent to install Ubuntu on the naked one only to find that it would not install.  I had eventually to send the laptop back to the manufacturer as they admitted that it was not fit for purpose.

Eventually bought one with 8.04 pre installed.

Now she should be obeyed wants to switch over so I am playing things very safe.  If Wubi works OK then dependant on how things go I will take matters from there.

Being a miserable Scot I hope it works with Wubi as I can see me being mugged for a new laptop otherwise.

Again my thanks

---

### Post by bcbc on 2011-03-21
So you're already running Ubuntu with Wubi? If so, then it works on that computer - I can't think of any thing different that should make it work with Wubi and not with normal.

Although many people assume Wubi Ubuntu runs within Windows or somehow different due to Windows, this is not the case - it is a natively run Ubuntu - just the 'partition' is a loop device that is a file off an ntfs or fat32 partition.

---

