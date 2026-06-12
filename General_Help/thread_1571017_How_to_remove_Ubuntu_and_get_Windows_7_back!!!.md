---
title: "How to remove Ubuntu and get Windows 7 back!!!?"
date: 2010-09-09
forum: General Help
---

### Post by Marik123 on 2010-09-09
I installed Ubuntu a few weeks ago side by side on a computer that already had windows 7 installed. But after installation I found that no GRUB menu appeared at startup. I tried to reinstall a fresh copy of windows 7 in a desperate attempt to get it back but that didn't work since this desktop that I am using does not show any BIOS screen when turned on. Not only that but it also does not automatically boot from cd. I started a thread about that here: [http://newyork.ubuntuforums.org/showthread.php?p=9818596](http://newyork.ubuntuforums.org/showthread.php?p=9818596) but none of the suggestions given have worked.

I know windows 7 exists on the machine. When I go to Places >> Computer I see this:

[IMG]http://i52.tinypic.com/o9n97l.png[/IMG]

When I click on the 3rd disk from the left I see the contents of my old Windows 7 installation:

[IMG]http://i51.tinypic.com/149tx15.png[/IMG]

Can someone please tell me how to get windows 7 back. I can't reinstall it due to the aforementioned issue and I also tried getting grub by following the instructions on the web and it all failed.

---

### Post by drdos2006 on 2010-09-09
Windows 7 and Bill Gates takes over control of your hard drive when you install Windows 7. Procedure is to install Windows 7 first, then install Ubuntu where Ubuntu takes control of Windows 7.

regards

---

### Post by mohansathish on 2010-09-09
+1 drdos2006

And one more advice is, try installing ubuntu separately and not inside windows using wubi.

---

### Post by mendhak on 2010-09-09
Have you ever gotten the BIOS screen in the past? If yes - you should probably attempt a reset on it - take the CMOS battery out for a minute, put it back, then start the machine.  

Have you also tried spamming F8 as the machine starts up, some BIOSes will give you an option screen where you can choose the boot device.

---

### Post by Saprissa on 2010-09-09
Boot into Ubuntu and open a terminal.

type:

```
sudo update-grub
```

You should see a message "generating grub.cfg".

If you get an error message saying grub is not installed, install it with:

```
sudo apt-get install grub2
```

Then try the update-grub command above. If all goes well, grub will find both your Ubuntu and Windows 7 installations and then you won't need to remove Ubuntu.

---

### Post by Mark Phelps on 2010-09-09
If your question deals with restoring dual-boot features, this is the right place to be.  

If your question deals with restoring Win7 -- then go to sevenforums.com -- a Windows 7 forum, where there are tutorials about doing what you want to do.

---

### Post by Aergan on 2010-09-09
I like the 7loader.TAG file.

I would suggest running your genuine Windows 7 DVD and running the repair feature to restore the Windows 7 boot loader priority, but it will break your activation.

---

