---
title: "LXDE problem"
date: 2011-02-24
forum: General Help
---

### Post by L Style on 2011-02-24
I'm new to ubuntu. I'm using ubuntu 10.04. Now I moved to LXDE desktop from gnome. But now I can't mount my hard disk partition. When I click On my hard disk partition It ask My password. When I typed my password It displayed Access denied. How can I solve this. Please help me:confused::confused:

---

### Post by zenwalker on 2011-02-24
Are entering your own logged in user account password correctly? Take care about case as well. 

I guess your user account may not be under the mount users group. Log in as root account and add urs into that.

---

### Post by L Style on 2011-02-24
> **zenwalker said:**
> Are entering your own logged in user account password correctly? Take care about case as well. 

I guess your user account may not be under the mount users group. Log in as root account and add urs into that.

yeah I logged in my user account. how can I logged as root & How to add user into mount user group. please help me

---

### Post by zenwalker on 2011-02-24
First, have you set the passwrod for the root account?
If not, do that first set a root password. Do this in terminal

sudo passwd
<Enter passwd>

To add user to a group, this should help [http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

---

### Post by L Style on 2011-02-24
> **zenwalker said:**
> First, have you set the passwrod for the root account?
If not, do that first set a root password. Do this in terminal

sudo passwd
<Enter passwd>

To add user to a group, this should help [http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

I tried but It's not work, Is there any solution can you help me

---

