---
title: "Firestarter: Insufficient privileges"
date: 2006-04-05
forum: General Help
---

### Post by Prism on 2006-04-05
Hi there,

I've installed firestarter step by step by [this guide]("http://doc.gwos.org/index.php/Firerstarter_Guide"), but when I boot my computer and GNOME starts, I see a message saying "Insufficient privileges: you must have root privileges to use Firestarter.

How can I solve this problem?

Thanks in advance. :)

---

### Post by tagg3rx on 2006-04-05
Did you do the very 1st steps listed?

Giving the user permission to launch Firestarter without the root password

Open a terminal and type:
Code:

sudo gedit /etc/sudoers


Add this line to the bottom:
File:/etc/sudoers

**username** ALL=NOPASSWD:/usr/sbin/firestarter

Save the file and close the terminal.

Note: **Make sure username is your actual username**

---

### Post by Prism on 2006-04-05
Yes, I added this to my sudoers file:
tomer ALL=NOPASSWD:/usr/sbin/firestarter

---

### Post by Prism on 2006-04-06
Anyone please?

---

