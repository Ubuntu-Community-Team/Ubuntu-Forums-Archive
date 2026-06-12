---
title: "cron jobs across multiple machines and PHP"
date: 2011-01-06
forum: General Help
---

### Post by cbarron on 2011-01-06
Ok I had this crazy idea to to run a cron job to download my email logs to my laptop. But the question is HOW? Im not sure how to write the php script for the cron job. the file is on "computer A" and the file is setup to chmod I just need to know how to write the php to "access" the other computer and then download the file to a certain file on my laptop.
Any help would be great Thanks in advance.

---

### Post by Cheesehead on 2011-01-06
Well, normally such control would be exercised through ssh, so I recommed starting there. [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by cbarron on 2011-01-13
Actually ssh is the hard way to do it. A small bash script and then setup a cron job...and it works great. but I still have questions about cron its self

---

### Post by matt_symes on 2011-01-13
Hi

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) ?

Kind regards

---

