---
title: "Error starting Gnome"
date: 2006-04-10
forum: General Help
---

### Post by bromleyi on 2006-04-10
Hi

I have problem logging on to Gnome. I get the message about the sessions lasted less than 10 seconds.
I have read all the messages on this forum about the permissions of .ICEauthority and .Xautority. They are both owned by me, and even deleteing them doesn't work.
Even if I start up as root and run startx I still can't get in. Its hard to post error messages as I have to use another PC to get on the internet.
It was all working OK until I rebooted.

Please any help would be helpful

Ian

---

### Post by krismatth3 on 2006-04-10
Can you post the contents of your ~/.xinitrc ?

---

### Post by bromleyi on 2006-04-10
I dont have a ~/.xinitrc file in my home directory

---

### Post by krismatth3 on 2006-04-10
Can you list the files in your home directory? "ls -a".. (Don't list anything you don't want other people to see.)

---

### Post by bromleyi on 2006-04-10
I fixed it.

I changed my /etc/hosts file earlier in the day, but for some reason the file got corupted. After I fixed the file I was able to login to Gnome.

I very strange problem, but I hope it can help someone.


Thanks for your help

Ian

---

