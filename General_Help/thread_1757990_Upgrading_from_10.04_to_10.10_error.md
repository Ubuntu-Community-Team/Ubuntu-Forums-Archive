---
title: "Upgrading from 10.04 to 10.10 error"
date: 2011-05-14
forum: General Help
---

### Post by md_md_md on 2011-05-14
Hi guys, 
I wanted to upgrade to 11.04 finally from 10.10, but before that I had to upgrade from 10.04 to 10.10 of course. 

But a problem occurred when I was updating. I accidentally my power button on the laptop, which forced shut down during upgrade from 10.04 to 10.10. Which unfortunately has let to a lot of problems. When I restart now its showing a lot of gibberish and says that battery module not installed and it doesn't just say it, it flashes and flickers. 

I tried from then to install 11.04 directly using a flaskdrive, this worked as I chose to install it side by side to avoid losing any files. But however once I was there I couldn't access my files to take a backup from it. 

Thinking it would be a good idea to reinstall windows xp and try to access those files have also not worked! 

I just want to get back my files first! and then reinstall 11.04. 

What are my ways forward? Thanks

---

### Post by jerome1232 on 2011-05-14
First what does your disk look like right now? Which partition has your data which needs to be backed up?

Why couldn't you access your files? Have you tried clicking places, then clicking the disk you want to access?

Can you post the output of fdisk?

```
sudo fdisk -l
```

---

### Post by linuxuser12345 on 2011-05-14
If I were you, I would just do a clean install. This is the fastest and easiest way to go.

---

