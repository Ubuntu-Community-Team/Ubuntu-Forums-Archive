---
title: "Uninstalling Ubuntu 11.04?"
date: 2011-08-14
forum: General Help
---

### Post by jonathanp63 on 2011-08-14
Hi all,

Just wanted to say before anything that I did love using Ubuntu every now and then but there's a lot of things that I cannot transfer over such as my games, etc.

Anyway, I followed an online tutorial on how to uninstall Ubuntu (not off of any Linux site) and it had me use a program that essentially wiped the partition I had set up clean and then gave me the option to return the memory to my C:\ partition.  

All worked out, but I still find Ubuntu listed under my boot options whenever I turn my computer on.  The screen where you can go into boot options or setup loads very slow since I erased that partition.  I'm not sure if it's related, but it drives me crazy!

I'm not sure if anyone here has ever had a similar issue and could give me a few tips?

Be as critical as you need to be, I know it was dumb to not follow proper instructions from Linux users on how to uninstall the OS.

---

### Post by mendhak on 2011-08-14
Which menu is coming up for you, is it the Windows OS menu or is it Grub?

---

### Post by jonathanp63 on 2011-08-14
> **mendhak said:**
> Which menu is coming up for you, is it the Windows OS menu or is it Grub?

Windows OS menu.  Gives me the option of Win 7 or Ubuntu.  Automatically defaults to Win 7 if I don't choose in the time period.

---

### Post by bro on 2011-08-14
it is not entirely clear what you mean. The default Grub screen that shows the boot menu cannot be present if the linux partition is properly deleted since it loads it configuration from there. 

You say something loads slowly, is not just booting from cd/dvd/usb?

---

### Post by wojox on 2011-08-14
Grub/Grub2 is still located on your Master Boot Record. You can usually use your Windows CD to reinstall The Windows Boot Loader.

---

### Post by bro on 2011-08-14
ah... sorry, I read that jus now. Unfortunately I have no idea how to configure the windows boot menu.

---

### Post by jonathanp63 on 2011-08-14
> **bro said:**
> it is not entirely clear what you mean. The default Grub screen that shows the boot menu cannot be present if the linux partition is properly deleted since it loads it configuration from there. 

You say something loads slowly, is not just booting from cd/dvd/usb?

I'm guessing the Linux partition was not properly deleted during the process.  When I try to open Linux from that boot menu, it doesn't run it.  It just reboots my computer.

I have an Inspiron desktop.  When I turn the PC on, it shows the screen that loads and says "Inspiron" in a big image with my function key options in the bottom for boot options or setup.  That screen used to load almost instantly and now it takes 30 seconds up to 2 minutes.

---

### Post by jonathanp63 on 2011-08-14
> **wojox said:**
> Grub/Grub2 is still located on your Master Boot Record. You can usually use your Windows CD to reinstall The Windows Boot Loader.

Running the Windows CD will give me the option to just install the boot loader?  Just want to make sure I don't have to reinstall the whole OS.

---

### Post by mendhak on 2011-08-14
Yes, if you follow steps such as these your data should be safe

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by wojox on 2011-08-14
> **jonathanp63 said:**
> Running the Windows CD will give me the option to just install the boot loader?  Just want to make sure I don't have to reinstall the whole OS.

Yes there should be an option to Repair your Computer from a menu. Depending on which version of Windows you have it's there somewhere. 

You won't reinstall the whole OS unless you tell it to (that would be a different option).

---

### Post by jonathanp63 on 2011-08-14
> **wojox said:**
> Yes there should be an option to Repair your Computer from a menu. Depending on which version of Windows you have it's there somewhere. 

You won't reinstall the whole OS unless you tell it to (that would be a different option).

My computer did not come with a OS disc.  I believe it's on my recovery partition.  Any difference in that tutorial if I have to boot through recovery?

---

### Post by Mark Phelps on 2011-08-14
If you can still boot into Win7, there is another way to remove the Ubuntu option ...

Go to the NeoSmart Technologies website, download and install the latest version of EasyBCD, and run it.

You will see an option to edit the boot menu.  Click that button.  When presented with the list, just delete the one for Ubuntu, and save it.

When you reboot, that option will no longer be displayed.

---

### Post by wojox on 2011-08-14
> **mark phelps said:**
> 
go to the neosmart technologies website, download and install the latest version of easybcd, and run it.

+1

---

### Post by jonathanp63 on 2011-08-14
> **Mark Phelps said:**
> If you can still boot into Win7, there is another way to remove the Ubuntu option ...

Go to the NeoSmart Technologies website, download and install the latest version of EasyBCD, and run it.

You will see an option to edit the boot menu.  Click that button.  When presented with the list, just delete the one for Ubuntu, and save it.

When you reboot, that option will no longer be displayed.

Extremely quick and efficient fix to my problem.  Thank you all for your help!

---

### Post by bestemdaanhel on 2011-08-14
Under Windows, go to:

```
Start --> Run --> msconfig
```

You should get a Window that looks like the image below. From there you can simply delete the Ubuntu option.

[IMG]http://cdnsupport.gateway.com/s/software/microsof/vista/graphics/MSConfig/MSConfig_boot.gif[/IMG]

Good luck!

---

