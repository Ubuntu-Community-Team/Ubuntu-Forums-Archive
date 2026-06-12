---
title: "Setting up a Ubuntu Mirror"
date: 2006-03-31
forum: General Help
---

### Post by kcbanner on 2006-03-31
Hi,

I want to mirror Ubuntu, but only the x86 portion. I know i need to use rsync...but could someone explain in full detail how to go about this? I have used linux quite a bit...just never done this :P

I want to mirror Ubuntu to have a speedy local cache and to help the community!

Thanks,
kcbanner

---

### Post by joft on 2006-03-31
Hi,

just another thought/tool to create a mirror of any debian repository:

apt-mirror

I use it for my mirrors and it's really simply. The configuration file has a similar syntax compared to sources.list .

---

### Post by kcbanner on 2006-03-31
Awesome! Now how do I set it up to check every few hours for updates? Using cron...but how?

---

### Post by kcbanner on 2006-03-31
bump

---

### Post by nanotube on 2006-03-31
make a cron job (by adding a line to /etc/crontab file)
and make it run the command "/usr/bin/apt-get update" or something. 
to learn about cron jobs, run "man cron" and do some reading. :)

---

