---
title: "Help with file permissions !!!"
date: 2011-01-18
forum: General Help
---

### Post by akemzo on 2011-01-18
Hi, i just started using ubuntu, hasn't been easy so far, am trying to CHMOD files and folders via filezilla, problem is, i keep getting error 550 "no permission to make action" . Anyone out there who can help me?

---

### Post by piquat on 2011-01-19
.

---

### Post by akemzo on 2011-01-19
Anyone gonna help me with this? :( CHMOD is the problem am having using filezilla:

Status:	Directory listing successful
Status:	Set permissions of '/social.E/Upload/temporary' to '777'
Command:	SITE CHMOD 777 temporary
Response:	550 CHMOD 777 temporary: Operation not permitted

---

### Post by geirha on 2011-01-19
Operation not permitted suggests that the filesystem the file is on does not support permissions. Maybe it's FAT32 or NTFS?

---

### Post by akemzo on 2011-01-19
NTFS? hm! am using ubuntu 10.10......any information you gonna need to help me? am kinda desperate here, spent long hours trying and trying but no good, really it can't be that bad, i just need to be able to CHMOD using filazilla, there i need to have full admin access

---

### Post by smurphy_it on 2011-01-19
You may not be the "owner" and thus can't change file permissions.  You could try going into a terminal, navigate to where you are trying to change the permissions and change the ownership to yourself, and change the permissions to whatever you need.

sudo chown akemzo  (assuming that is your ID)
sudo chmod xxxx


chmod by text, you have (g)roup, (u)ser, and (o)ther  (and a for ALL).... then permissions are (r)ead, e(x)ecute and (w)rite....

so here is an example.

chmod u+rwx somefile.sh

That would give just the user read, write and execute permissions.

---

### Post by smurphy_it on 2011-01-19
You may not be the "owner" and thus can't change file permissions.  You could try going into a terminal, navigate to where you are trying to change the permissions and change the ownership to yourself, and change the permissions to whatever you need.

sudo chown akemzo  (assuming that is your ID)
sudo chmod xxxx


chmod by text, you have (g)roup, (u)ser, and (o)ther  (and a for ALL).... then permissions are (r)ead, e(x)ecute and (w)rite....

so here is an example.

chmod u+rwx somefile.sh

That would give just the user read, write and execute permissions.


Afterwords, you should have no problem accessing it in nautilus...

alternatively. launch nautilus with root permissions.

Hit Alt-F2, and type "sudo nautilus"

---

### Post by akemzo on 2011-01-19
Thanks alot, tried it but geeting the error
 
root@ubuntu:~# chown /opt/lampp/htdosc/uploads
chown: missing operand after `/opt/lampp/htdosc/uploads'
Try `chown --help' for more information.
root@ubuntu:~# ........maybe u can give an exmple?

---

### Post by akemzo on 2011-01-19
Thanks alot, tried it but geeting the error
 
root@ubuntu:~# chown /opt/lampp/htdosc/uploads
chown: missing operand after `/opt/lampp/htdosc/uploads'
Try `chown --help' for more information.
root@ubuntu:~# ........maybe u can give an exmple?

---

### Post by oldos2er on 2011-01-19
**chown** needs an owner:group to assign the target, e.g. **chown akemzo:akemzo /opt/lampp/htdosc/uploads**

---

### Post by akemzo on 2011-01-19
chown -R akemzo:akemzo /opt/lampp/

Now i see a lock on all my folders, can't see my xammp panel also on local host, have i done something wrong again? Thanks to you all for trying to help so far :(

---

### Post by akemzo on 2011-01-19
chown -R akemzo:akemzo /opt/lampp/

Now i see a lock on all my folders, can't see my xammp panel also on local host, have i done something wrong again? Thanks to you all for trying to help so far :(

---

### Post by akemzo on 2011-01-19
Thanks, was able to change the CHMOD at last but now another problem developed in the process,this was the command i used: chown -R akemzo:akemzo /opt/lampp/

Now i see a lock on all my folders, i can't see my xammp cpanel also on local host, have i done something wrong again? Thanks to you all for trying to help so far, more help is needed.

---

### Post by smurphy_it on 2011-01-21
Is this your USERID you are using, or are you blindly entering what was supplied to you ?


The chown should be changed to your USERID.  If you have a lock on them, you probably aren't the owner.

Post results from the following two commands:

whoami
ls -ld /opt/lampp

---

