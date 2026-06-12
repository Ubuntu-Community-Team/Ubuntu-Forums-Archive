---
title: "Fixing Annoying SystemError:ArchivesFailed For Nvidia Cards"
date: 2012-02-24
forum: General Help
---

### Post by enjoijesus94 on 2012-02-24
Hello Ubuntu Community.

This Tut Today Will Teach You How To Install Your Nvidia Card If You Are Having The SystemError: ArchivesFailed() Message When Trying To Enable Graphics.

First Things First 
1.Download Your Driver Here 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

If Your Unsure About What Type Of Graphics Card You Have.
Open A Terminal And Type. 
> lspci2.If You Dont Got gdm Installed , Install It.
> sudo apt-get install gdmNow That You Have Your Driver. 
You Want To Disable Nouveau.

Now Here We Go

Edit The Blacklist File.
> gksudo gedit /etc/modprobe.d/blacklist.confAt The Very Bottom Put These Within It
> blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatvNow Save And Exit.

Next Open A Terminal And Type.
> sudo update-initramfs -u
To Create A New Image.

After This, Reboot.

After All This Is Done, Log In Using The Text Interface Within Linux By Pressing.
Alt+Ctrl+F4

Next Disable Xorg.
> sudo /etc/init.d/gdm stopNow cd Your Nvidia Driver That You Downloaded.
For Example.
> cd /home/Username/Downloads/YourDriverNow That Your Ready, Its Time To Install.

Simply Run 
> sudo sh /home/YourUsername/Downloads/YourDriverAfter This Is Complete You Will Be Prompted Back At The Text Screen.

Start Xorg Now.
> sudo /etc/init.d/gdm startThen We Start Interface
> startxAll Done!!!!

This Should Enable Your Card.
Just Be Sure To See How Everything Works.
Hope This Thread Helped.

Cheers:popcorn:

---

### Post by cariboo on 2012-02-24
Moved to General Help, as this isn't a Cafe question.

---

