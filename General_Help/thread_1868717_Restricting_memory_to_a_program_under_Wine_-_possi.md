---
title: "Restricting memory to a program under Wine - possible or pointless?"
date: 2011-10-24
forum: General Help
---

### Post by zozza on 2011-10-24
I am running a program under Wine which keeps crashing (the screen grays out and it gets stuck).

I can only assume this is due to the vast amount of memory it is using.

ps aux:

%CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

47.9 13.8 1667784 141148 ?      Sl   22:06   1:39 C:\Program Files\Informatica64\FOCA Free\FOCA Free.exe     

Is there a way to restrict the amount of memory a program uses in Wine?  Do people think that this is the best way to prevent the crash?

Thanks.

---

### Post by Paddy Landau on 2011-10-24
No, the exact opposite. If it is crashing due to memory use, restricting its memory would make it worse.

The chances are that it crashes because Wine is not a perfect replacement for Windows.

---

### Post by Mark Phelps on 2011-10-24
Anything that is NOT listed at the WineHQ site as being compatible with Wine is unlikely to work.  Informatica's FOCA is NOT listed.  

Therefore, it could be crashing simply because like, so many OTHER Windows apps, it's simply not compatible with Wine.

If you're going to use Wine, you need to take the time to check the WineHQ site for compatibility ratings, first.

---

### Post by zozza on 2011-10-27
Thank you for the advice.

Would the best solution then be to install a virtual machine then run XP (for example) in it?

Does that sound viable?

Is there a particular VM that people would recommend (considering I have never used any VMs before).

Many thanks.

---

### Post by Paddy Landau on 2011-10-27
If your computer has a good amount of RAM, you can indeed run a VM.

[VirtualBox]("https://www.virtualbox.org/") seems to be the most popular; I have used it, and it is good. Be sure to follow the instructions under "Debian-based Linux distributions" on the [Linux download page]("https://www.virtualbox.org/wiki/Linux_Downloads"), and also download and install the Extension Pack from the [main download page]("https://www.virtualbox.org/wiki/Downloads").

However, a VM does run slowly. Use it if you use your Windows program occasionally and speed is not an issue. If speed is an issue, or you use your Windows program for long periods, you may prefer a dual-boot.

Another alternative is a hypervisor, but that is useful only if you have a strong modern 64-bit computer with virtualisation (you may need to enable virtualisation in your BIOS). A hypervisor (the default is KVM for Ubuntu) allows you to swap between Windows and Ubuntu without rebooting. I understand it is complex to set up, so don't go this way if you don't really need to (unless you want to experiment).

---

### Post by Mark Phelps on 2011-10-27
> **zozza said:**
> Would the best solution then be to install a virtual machine then run XP (for example) in it?

A VM is certainly an option, and often ends up being the ONLY option when something won't work right under Wine (or any of its derivatives) and you don't want to dual-boot.  

The main concern I have, and the reason I don't use it, is that you have to reinstall from scratch. Not only does that mean that ALL your apps have to be installed again -- and, if they have received updates over the years, those updates as well, but if you're reinstalling the ORIGINAL XP, you will have three Service Packs and HUNDREDS of Windows Updates to do to make it a "current" system.

To me, that is a LOT of work, just to continue to use an Windows app that is already working in MS Windows.

---

### Post by oldtimer7777 on 2011-10-27
Use Virtualbox or VMWare to run Windows..  Wine and PlayOnLinux are for things you only need to use occasionally.

---

