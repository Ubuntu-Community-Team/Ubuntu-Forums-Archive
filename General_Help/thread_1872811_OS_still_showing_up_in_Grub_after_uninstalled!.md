---
title: "OS still showing up in Grub after uninstalled!"
date: 2011-10-31
forum: General Help
---

### Post by MoonLitOwl on 2011-10-31
(This issue has been solved!)

So after fighting with Joli OS in an attempt to get it to connect, I decided to uninstall it.

I had done this once before, and there were no issues. But now, after taking it off, the bloody thing still shows up in the Grub menu under Windows 7. 

Anyway I can get it off?

(I wasn't sure where else to put this)

---

### Post by wojox on 2011-10-31
Did you updte grub?

---

### Post by MoonLitOwl on 2011-10-31
> **wojox said:**
> Did you updte grub?

I have no idea what that even means. :) Im very new to the who Linux thing.

---

### Post by ofnuts on 2011-10-31
> **MoonLitOwl said:**
> I have no idea what that even means. :) Im very new to the who Linux thing.
man update-grub

:D

---

### Post by grahammechanical on 2011-10-31
Do you still have Ubuntu installed? How did you un-install Joli OS? Did you re-format its partition or delete its partition?

From the information that you have given we are guessing the Joli would have been the third OS that you have installed - Windows 7, Ubuntu and Joli. Please confirm this.

If you are now dual booting into Windows 7 and Ubuntu. Then boot into Ubuntu and load the terminal and run the command sudo update-grub and that should fix it.

But really you need to give more information. We are having to make assumptions.

Regards.

---

### Post by MoonLitOwl on 2011-10-31
> **grahammechanical said:**
> Do you still have Ubuntu installed? 

No, I'll be putting it back on once I get Joli out of my Grub.

> How did you un-install Joli OS?Same as the first time. Went to my C drive, deleted it's folder. 

> Did you re-format its partition or delete its partition?I've no idea how to do that. The install is fairly simple and keeps things easy when installing (partition included). When Joli is installed, the partition actually shows up on my C drive, which I did like. It just shows how much room I had left for Windows 7.

> From the information that you have given we are guessing the Joli would have been the third OS that you have installed - Windows 7, Ubuntu and Joli. Please confirm this.

Yes, but before I installed Joli, I took Ubuntu off. I'll be putting it back on; didn't want to over-work my little laptop by having three OS on it at the same time.

> If you are now dual booting into Windows 7 and Ubuntu. Then boot into Ubuntu and load the terminal and run the command sudo update-grub and that should fix it.

But really you need to give more information. We are having to make assumptions.

Regards.Sorry, though I did state in my first post that Joli is showing up in the Grub under Windows 7. =P 

Suppose installing Ubuntu again, and putting that command into the terminal may do the trick. I'll give it a go and let ya'll know if it works.

---

### Post by fantab on 2011-10-31
If Joli was installed on a separate Partition, it will be better if you reformat that partition, you can use Gparted which is provided with Ubuntu live CD.

Reinstall Ubuntu and the Grub will detect only the installed OSes.

---

### Post by grahammechanical on 2011-10-31
I have just searched Joli OS and I would say that although you have uninstalled Joli and the reference is still showing up in the boot menu, it is not the Grub boot menu but the Windows Boot Manager. See this link

[http://help.jolicloud.com/entries/230291-how-do-i-install-joli-os-while-keeping-windows]("http://help.jolicloud.com/entries/230291-how-do-i-install-joli-os-while-keeping-windows")

Go to section 5 Install Joli OS notice what is written on the top of the picture of the boot loader.

I know that there are some very experienced people on this forum but I did not know that we gave support for the Joli OS. Should you not be turning to the Joli cloud community for advice?

Regards.

P.S. Did you see this?

[http://help.jolicloud.com/entries/249557]("http://help.jolicloud.com/entries/249557")

See the section Restore the boot menu. It seems that Joli OS uses Grub. Well I never! But what you have to do is listed in that section.

---

### Post by MoonLitOwl on 2011-10-31
> **grahammechanical said:**
> I have just searched Joli OS and I would say that although you have uninstalled Joli and the reference is still showing up in the boot menu, it is not the Grub boot menu but the Windows Boot Manager. See this link

[http://help.jolicloud.com/entries/230291-how-do-i-install-joli-os-while-keeping-windows](http://help.jolicloud.com/entries/230291-how-do-i-install-joli-os-while-keeping-windows) 

Right well, even though Joli OS is not even on my computer anymore, it still showing up there.

> I know that there are some very experienced people on this forum but I did not know that we gave support for the Joli OS. Should you not be turning to the Joli cloud community for advice?

I went to the Joli website. There's no bloody forum, and I've no idea how you even found the link below. I had to search through bing just to find another forum (that's not even connected to Joli OS) when I was still trying to figure out how to get my wireless to work on it. They seriously lack in the community department.

> Regards.

P.S. Did you see this?

[http://help.jolicloud.com/entries/249557](http://help.jolicloud.com/entries/249557)

See the section Restore the boot menu. It seems that Joli OS uses Grub. Well I never! But what you have to do is listed in that section.

Which I did. I went in through my "remove" programs AND tbhrough my c-drive. It's not there anymore.

Rather odd. Anyways, I'll be instaling Ubuntu again in a bit. I'm hoping that it will clear Joli from the boot.

---

### Post by Paddy Landau on 2011-10-31
Simply install Ubuntu (I presume you will install it over Joli).

When it installs, it will refresh Grub.

---

### Post by wojox on 2011-10-31
> **Paddy Landau said:**
> Simply install Ubuntu (I presume you will install it over Joli).

When it installs, it will refresh Grub.

+1 I thought you had Ubuntu installed. ^^ This will work

---

### Post by MoonLitOwl on 2011-10-31
> **wojox said:**
> +1 I thought you had Ubuntu installed. ^^ This will work

My apologies for not being more clear in the OP.

I actually NOW have it installed, but along side Win7. Joli is still showing up( (lol! surprise) but I'm not going to worry about it. It doesn't seem to be bothering my system at all, just grinding on my nerves. 

I still need Win7 for the time being (Office 2010, but just till the start of Dec) and then I'll be making Ubuntu as my main and only OS. That should take care of Joli.

Thanks folks!

---

### Post by Paddy Landau on 2011-11-01
> **MoonLitOwl said:**
> I actually NOW have it installed, but along side Win7. Joli is still showing up...
I've reread your posts and visited the Joli site, and I realise that you have installed Joli via the Windows installer. (This is the same concept as using WUBI for Ubuntu.)

In this case, Joli has inserted itself into the Windows start-up routine.

The only way that I know to solve this is to boot into Windows and use a third-party application such as [EasyBCD]("http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html"). Having done that, you may then find you can boot only into Windows. If that happens, you'll need to boot from an Ubuntu Live CD and repair Grub.

But if you're getting rid of Windows anyway soon, then it's not worth the bother.

---

