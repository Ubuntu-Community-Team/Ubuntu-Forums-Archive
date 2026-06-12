---
title: "available at release?"
date: 2010-10-30
forum: General Help
---

### Post by matt-d3 on 2010-10-30
I have a Lenovo S10-3. There is a known issue with this laptop booting Ubuntu 10.10 and it is indicated that this problem will be fixed at release? Please forgive my ignorance but what does this mean? How will I know when this fix has been implemented?
 
Quote:
Lenovo S10-3 systems don't boot. Temporary workaround: add "intel_idle.max_cstate=0" as a kernel paremeter at boot (634702). A fix already exists that will be available only at release time (647071). 
 
I am hoping to run 10.10 on this Lenovo!
 
Thank you!

---

### Post by Ancanus on 2010-10-30
According to the bug report, "This bug was fixed in the package linux - 2.6.35-22.34"

I'm running 2.6.35-22.35, so the fix should be available from the repositories already.

---

### Post by matt-d3 on 2010-10-30
First off - thanks for the quick response! Awesome!
 
Are these fixes available in the current iso download or is this something that would need to be applied after? I downloaded the iso on 10/24 and it appears to have the problem.
 
Don't want to bombard you with a load of what may be dumb newbie questions but that's what you get for being helpful.
 
Side note - 10.04 runs fine.
 
Thanks!

---

### Post by Ancanus on 2010-10-30
I wouldn't really know if the ISO's carry the latest version. Judging from [http://packages.ubuntu.com/search?keywords=linux-image-generic](http://packages.ubuntu.com/search?keywords=linux-image-generic) and my personal insight, I would vote no.

Never tried it personally, but maybe the daily build ISO does:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by matt-d3 on 2010-10-31
Thanks Ancanus! 
I looked at the daily builds but they have a modification date of 10/7 which is the same modification date I see in the iso I dowloaded. I guess this would suggest that these aren't updated every day?
 
I have entered boot paramaters at the screen where you are presented with the options -
Try without installing etc. but the boot process on my Lenovo doesn't even make it that far before it hangs. 
 
I've setup USB sticks with unetbootin and universal USB intaller with the same result. I like the universal usb installer because it offers persitance as an option with ubuntu.
 
I'll see if I can find the file on the usb stick that needs to be modified and add "intel_idle.max_cstate=0" to the kernel parameters.

---

### Post by 3rdalbum on 2010-11-01
Install Ubuntu 10.04 and then dist-upgrade it to 10.10. Then you will have the latest packages.

---

