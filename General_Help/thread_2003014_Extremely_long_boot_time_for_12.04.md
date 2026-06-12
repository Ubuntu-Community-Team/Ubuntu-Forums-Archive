---
title: "Extremely long boot time for 12.04"
date: 2012-06-13
forum: General Help
---

### Post by Malzkaffee on 2012-06-13
Hi, folks!

I just installed Ubuntu 12.04 on my Toshiba Laptop and am quite satisfied with nearly all the stuff delivered with it - except the boot time.

As I am quite a beginner, I googled around and then installed bootchart as a starting point in my hunt for seconds. 

But as a rookie I'm unfortunatly not able to interprete the chart - not to speak of any conclusions to draw from or actions to take.

I've enclosed the bootchart graph. Could somebody give me a hint where the problem(s) lie and how to solve them?

Thank you very much in advance!

Regards,
Thomas

---

### Post by oldfred on 2012-06-13
How long is it? My 6 year old  Toshiba laptop is about a minute. Amount of RAM can make a difference.

Boot Charts attached are always too small to review. But I never learned how to review either.:) But do have a link.

[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

I look at log files and look for long times between tasks, a task repeating & then failing, or error messages.
Look in Log File Viewer and dmesg or syslog.

---

### Post by Malzkaffee on 2012-06-14
Hi!
 
Well, after doing several reboots and marveling at lots of graphs I stated that my Toshiba L755-10U needs approximatly 1 minute to show up login screen. 
 
With 4 Intel i5 processors, 4GB of RAM and 64bit the machine should not be considered as an old frump. 
 
Win7 definetively booted faster - even packed with loads of unnecessary Toshiba-Software. 
 
But as there are other reasons for me to switch from Win to Ubuntu, it seems to me that there's no way as to dig deeper into all the programs that are started with the OS.
 
Anyway, I' ll have a look at your reference - thank's a lot for that.
 
Regards,
Thomas

---

