---
title: "Removing pam-face authentication"
date: 2010-10-01
forum: General Help
---

### Post by rasmus91 on 2010-10-01
Hi there.

I'm trying to remove pam-face authentication, but i am having a hard time doing so, i installed it using [this guide]("http://www.omgubuntu.co.uk/2010/09/login-to-ubuntu-using-your-face/")

and awesome as it is, i prefer my good old password.

so, does any one know how i can uninstall it?

thanks.

---

### Post by luvshines on 2010-10-01
How are you trying to uninstall it ??

Can you cat and paste the output of /etc/pam.d/gdm and /etc/pam.d/gnome-screensaver files here ?

If you'll look further down that link into the comments

The comments by 'jmastorga' and 'bhm' explain the removal procedure.

Warning: Be very careful when modifying PAM file. One mistake and you can loose your login forever :)

---

### Post by herophuong on 2010-10-03
If something go wrong, you still can use a liveusb to access the disk.

---

### Post by rasmus91 on 2010-10-04
> Can you cat and paste the output of /etc/pam.d/gdm and /etc/pam.d/gnome-screensaver files here ?


not sure what you mean by cat...

---

### Post by Ironfisher on 2010-10-21
Hi

Try removing line "auth sufficient pam_face_authentication.so" of the files /etc/pam.d/gdm and /etc/pam.d/gnome-screensaver

ok?

---

### Post by priesty on 2010-12-13
> **Ironfisher said:**
> Hi

Try removing line "auth sufficient pam_face_authentication.so" of the files /etc/pam.d/gdm and /etc/pam.d/gnome-screensaver

ok?
In 10.10 this works great - just ensure to remove the full line (as suggested by Ironfisher) as mine had "EnableX" after the auth sufficient pam_face_authentication.so
If you fail to do this, your password to log back in wont work after a reboot. I had to use recovery mode to go back in and manually edit both the "gdm" and "gnome-screensaver" files to remove "EnableX".  Then it rebooted and logged back in normally.

---

### Post by naturebud on 2011-08-08
hi am having the same proplem and am using 11.04 can any one help me pleeeeece

---

### Post by und3rw0rld on 2011-11-13
Hi, you could remove pam-face-authetication in this way:

1. Open the terminal.
2. Type "sudo su" and enter the password. 
3. Type "cd /tmp && wget http://pam-face-authentication.googlecode.com/files/pam-face-authentication-0.3.tar.gz"
4. Extract the files from this arhive: "tar -xf pam-face-authentication-0.3.tar.gz"
5. Type "cd pam-face-authentication"
6. Type "mkdir build && cd build"
7. Type "cmake -D CMAKE_INSTALL_PREFIX=/usr .. "
8. Type "make"
9. Type "checkinstall --pkgname=pam-face-authentication"
10. And finally remove the aplication, all you have to do is to type this: "dpkg -r pam-face-authentication". Good luck!

---

