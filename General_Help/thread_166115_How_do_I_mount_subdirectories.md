---
title: "How do I mount subdirectories?"
date: 2006-04-25
forum: General Help
---

### Post by danakatheone on 2006-04-25
How, exactly, do I mount subdirectories of filesystems elsewhere on the filesystem?

---

### Post by WhimpyPeon on 2006-04-25
You would probably be better off with a symbolic link rather than mounting.

For instance:

ln -s /usr/shar/whateverapp /var/www/whateverapp

Let me know if that doesn't work for you.

---

### Post by danakatheone on 2006-04-25
Symbolic links won't do it, sadly, in this situation. I'm sharing this on an FTP server, symlinks don't work.

---

### Post by WhimpyPeon on 2006-04-25
mount --bind /home/wally /mnt/wally

---

### Post by danakatheone on 2006-04-25
Thank you.

---

### Post by danakatheone on 2006-04-25
How could I make it do that on startup?

---

### Post by joachim.j on 2006-10-09
> **danakatheone said:**
> How could I make it do that on startup?

I have the same problem. As stated in the ProFtpd FAQ [http://www.proftpd.org/docs/faq/linked/faq-ch5.html]("http://www.proftpd.org/docs/faq/linked/faq-ch5.html") it's not possible to use Symlinks in the ftp-server hierarchy.

I have used:```
 mount --bind /original_dir/ /new_dir/
``` but the mount disappears when I reboot.

Any suggestions?

---

### Post by aidanr on 2006-10-09
add it to your startup items, gnome-session-properties

or edit /etc/fstab

---

