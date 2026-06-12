---
title: "Boot into console only"
date: 2011-06-11
forum: General Help
---

### Post by CaptainMark on 2011-06-11
This is probaly the opposite of most posts about booting to terminal only. 

On 11.04 how would i go about making my machine boot into terminal mode by default and only booting a graphical interface when I type startx or some such similar command?
I tried the method at [this link]("http://ubuntuguide.net/boot-into-consolecommand-line-when-startup-ubuntu-9-10") but it hangs whilst displaying the message 'checking battery state' Im on a desktop so there is no battery present
Any advice would be appreciated.

Mark

---

### Post by Rubi1200 on 2011-06-12
Hi,
I would go back to the instructions you followed, but instead of editing the line to look like this:
> GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”

Make it this:
> GRUB_CMDLINE_LINUX_DEFAULT=”text”

Then run:
```
sudo update-grub
```

Reboot and see if it achieves what you want it to.

---

### Post by CaptainMark on 2011-06-12
it almost does, it boots to terminal thank you but 'startx' does not start unity i have to run 'unity --replace' to start that but that leaves a terminal open which will crash unity if closed

---

### Post by dancer_69 on 2011-06-12
You can start gdm with
sudo gdm service start
and login to Unity from there.

---

