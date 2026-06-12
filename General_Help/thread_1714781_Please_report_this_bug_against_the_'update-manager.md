---
title: "Please report this bug against the 'update-manager' package"
date: 2011-03-25
forum: General Help
---

### Post by meself on 2011-03-25
Hi.

I am running Ubuntu 10.04.  There was a red circle icon on my launcher panel with a white minus sign acoss it.  The icon attempted to open update manager but I got a box with the following four paragraphs:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/cache/apt/pkgcache.bin - open (13: Permission denied), E:Failed to truncate file - ftruncate (9: Bad file descriptor), E:The package lists or status file could not be parsed or opened.'

I opened pkgcache.bin in jEdit to view it but it's a very large file of unreadable machine code.

I recently changed the permissions on the /var/www apache folder to allow development of .php web files locally.  I have no use whatsoever for the restricted permissions on /var/www since my desktop machine is private to me, I use a shared webhosting plan, my files are of no interest to anybody, and I am merely developing web pages there on a new project which nobody has any interest in anyway.  But I'm wondering if changing those permissions is the cause of this update error?

I also recently installed the apache server and phpMyAdmin so I could display and develop php web pages and perhaps this may have triggered the malfunction?

Does anybody know is there a way to fix update manager without re-installing the whole system?


Resolved!  My son ascertained that when I changed permissions in /var/www, I had also changed permissions in /var and that was the cause of the problem and using his terminal commands, restoring the permissions to /var fixed the problem.

I am storing the commands he provided here for future reference:

This should fix the permissions in /var:

sudo chmod -R u=rwx,go=rx /var
sudo chmod -R ug=rwx,o=rx /var/local
sudo chmod -R ugo=rwx /var/lock /var/tmp
sudo chown -R root:root /var
sudo chown -R root:staff /var/local
sudo chown -R root:mail /var/mail

-- 
Mike 2

---

