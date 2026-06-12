---
title: "Editing apache file"
date: 2012-04-11
forum: General Help
---

### Post by nabberuk on 2012-04-11
Hi,

I've just installed the desktop version of Ubuntu. I'm planning on doing some website development on it. I've installed apache and php, i now have the following issue.

When i browse to /var/www/ i can't edit/create any files. I presume this is because i don't have the permission's too. How can i add the correct permission on the www folder?

thanks

---

### Post by SeijiSensei on 2012-04-11
Quick solution is to add your user account to the www-data group and make sure /var/www and anything below is writable by that group.

1)  Add yourself to the group

Edit the file /etc/group as root with sudo.  Find this line in the file:

```
www-data:x:33:
```

then add your username after the final colon without any spaces.  You're now a member of the www-data group.

2)  Fix permissions

```
cd /var
sudo chgrp -R www-data www
sudo chmod g+w -R www

```

Now the group has write permissions to /var/www and anything below it.

To test this, log in as normal and run the command "touch /var/www/testfile".  That will create a zero-length file called testfile in the /var/www directory.  If you get a "permission denied", ask again here, and we'll figure out why.

---

### Post by nabberuk on 2012-04-12
Hi,

thanks for you reply, after following the commands you posted i still get permission denied.

```
nathan@ubuntu:~$ touch /var/www/testfile
touch: cannot touch `/var/www/testfile': Permission denied

```

thanks

---

### Post by nabberuk on 2012-04-12
Got it sorted, i had to log out and back in again for the group alterations to take effect.

thanks for you help!

---

### Post by Lars Noodén on 2012-04-12
> **SeijiSensei said:**
> Quick solution is to add your user account to the www-data group and make sure /var/www and anything below is writable by that group.

A drawback to that method is that it also grants write permission to the web server and related processes.  That could be considered by some to be a rather serious security risk.  

If there is only one user to ever access /var/www, then it would be enough to change owndership to that user.

```

sudo chown -R nabberuk:nabberuk /var/www

```

If there are several users that must share write access to /var/www, then a group can be made for just that activity and leave httpd out of the picture by leaving www-data alone.

```

sudo addgroup webmasters

sudo gpasswd --add nabberuk webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws "{}" \;

```

---

### Post by mörgæs on 2012-04-12
> **nabberuk said:**
> Got it sorted, i had to log out and back in again for the group alterations to take effect.

thanks for you help!

Good, then please mark the thread 'solved'.

---

