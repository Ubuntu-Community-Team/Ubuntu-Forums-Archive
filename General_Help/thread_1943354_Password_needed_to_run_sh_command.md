---
title: "Password needed to run sh command"
date: 2012-03-19
forum: General Help
---

### Post by Diwin on 2012-03-19
I am on Maverick. In my user's crontab I run a backup script, dbbackup.sh. But it won't run because the sudo password is requested. Why is that? The script is owned by my user account and is executable. This script used to run in lucid. Do I not have permission to run a shell script?

---

### Post by haqking on 2012-03-19
> **Diwin said:**
> I am on Maverick. In my user's crontab I run a backup script, dbbackup.sh. But it won't run because the sudo password is requested. Why is that? The script is owned by my user account and is executable. This script used to run in lucid. Do I not have permission to run a shell script?

well is your user account a member of the sudo group ?

---

### Post by Diwin on 2012-03-19
Thanks for the lightning fast response! I am not sure what you are asking. Something to do with the sudoers file I vaguely think.

---

### Post by philinux on 2012-03-19
> **Diwin said:**
> Thanks for the lightning fast response! I am not sure what you are asking. Something to do with the sudoers file I vaguely think.

Before getting into that it may help to review your script. Can you post it here.

---

### Post by Diwin on 2012-03-19
I trimmed it down to one line for a test and it had the same behavior.

sudo mv /home/david/website_backup/dbbu.5 /home/david/website_backup/dbbu.6

---

### Post by whatthefunk on 2012-03-19
Its asking you for your password because you have "sudo" in front of the script.
Since its in your home directory, you shouldnt need sudo.  Cut it off the front and try again.

---

### Post by Diwin on 2012-03-19
I guess not. I have not added it. And I am the only user of this laptop. Is that 

$ sudo visudo 

and add 

david ALL=(ALL) ALL

?

---

### Post by Diwin on 2012-03-19
> **whatthefunk said:**
> Its asking you for your password because you have "sudo" in front of the script.
Since its in your home directory, you shouldnt need sudo.  Cut it off the front and try again.
Since the script pulls down files from a server using RSync, they are not all owned by me, some are owned by user 627 wherever that comes from. I think that was why I used sudo.

---

### Post by Diwin on 2012-03-19
I added my account to the sudoers list and it still asks for the password. Did I miss a step?

---

### Post by whatthefunk on 2012-03-19
Adding your account to sudoers simply means that you are now allowed to enter the sudo password.  Try running your script without sudo.

---

### Post by Diwin on 2012-03-19
I removed sudo.
This line of code produces the following error.

```
mv /home/david/db_backup/dbbu.1 /home/david/db1_backup/dbbu.2

cp: cannot create link `/home/david/db_backup/dbbu.1/dbbu/db1.sql.gz': Operation not permitted
```

The file referenced in the error is owned by user #627.

Here is the whole script without sudo. I had sudo at each line except the last one.
```
rm -rf /home/david/db_backup/dbbu.6
mv /home/david/db_backup/dbbu.5 /home/david/db_backup/dbbu.6
rm -rf /home/david/db_backup/dbbu.5
mv /home/david/db_backup/dbbu.4 /home/david/db_backup/dbbu.5
rm -rf /home/david/db_backup/dbbu.4
mv /home/david/db_backup/dbbu.3 /home/david/db_backup/dbbu.4
rm -rf /home/david/db_backup/dbbu.3
mv /home/david/db_backup/dbbu.2 /home/david/db_backup/dbbu.3
rm -rf /home/david/db_backup/dbbu.2
mv /home/david/db_backup/dbbu.1 /home/david/db_backup/dbbu.2
rm -rf /home/david/db_backup/dbbu.1
cp -al /home/david/db_backup/dbbu.0 /home/david/db_backup/dbbu.1
rsync --delete -ave ssh someuser@somedomain.com:/home/somefolder/dbbu /home/david/db_backup/dbbu.0/
```

---

### Post by Diwin on 2012-03-19
I obviously am missing a couple things here. This script worked on Lucid, with sudo. What could be different that it would not work on Maverick?

---

