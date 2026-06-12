---
title: "how to make a &quot;boot repair&quot;"
date: 2012-03-15
forum: General Help
---

### Post by alenn on 2012-03-15
Hi

I'm using ubuntu 11.04. I tried to install GNOME 3 but it fails, just after restart I couldn't load system. I only see message "Checking battery state..." and it stay forever. Is there any way for restoring system except of reinstalling it

---

### Post by alenn on 2012-03-15
anyone? I hope you understand my previous post

---

### Post by SystemsGO on 2012-03-15
> **alenn said:**
> anyone? I hope you understand my previous post

You need your LIVE CD, or LIVE USB stick. Once you have that, go ahead and open the terminal and type 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair

That should work.

---

### Post by alenn on 2012-03-15
> **SystemsGO said:**
> You need your LIVE CD, or LIVE USB stick. Once you have that, go ahead and open the terminal and type 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair

That should work.

tried it, but not working, I have the same message, nothing changed

---

### Post by kurja on 2012-03-15
do you mean that the same thing is happening when trying to boot from the live cd, or that you successfully ran the commands but it didn't help?

---

### Post by alenn on 2012-03-15
live cd is ok, but after those commands nothing changed

---

