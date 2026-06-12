---
title: "Wakeup on wakealarm not working in 10.04!"
date: 2010-06-26
forum: General Help
---

### Post by edannert on 2010-06-26
Ok, just rebuilt my media centre, upgraded to 10.04 mythbuntu and can't get the wakealarm working. After a log of investigating and analysing I narrowed it down to the following, but wasn't able to find anyone that has similar issues, hence the post here:

My motherboard (Asus M4A785T-M with latest bios) can be set to wakeup at a predetermined time, but surprisingly I can't set a date in the bios. I only have the options of setting everyday or a number of days from now plus obviously the wakeup time.

When I boot into linux and analyse these settings using cat /proc/driver/htc the alrm_time is shown correctly but the alrm_date is set to "****-**-**". So far so good and when making the setting in the bios the machine boots up at the correct time.

Now, when I try the same with using the wakealarm function:
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"

The time AND date is displaved correctly after running "cat /proc/driver/rtc", but the machine does not wakeup.

Now, I through if I could only set the time and not the date, i.e. emulating what the BIOS does when I set the wakeup there it should work, but
a) I don't know how to do that
b) I am still puzzled that I can't get it working with wakealarm

Anyone any suggestions/ideas? Any help appreciated, since I am close to solve this by replacing the mobo... not the best option :-(

---

