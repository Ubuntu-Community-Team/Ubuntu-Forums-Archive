---
title: "time setting !!"
date: 2011-08-28
forum: General Help
---

### Post by gringo8217 on 2011-08-28
hi 
   guys 
           every time i correct the time to the proper time it changes back to an hour behind i have set it correctly to london (gmt ) or put my location etc and set it but it keeps  re-setting to an hour behind the correct time !! anybody any idea or the correct fix !!

---

### Post by dino99 on 2011-08-28
is network time activated ?

---

### Post by gringo8217 on 2011-08-28
sorry , but could you explain or direct me by wot you mean by network time activated ? plz

---

### Post by beew on 2011-08-28
Right click the time display on the upper right of the top panel (assuming you are using Unity),  click time and place settings from the drop down, go to the time and date tab, unlock and check Automatically From the Internet. This should have been set up when you installed the system.

I think you need to do the same with Windows, I have an xp partition and it is always out of the sync for a few hours because it has difficulty connecting to the internet (wifi keeps dropping dead)

---

### Post by gringo8217 on 2011-08-28
thanks that may explain the the reason as at times my wifi connects and  then disconnects at the odd time   then re -connects !!

---

### Post by tredegar on 2011-08-28
Are you dual-booting with windows?

When your computer boots, the OS sets the OS's time from the CMOS HW clock.

Windows expects the HW clock to be set to *local time* (Ie British Summer Time right now).

But linux expects the HW clock to be set to **UTC**, so if it is set to local time, your time will indeed be an hour out, during the summer, but correct during the winter (because UTC *almost* = GMT).

There's information about how to fix this [here]("https://help.ubuntu.com/community/UbuntuTime") but basically, if you want linux to see the HW clock as local time (like win does) you need to edit **/etc/default/rcS ** and set **UTC=no**.

Then reboot.

---

### Post by gringo8217 on 2011-08-28
thanks that explained it  !!

---

