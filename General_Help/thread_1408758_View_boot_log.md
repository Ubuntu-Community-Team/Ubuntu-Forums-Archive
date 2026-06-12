---
title: "View boot log"
date: 2010-02-16
forum: General Help
---

### Post by cambunctious on 2010-02-16
Every time I boot into Linux, immediately after selecting it in GRUB2.  A message appears on the screen for a second then continues with normal startup.  I think this started happening after the last ubuntu image update or whatever but I'm not sure.  I suppose there is no real problem but I'm kinda OCD so I want to know what it says and if there's an error.  Is there a log somewhere I can view and perhaps post in on this thread?  Thanks in advance!

---

### Post by byStanderone on 2010-02-16
...try to catch that message by hitting your 'pause key' and 'esc key' to resume the boot process.

---

### Post by cambunctious on 2010-02-16
Ha!  I thought that Pause button was some kind of joke!  Here's the message.

*vga=786 is deprecated.  Use set gfxpayload=640x480x24, 640x480 before linux command instead.*

I'm sure this is from messing with the resolution and color depth in StartUp-Manager.  I changed them back to the minimum settings and got...

*vga=**769** is deprecated.  Use set gfxpayload=640x480x**8**, 640x480 before linux command instead.*

I googled the problem and [found this bug report]("https://bugs.launchpad.net/startup-manager/+bug/483262") but the solution isn't clear and I'm scared to try it.

Also, I was still hoping I could learn where to find logs if possible.

---

### Post by KayakJim on 2010-02-16
Run "dmesg" to view the boot log.

---

### Post by MinimalBin on 2010-02-16
Log files can be found in /var/log. Have you actually tried to edit the kernel line and replace the parameters as suggested ?

---

### Post by cambunctious on 2010-02-16
Thank you both for responding.

> **MinimalBin said:**
> Have you actually tried to edit the kernel line and replace the parameters as suggested ?

:-k
Uhh...Do you mean in the bug report I linked to?  I didn't fully understand the solution on that page.  Do you think you could reword it in more noobular terms?

---

### Post by MinimalBin on 2010-02-17
Read the [Wiki]("https://help.ubuntu.com/community/BootOptions") :)

---

### Post by byStanderone on 2010-02-21
...ALWAYS REMEMBER TO UPDATE YOUR GRUB:  sudo udate-grub (specially after any alteration, manual or guiwise, in any grug2 configuration files)

---

### Post by razedafear on 2011-04-23
hey i am facing the same problem  with vga=786, m a newbie to ubuntu..can uplz tel me how to fix it. i mean the grub files n all...

---

### Post by Geoffke on 2011-07-29
1. Open up a terminal (or press ctrl + alt + t)
2. Type in: sudo gedit /etc/default/grub
3. Type in your password (if needed)
4. Look for the following line:

GRUB_CMDLINE_LINUX=" vga=769"

5. Change it to:

GRUB_CMDLINE_LINUX=" gfxpayload=true gfxpayload=640x480x8"

6. Save the file
7. Go back to your terminal and type in: update-grub.

Thanks to kevin @ [http://www.helpmesolve.it/answers/450/vga769+is+deprecated.html](http://www.helpmesolve.it/answers/450/vga769+is+deprecated.html)

---

