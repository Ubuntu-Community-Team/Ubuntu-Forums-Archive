---
title: "Black Screen  stays too long before the Ubuntu logo"
date: 2010-12-31
forum: General Help
---

### Post by Nuxala on 2010-12-31
I've installed Ubuntu on another PC and most things are great except fore the black screen that you get when you start the PC (just before the Ubuntu Logo). It stays black for 20 seconds. Is there something I can do to make it shorter like on my other PC.

---

### Post by nitro_n2o on 2010-12-31
hmm... each computer is different (the motherboard, the chip .. ), 20 seconds is not a lot of time. I once had a computer that would have the motherboard screen lasting for minutes

---

### Post by IWantFroyo on 2010-12-31
It depends on the computer, and how you're using it. I don't really think there's any way to fix this without making the boot longer though. My laptop doesn't even have a splash screen after I dual booted it with Windows.

---

### Post by Nuxala on 2010-12-31
> hmm... each computer is different (the motherboard, the chip .. ), 20  seconds is not a lot of time. I once had a computer that would have the  motherboard screen lasting for minutes 	

But it was faster on Windows XP and that's why I thought the problem wasn't the PC.

---

### Post by kzenthil on 2011-06-08
I know this is old post, but I face the same thing. 

Mine is a brand new Lenovo T410. I setup dual boot, XP & Ubuntu 10.04. I updated Ubuntu and restarted it. It stays in black screen for a very long time. I tried force rebooting couple times, but still the same issue. 

Should I re-install Ubuntu ? Any other solution ?

---

### Post by pizzaia on 2011-06-08
Mine does it too, and I have a Core i7 and a GTX 560. I think it's normal.

---

### Post by kzenthil on 2011-06-08
But, How long does it take to come up ? 
Mine doesn't seem to boot at all. I waited for more than 15 mins.

---

### Post by hatalar205 on 2011-06-08
Did you try to update the Bios. Before updating the Bios my Toshiba was waiting too long. Look at your machines support page for more detailed information. 
By the way of course don't try to update through Ubuntu. **Unfortunately** we still need Windows sometimes.

---

### Post by Mark Phelps on 2011-06-08
As you may know, there's a LOT going on inside your PC between the time you power on and get a working desktop -- and how long that takes depends on a number of factors, including (but not limited to), the following:
1) BIOS POST settings (memory checking, for example)
2) Loading the operating system (boot loader time)
3) Enumerating the devices through bus checks and loading the corresponding drivers
4) Bringing up the proper login screen.

The BIOS settings will take the same time duration regardless of the OS because they happen long before any OS is loaded.  So, nothing you do to Ubuntu is going to make that part any faster.

The rest of the stuff is OS-dependent and, since the OSs are very different, I'm not surprised that the timeframes are different, too.

If you simply don't like a black screen, there are generally options you can set in your BIOS to either (1) display a logo screen, or (2) display the POST messages.

Actually, I would suggest you do the second, and then, time the duration from the last POST message to the OS login screen appearing. That will tell you how long each OS is taking to initialize.

---

### Post by jramshu on 2011-06-08
I think the reason you don't "see" this in windows is because it shows a splash screen while it's waiting for bios to get everything ready.

I actually had to add a delay to grub(GRUB_CMDLINE_LINUX="rootdelay=90") on an old desktop running a server to stop it from dropping into busybox. It takes the old bios around 90secs to get the hard drive ready. Anything less that that and I get an error about the hard drive. I think it was something along the lines of Error UUID XXXXXXXXX not found, check root delay. Can't remember exactly how the error was written.

---

