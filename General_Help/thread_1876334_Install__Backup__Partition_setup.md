---
title: "Install / Backup / Partition setup"
date: 2011-11-06
forum: General Help
---

### Post by lonewolf69 on 2011-11-06
I am looking for the best way to install linux so that if reinstalling has the least effect.  I was thinking that putting the /etc and /bin directories in a separate partition.  Someone told me that you can easily put a couple folders into a small partition and everything else resides on the main.  

I have searched the web for best linux install practices and found a giant mess of everything but what I was looking for.  I am fairly new and would like to learn more about this so that if I reinstall my files and programs are not gone.  

Also, what folders do I need to backup?  I have plenty of space.

On another topic, I read that you can setup all your /usr directory on a single machine so that all users on a network access the same /usr programs.  Unfortunately the article did not go into specifics and practices on doing this.  Does anyone know of an article that outlines how to set this up?

Thanks.
K

---

### Post by dcstar on 2011-11-06
> **lonewolf69 said:**
> I am looking for the best way to install linux so that if reinstalling has the least effect.  I was thinking that putting the /etc and /bin directories in a separate partition.
..........

Essentially pointless.

Set up a separate /home partition and you can reinstall as many times as you like and not affect your user files.

Save your installed programs list with Synaptic and you can use the file to reinstall all of those packages after a fresh reinstall.

Keep a copy of /etc for the same purpose (if you really think that you need the configuration stuff). Reinstalling will wipe any separate partition anyway so the is a waste of time.

People over-complicate things that are basically not worthy of the time and effort in relation to any benefits.

---

