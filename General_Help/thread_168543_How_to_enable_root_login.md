---
title: "How to enable root login?"
date: 2006-04-30
forum: General Help
---

### Post by OMJD on 2006-04-30
Not being able to login to GNOME using the root account is extremely annoying considering I am currently unable to access it via SSH and I need to put some files in the www directory. I can't be bothered with having to su to root all the time via terminal, that's purely a pain in the a**.

Any ideas on how to enable direct root login? 

Thank you. :)

---

### Post by bluevoodoo1 on 2006-04-30
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Here you are, but logging in as root is not recommended.

---

### Post by rvergara on 2006-04-30
just create a launcher with this command:

gksudo nautilus

That will do it.

Ramiro

---

### Post by billeman on 2006-05-01
You can also do this:

System -> Administration -> Login Screen Setup

Go to the "Security" tab.

Under Options:
Allow root to login with GDM (Checked)

---

### Post by Anilkumar on 2006-05-01
Just go to System ->Adminstration->Login Screen Setup-> press Security Tab->Enable Root Login gdm.That's it

Note:At the time of login u need to type root for username .

---

