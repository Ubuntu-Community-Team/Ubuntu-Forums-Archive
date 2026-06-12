---
title: "Speed problem"
date: 2006-02-05
forum: General Help
---

### Post by snl on 2006-02-05
I have just installed Ubuntu 5.10 (dual boot with Windows XP). When I ran an example in a C program, it returned that it took ~17000-20000 ms. I previously had coLinux+gentoo installed on this laptop and with the same example, it took ~700-900 ms. 

Is it the problem with the clock or Ubuntu run slower? How I might be able to fix it?

Thanks.

---

### Post by Lord Illidan on 2006-02-05
Do you have dma enabled?

---

### Post by snl on 2006-02-05
Sorry, what is dma and how do I check if I have dma enable or not?

Thanks.

---

### Post by Lord Illidan on 2006-02-05
Run ```
sudo hdparm /dev/hd*
``` where * is the letter of your drive, eg..in my case it is

```
sudo hdparm /dev/hdd
```, could be different in yours

To enable it, run ```
sudo hdparm **-d1 **/dev/hd*
```

To view your drive letters, see the fstab file in /etc/fstab.

---

### Post by snl on 2006-02-05
sudo hdparm /dev/hda ```
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78126048, start = 0

```

So I think dma is already enable.

What should I do now?

Thanks.

---

### Post by dcstar on 2006-02-05
[QUOTE=snl]I have just installed Ubuntu 5.10 (dual boot with Windows XP). When I ran an example in a C program, it returned that it took ~17000-20000 ms. I previously had coLinux+gentoo installed on this laptop and with the same example, it took ~700-900 ms. 

Is it the problem with the clock or Ubuntu run slower? How I might be able to fix it?

Thanks.[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by snl on 2006-02-06
[QUOTE=dcstar][http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)[/QUOTE]
Thanks for your suggestion. I tried it but it still took ~17000 ms :( 

Could it be that the clock runs faster and hence the timing is wrong? How can I test it?

Thanks.

---

### Post by dcstar on 2006-02-06
[QUOTE=snl]Thanks for your suggestion. I tried it but it still took ~17000 ms :( 

Could it be that the clock runs faster and hence the timing is wrong? How can I test it?

Thanks.[/QUOTE]
Better to check if something else is using up the CPU:

Applications-System Tools-System Monitor

---

### Post by snl on 2006-02-06
[QUOTE=dcstar]Better to check if something else is using up the CPU:

Applications-System Tools-System Monitor[/QUOTE]
I checked the CPU usage before and it was less than 10%.

---

### Post by beerorkid on 2006-02-06
possibly the double clock speed problem?  Does my animated avitar look like it is going really fast?  then you have this issue.

[http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)

this drove me nuts for a week.

---

