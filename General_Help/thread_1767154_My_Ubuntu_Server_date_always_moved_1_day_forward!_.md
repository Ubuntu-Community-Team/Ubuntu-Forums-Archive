---
title: "My Ubuntu Server date always moved 1 day forward! Please help."
date: 2011-05-25
forum: General Help
---

### Post by cinlung on 2011-05-25
Dear all experts

I installed the Ubuntu 10.04 LTS Server version with no GUI. I have set my timezone to be ASIA/JAKARTA. For some reason, my server date always moved 1 day at around 6 pm.

I never installed any date specific software. Just java, tomcat, and mysql server. No Time Server connection and the ubuntu server is only accessible locally, no internet access.

Every night I need to do "date -s" to set the date and time to the correct time. At first I thought my server bios battery was out, but if it was out, why do the time always move forward by 1 day?

For example, this morning the date is still 25 of May here in Indonesia. At 6 pm, it changed to 26 of May. Other thing that I am confused is that every time I check the date, the date always had WIT on it like this: Wed May 25 20:01:06 **WIT **2011 (this is after I performed date -s)

Does that mean Waktu Indonesia Timur (Indonesian Eastern Time), is that the time zone? If so, Jakarta is supposed to be WIB (Indonesian Western Time). How can I fix this?

Thank you
Rendra

---

### Post by hwttdz on 2011-05-25
Try running "sudo dpkg-reconfigure tzdata" and setting your time zone to the correct one and see if that at least fixes the time zone issue.  

Also check if 1) you're using UTC time (recommended) and 2) that it's set correctly in the bios
more info here: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

