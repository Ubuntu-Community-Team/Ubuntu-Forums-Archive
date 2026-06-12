---
title: "apache help !!!"
date: 2011-03-08
forum: General Help
---

### Post by khaj_vah on 2011-03-08
Hi everyone 
Well, i am a new user of ubuntu and also new web designer.I have installed apache2 server and the network name is "localhost" by default so here is my question how can i change it to a name that i want and also how can i change the default domain name to a domain name that i have registered so that everyone can reach my website...
Thank for help

---

### Post by vivek.pandey on 2011-03-08
hope this helps
sudo vi /etc/apache2/sites-available/default


instead of localhost..change to what you want
save it :wq

---

### Post by new_tolinux on 2011-03-08
Assuming that neo_aryan is correct, you said that you are a new user. That means you probably prefer nano over vi as an editor.

The command for that is:
sudo nano /etc/apache2/sites-available/default

---

### Post by khaj_vah on 2011-03-09
Thanks alot  and u were right nano is better for me :)

---

