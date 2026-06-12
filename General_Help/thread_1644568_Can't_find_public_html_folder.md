---
title: "Can't find public_html folder"
date: 2010-12-13
forum: General Help
---

### Post by Shinonuma on 2010-12-13
Hi,


I cant find the public_html folder on ubuntu. I thought it was installed by default on linux but I can't find it.

---

### Post by wojox on 2010-12-13
Everything should be in /var/www/ in apache and linux. If you want a public_html you could create one in your /home/userName/ directory and activate or edit userdir.

Personally I just stick with /var/www since I'm the only user on my server.

---

### Post by Shinonuma on 2010-12-13
Oh ok, and how do you active userdir? I'm new to this.

---

### Post by Shinonuma on 2010-12-13
Do you have a tutorial or something?

---

### Post by wojox on 2010-12-14
> **Shinonuma said:**
> Do you have a tutorial or something?

Here's an easier way [Create a symbolic link.]("http://blog.damontimm.com/how-to-redirect-apaches-default-www-or-public_html-folder-to-a-directory-in-your-home-folder/")

---

### Post by David52 on 2010-12-14
[https://help.ubuntu.com/10.10/index.html](https://help.ubuntu.com/10.10/index.html)
If u are new to this system, here is where you should read before really digging into Ubuntu. It sure did help me alot when I started with 10.4
Check it out
david52

---

### Post by Verbeck on 2010-12-14
if you want the document root to be in your home folder, then run
```
gksu gedit /etc/apache2/sites-available/default
```and replace the two **/var/www **with **/home/username/public_html**
and then, restart apache
```
sudo /etc/init.d/apache2 restart
```**you might need to adjust the permissions of your home folder if you want to do that ^

---

