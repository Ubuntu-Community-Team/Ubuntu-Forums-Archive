---
title: "File Permissions"
date: 2009-09-22
forum: General Help
---

### Post by Sarteck on 2009-09-22
I have a directory, /var/sites/cb/www.
I want to give four users read/write/execute permissions to this directory.  All these users belong to the group "webmasters" that I created.  The directory is owned by www-data and the webmasters group, and I have the directory permissions set to 775.  I thought this would allow the webmasters group write access, but they are unable to create files there (unless they sudo, and only one of them has sudo privileges).

Could someone tell me what I might have done wrong, or if I am going about this the right way?

---

### Post by bobince on 2009-09-22
That sounds like it should work in general. Have you tried logging in as those users (or ‘sudo su’) and trying to change into that directory and ‘touch’ a file to see what the error is?

Check that /var, /var/sites and /var/sites/cb are executable for the webmasters group or they may not be able to get into the www directory in the first place.

---

### Post by Lars Noodén on 2009-09-22
# Verify that anotheruser is a member of the group webmasters
groups anotheruser

# everything shall be owned by the right user
sudo chown -R www-data /var/sites/cb/www

# everything shall be owned by the right group
sudo chgrp -R webmasters /var/sites/cb/www

## Fix existing files and directories
# set directory permissions, sticky for group
sudo find /home/ -type d -exec chmod 2775 {} \;

# set file permissions
sudo find /home/ -type f -exec chmod 0774 {} \;



## Test the settings
sudo su - anotheruser
touch /var/sites/cb/www/foo && ls -lh /var/sites/cb/www/

rm -i /var/sites/cb/www/foo

----

References:

chown(1)
[http://linux.die.net/man/1/chown](http://linux.die.net/man/1/chown)

chgrp(1)
[http://linux.die.net/man/1/chgrp](http://linux.die.net/man/1/chgrp)

chmod(1)
[http://linux.die.net/man/1/chmod](http://linux.die.net/man/1/chmod)

find(1)
[http://linux.die.net/man/1/find](http://linux.die.net/man/1/find)

su(1)
[http://linux.die.net/man/1/su](http://linux.die.net/man/1/su)

---

### Post by Sarteck on 2009-09-22
bobince, Lars, thank you both.

Lars, I executed the chown and chgrp commands and all four users of the webmasters group is now able to read, write, and execute within the directory.  Thanks a lot!

---

