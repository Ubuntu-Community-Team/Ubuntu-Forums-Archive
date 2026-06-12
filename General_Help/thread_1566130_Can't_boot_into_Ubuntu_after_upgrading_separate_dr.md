---
title: "Can't boot into Ubuntu after upgrading separate drive's Windows OS"
date: 2010-09-02
forum: General Help
---

### Post by TonyChaos on 2010-09-02
Hey all! I had a quick question and issue. I have two hard drives in my HP, on had XP and the other had Ubuntu Lucid Lynx. I upgraded my XP drive to Windows 7 and now it won't give the an option to boot into Ubuntu like it did before with XP. 

I was wondering how to fix this? I miss my Linux!

---

### Post by garvinrick4 on 2010-09-02
> **TonyChaos said:**
> Hey all! I had a quick question and issue. I have two hard drives in my HP, on had XP and the other had Ubuntu Lucid Lynx. I upgraded my XP drive to Windows 7 and now it won't give the an option to boot into Ubuntu like it did before with XP. 

I was wondering how to fix this? I miss my Linux! Can you get into the BIOS and choose to boot off of your second drive. 
 Before on XP were you booting off of Ubuntu grub or the Windows boot manager? Windows 7 has a different boot manager than XP and would overwrite any other on upgrade. If you want to install grub2 to sda that would be one way. Or select to boot in BIOS on whatever drive you want to boot each having a different boot manager. I like grub2 myself to manage all drives.

---

### Post by TonyChaos on 2010-09-02
I believe I was booting from an Ubuntu grub. It was set to my primary operating system, though it was on a separate drive. I had to go to the bottom where it listed other operating systems and pick XP. I can try to boot into Ubuntu via the BIOS now and let you know how it goes from there.

---

### Post by TonyChaos on 2010-09-02
So it didn't go well. I got a screen that told me to hit tab to list file commands? It was something I've never encountered before. I even cracked open my desktop to unplug the drive with Windows 7 on it and it kept giving me the error. 

Anymore suggestions? Maybe something I could do on the Windows side to get it to give me the option of which drive to boot into from startup?

---

### Post by garvinrick4 on 2010-09-02
Get your drives plugged back into case. Grab a Ubuntu CD and  boot off of it and choose Try Ubuntu. When it boots up go to this website and download this script to your desktop.[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
Then run this code below in a terminal and you will get a text file on your desktop.
Copy and paste it into this Thread. After you copy and paste it highlight the whole thing and then click the # sign and it will make it take up less room. 
Most likely we will just have to install grub into sda but might as well look at your boot info to make sure. 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by TonyChaos on 2010-09-02
I'll need to download an Ubuntu image, as I lent my Ubuntu disc to a buddy of mine. I'll have at it now.

---

