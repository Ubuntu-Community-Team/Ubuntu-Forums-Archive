---
title: "rsync acl ownership"
date: 2012-09-05
forum: General Help
---

### Post by teacosy on 2012-09-05
hi... 

i have a samba fileserver on an ubuntu server using acl's and i want to back it up to another ubuntu server using rsync. 

im running this as a cronjob. this is the command:

```

rsync -az --delete -e ssh /home/sambashare/ backup:/media/fileserverbackup/backup/

```

i want to preserve all acl's and file/directory permissions. 

at the moment the timestamp and group is being replicated but not the acl users or owner. the owner is the user running the cronjob. 

has anybody had experience backing up acl?

is there another way i should do this? 

thanks in advance... 

teak

---

### Post by Habitual on 2012-09-05
```
-p, --perms
This option causes the receiving rsync to set the destination permissions to be the same as the source permissions.  (See also the --chmod option for a way to modify what rsync  considers  to be the source permissions.) 
```

I've used -azp in the past. Add "v" for verbosity. Perms can get messy on the target, so I usually only rsync as root.

---

### Post by LewisTM on 2012-09-05
Use the -A switch to transfer ACLs. The -X also exists for transferring other kinds of user extended attributes. So -aAX would sync everything.

Cheers!

---

### Post by teacosy on 2012-09-06
thanks Habitual... 

ive tried the -p option with no luck... i thought with the -a option -p is implied... 

i am tring to ssh rsync as root but am having problems as there is no root password... 

any ideas? 

thanks again

---

### Post by teacosy on 2012-09-06
ah thanks LewisTM... 

the -AX options replicated the acl's but the ownership is still with the user running rsync and not the owner on the fileserver... 

would rsync'ing as root fix that?

---

### Post by LewisTM on 2012-09-06
You need to ssh in as the desired user
```
rsync -aAXz --delete /home/sambashare/ **<username>@**backup:/media/fileserverbackup/backup/
```
Most ssh daemons don't permit root logins by default, whether it be though keys or passwords. This can be changed but is considered insecure.

Edit: I see where you're getting at. You have variable owners for your files and you want that mirrored. This cannot be done in a straightforward way through rsync/ssh. I'll report back if I find a solution.

---

### Post by LewisTM on 2012-09-06
Okay, it's definitely possible, although less secure.

1) Edit your server's /etc/ssh/sshd_config file and change 
PermitRootLogin to yes

3) Restart ssh
```
sudo service ssh restart
```

2) Run *sudo ssh-keygen* to generate a key for the root user.

3) Copy that key (in /root/.ssh/id_rsa.pub) to your server's /root/.ssh/authorized_keys

4) Test whether you can login as root
```
sudo ssh backup
```

5) You should now be able to rsync as root. Just put sudo in front of the command.

I have an alternative if you don't want to allow root logins: **metastore**. It's a tool available in the repos that will store all metadata about a file tree, including **ownership**, ACLs, xattrs and permissions. It puts them in .metadata at the base of the tree.
```
cd /home/sambashare
metastore -s
```
Would store all metadata. The file should then be backed up as a regular user (not root) and so should all other files.

To reapply metadata after a restore from backup, run
```
cd /home/sambashare
sudo metastore -a
```
It's a solution for any backup container that doesn't support  the full Linux file attribute set, such as most network shares and Dropbox.

Good luck!

---

### Post by teacosy on 2012-09-06
thanks very much again... 
yes you are correct... 
i thought about as much... 
ill post a solution if i find one also...

---

### Post by teacosy on 2012-09-06
ok thanks...
i have to head off, but ill give it a go soon and post the results...

---

