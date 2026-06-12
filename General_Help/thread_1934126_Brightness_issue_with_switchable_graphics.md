---
title: "Brightness issue with switchable graphics?"
date: 2012-03-01
forum: General Help
---

### Post by Imagery on 2012-03-01
Hi everyone,

I have a HP notebook with ATI switchable graphics, and I installed the latest ATI driver off their site, which works fine.

But I do have the brightness issue where at login, my display is dark and I have to manually set the brightness at each restart.

I did try and edit the Rc.local file, as noted by others, where you set the brightness to 5 or 10:  

"echo 10 > /sys/class/backlight/acpi_video0/brightness"

When I try and save it, I get this message in Terminal:

(gedit:3801): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


So far nothing is working to set the brightness to max at startup. Even used a Python script I found with no luck.

Here's my lspci | grep VGA listing:


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]


Sorry for the long post, anyone have any ideas? I assume this is realted to switcable graphics.

Thank you

---

### Post by Ms. Daisy on 2012-03-03
I have the same problem on a toshiba laptop. I never found a solution, hopefully someone else did.

You didn't say but I assume you're running 11.10?

---

### Post by Imagery on 2012-03-03
Exactly Ms. Daisy, I'm using 11.10. I have the feeling it doesn't matter so much on what version of Ubuntu we are using.

I was able to fix the problem when I didn't have ATI drivers installed with switchable graphics enabled. 

I think the issue is that we now have 2 video displays enabled and we just have to set the settings for each adapter. I just don't know how.  Sucks.

I'm hoping like you are that there's a solution.

---

