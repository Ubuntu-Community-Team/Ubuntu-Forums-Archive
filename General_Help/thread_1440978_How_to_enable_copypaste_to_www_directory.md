---
title: "How to enable copy/paste to www directory?"
date: 2010-03-28
forum: General Help
---

### Post by insanoff on 2010-03-28
How to enable copy/paste to www directory or how to copy files to www directory?

---

### Post by lisati on 2010-03-28
Are you running a server? 

You are likely to need [root privileges]("https://help.ubuntu.com/community/RootSudo").
If you have a GUI on your server, you can use Nautilus as usual. From the command line, the cp command does me fine.

---

### Post by insanoff on 2010-03-28
yes, i'm running lamp server.

---

### Post by new_tolinux on 2010-03-28
On a previous install I fixed this by adding my local user to the group www-data

On the current install I changed ownership to user:www-data and chmod 770

Not the most secure way, but it's only a home server (with in the firewall port 80 only enabled for the local ip-range).

---

### Post by insanoff on 2010-03-28
is there another way to do this? for example: paswword protected normal copy/paste?

---

### Post by Mawoon on 2010-03-28
You can change the permissions so you can write to the folder. Since it's a development computer (I assume), this is a very good idea.

/var/www is my www directory, yours might be different
sudo chown {your_name} /var/www/
sudo chmod 755 /var/www/ -R

NOTE: 755 does not always work, note that there are no write permissions, caching would be impossible on 755 files

[PHP]
<?php
$filename = '755-file.txt';
$handle = fopen($filename, 'w');
fwrite($handle, 'Some text');
fclose($handle);
?>
[/PHP]

This would be impossible since you'd need write permissions. It's best to manually make a data or cache directory that has write permissions.

Hope that helped

---

### Post by insanoff on 2010-03-28
Thanks all for awesome advise!:popcorn:

---

### Post by new_tolinux on 2010-03-28
> **Mawoon said:**
> sudo chown {your_name} /var/www/
sudo chmod 755 /var/www/ -R

I would suggest using
sudo chown -R {your_name} /var/www/

since you also used -R for the chmod command.
@OP: -R stands for "recursive", so not only /var/www/ will get the changed user+rights, but also /var/www/includes for example.

---

