---
title: "File copy to USB too fast, hangs at the end"
date: 2012-07-25
forum: General Help
---

### Post by clappboard on 2012-07-25
Hello,
How would I go about enabling the **sync** or **flush** option for automounted devices?  The copy speed when copying a 700mb file to a USB drive is reported as 70mb/s by the nautilus copy dialog, but the progress hangs at the end of the file and refuses to go any further.  I'd like to see real-time copying.  I'm currently running precise.
Thanks.

---

### Post by dcstar on 2012-07-27
> **clappboard said:**
> Hello,
How would I go about enabling the **sync** or **flush** option for automounted devices?  The copy speed when copying a 700mb file to a USB drive is reported as 70mb/s by the nautilus copy dialog, but the progress hangs at the end of the file and refuses to go any further.  I'd like to see real-time copying.  I'm currently running precise.
Thanks.

It does **not** "hang". The data is initially copied (quickly) into the RAM buffer and the buffer is then written (slowly) to the actual device.

You have to **wait** for the actual write to complete.

---

### Post by clappboard on 2012-07-27
> **dcstar said:**
> It does **not** "hang". The data is initially copied (quickly) into the RAM buffer and the buffer is then written (slowly) to the actual device.

You have to **wait** for the actual write to complete.
Yes, I'm aware of that.  I can issue the sync command to force all the cached data to be written to the device as well.  But is there a flag I can set that will stop the data being written to cache en masse and instead be written to the device, so that the nautilus progress bar will be accurate?  I'm trying to set up my computer so that someone who doesn't know this won't think the copy is done and unplug their flash drive.

---

### Post by 14quartz on 2012-07-27
I'm also facing the same problem. Friends are making fun of this.
And this is not in case of windows.

---

### Post by dcstar on 2012-07-27
> **clappboard said:**
> Yes, I'm aware of that.  I can issue the sync command to force all the cached data to be written to the device as well.  But is there a flag I can set that will stop the data being written to cache en masse and instead be written to the device, so that the nautilus progress bar will be accurate?  I'm trying to set up my computer so that someone who doesn't know this won't think the copy is done and unplug their flash drive.

[http://askubuntu.com/questions/61448/how-to-configure-to-record-data-to-pendrive-instantly](http://askubuntu.com/questions/61448/how-to-configure-to-record-data-to-pendrive-instantly)

---

