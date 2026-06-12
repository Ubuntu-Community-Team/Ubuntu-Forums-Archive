---
title: "Wubi problem / Grub / Windows Boot Manager."
date: 2012-02-29
forum: General Help
---

### Post by Zaxfair on 2012-02-29
I have instaled Wubi and chose Ubuntu 11.10 everything fine then I reboot but windows manager don't show up.And it only go to Lixnux.

I have do ne this: all off this

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

this

[http://dicasdofabio.wordpress.com/2011/08/27/alterar-ordem-de-boot-windows-7-x-ubuntu-11-04/](http://dicasdofabio.wordpress.com/2011/08/27/alterar-ordem-de-boot-windows-7-x-ubuntu-11-04/)

but i can do this 

[http://aurelianomartins.wordpress.com/2012/02/02/grub-alterar-ordem-de-boot-entre-windows-e-linux/](http://aurelianomartins.wordpress.com/2012/02/02/grub-alterar-ordem-de-boot-entre-windows-e-linux/)


Someone please help-me I 'm frustreded.

I wanna go back my files are in the C: HD

---

### Post by bcbc on 2012-02-29
If you set Windows to boot Ubuntu by default and set the timeout to 0 (less than 6 can cause this as well), then it won't boot Windows. How to fix depends on what version of windows you are running, but nothing you do with the windows bootloader or grub will fix it.

Your C: files are likely under /host if you installed on the C: drive.

So what version of windows do you have?
Do you have a windows DVD or repair CD?

---

### Post by Gremlinzzz on 2012-02-29
Restore the Windows Boot Loader After an Ubuntu Update

Will your computer not boot into Windows after installing an update on your dual-boot or Wubi Ubuntu install?  Here’s how you can get your Windows boot loader back so you can easily get back to work in either OS.

[http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/](http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/)

:popcorn:might help i don't use wubi

---

### Post by Zaxfair on 2012-03-01
My Windows is 7 Ultimate 64 bits, yes I have set Wubi to installed on the C Hard Drive and yes I have it a windows DVD

But I don't won't to format my PC because all of my files are is this HD of  500 Gb, I have hope that I can fix this, but everething is not working .

And on this part 

After a few moments, it should detect your Windows installation and ask if you want to add it to the boot loader.  Enter *Y* to add it, then exit the command prompt and reboot your computer when you&#8217;re finished.
[http://www.howtogeek.com/wp-content/uploads/2010/10/sshot-2010-10-29-1-11-08-46.png](http://www.howtogeek.com/wp-content/uploads/2010/10/sshot-2010-10-29-1-11-08-46.png)
it says that on the scan have found no Windows system , like 0 Windows system.

---

