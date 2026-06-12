---
title: "Ubuntu doesn't boot"
date: 2010-11-14
forum: General Help
---

### Post by Dominis on 2010-11-14
This is the first time I've used Linux so I don't know how to begin to solve my issue.

My Ubuntu install doesn't boot it. After showing the GRUB options it goes to a screen with a blinking cursor that doesn't accept input forever. I've let it run for an hour with no boot.

Note: I successfully installed Ubuntu. I got it to boot but only after unplugging my DVD drive, but that isn't really a long-term solution. I've tried an install from my flash drive twice and then burned a DVD all with the same issue.

I'm using 64 bit Ubuntu.

After selecting my Ubuntu install if I spam enter it will boot saying '[%f] Too many connections'. %f is the up-time from what I can tell.

---

### Post by Rubi1200 on 2010-11-14
Hi and welcome to the forums :)

What graphics card do you have and how much RAM is available?

Also, what version of Ubuntu are we talking about?

---

### Post by Dominis on 2010-11-14
I have a GeForce 470 GTX (1280 MB) w/ 12 GB of RAM.

Ubuntu 10.10 64 bit

---

### Post by Rubi1200 on 2010-11-15
Try booting using the nomodeset parameter:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Dominis on 2010-11-18
This didn't work.

I can fix the issue by unplugging my CD drive....

---

### Post by kwhatcher on 2010-11-18
What kind of CD drive do you have? PATA, SATA? Make and Model?

---

### Post by Dominis on 2010-11-21
LITE-ON PATA SOWH-1693S Fairly old ~June 2005

---

### Post by Quackers on 2010-11-21
Please boot from the Live cd and select "try ubuntu" then go to the site below and download the boot script to your DESKTOP then open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

