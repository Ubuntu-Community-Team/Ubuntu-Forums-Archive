---
title: "Changing resolution"
date: 2011-05-14
forum: General Help
---

### Post by linux_dream on 2011-05-14
I'm having a very hard time with the new Ubuntu (I can't make Unity to work).

My default resolution is 1360x768 and I'm currently under a 640x480 resolution.  I'd like to get back to 1360x768 but I don't know how.
My graphic card is a Nvidia 7300 GS.  I've modified the /etc/X11/xorg.conf, so that instead of the line "nvidia", I have "nv" otherwise Ubuntu freezes.

How can I get back to a normal resolution?  All messed up when I typed "sudo nvidia-xconfig".  It modifed the xorg.conf file and totally messed up my resolution.

Thanks for any help.

---

### Post by ubume2 on 2011-05-14
[s]Did you try Applications--System Settings--Monitors to make the changes?[/s]

Edit: Sorry that was for Ubuntu 11.04. Try System--Preferences--Monitors.

---

### Post by linux_dream on 2011-05-14
> **ubume2 said:**
> Did you try Applications--System Settings--Monitors to make the changes?
Do you mean System, Preference, Monitors?  If so, yes.  I have no other choice than 640x480.
However I know my monitor can support 1360x768 since it was like that before I've messed up.

---

### Post by ubume2 on 2011-05-14
Yes, I just edited my post.
Sorry, I am out of ideas. Probably could reinstall some x apps. There are some nvidia listings in synaptic package manager that you could try reinstalling, but I really don't know what I am doing in that area. Hopefully somebody else with more expertise will respond.

---

### Post by linux_dream on 2011-05-14
Problem solved.  I changed (downgrated) my drivers to fix Unity problem.  Resolution came back to normal.

---

