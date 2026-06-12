---
title: "Rsync remote backup help"
date: 2011-01-10
forum: General Help
---

### Post by neokyle on 2011-01-10
I'm trying to use rsync to make a remote backup. I want to have files from my dedicated server be copied over to my desktop. This is the command im using.


rsync -avc /testfolder/ root@localhost:~/testfolderbackup

I assume for root@localhost i would have ? my remote machines information. I have no idea what that info would be.

Thanks in advance :)

---

### Post by Drenriza on 2011-01-10
rsync -a -r -z -v --progress --partial -e ssh /source USER@IP:/destination      from server to desktop

rsync -a -r -z -v --progress --partial -e ssh USER@IP:/source/ /destination/    from desktop to server

These are two rsync commands i use for such. And it was a pain to figure out how i would use it. With options and so on and so forth.

Example:
rsync -a -r -z -v --progress --partial -e ssh /home/name/Desktop/background.gif drenriza@192.168.100.150:/home/name/Desktop/

---

### Post by neokyle on 2011-01-10
> **Drenriza said:**
> rsync -a -r -z -v --progress --partial -e ssh /source USER@IP:/destination      from server to desktop

rsync -a -r -z -v --progress --partial -e ssh USER@IP:/source/ /destination/    from desktop to server

These are two rsync commands i use for such. And it was a pain to figure out how i would use it. With options and so on and so forth.

Example:
rsync -a -r -z -v --progress --partial -e ssh /home/name/Desktop/background.gif drenriza@192.168.100.150:/home/name/Desktop/

Also for user@ip , user is the username of my account on my computer? and the ip is my ip address?

otherwise this looks great. Im completely new to ubuntu, linux, and ssh clients so it looks a little confusing but im sure i,ll figure it out. Do i need anything installed on my desktop for this to work?

thanks again.

---

### Post by neokyle on 2011-01-10
Received this error when trying to run the command.

root@neokyle:/# rsync -a -r -z -v --progress --partial -e ssh /testfolder/ kyle@192.168.101.104:/Downloads/BACKUPS
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(544) [sender=3.0.6]

---

### Post by Drenriza on 2011-01-10
rsync -a -r -z -v --progress --partial -e ssh /testfolder/ kyle@192.168.101.104:/Downloads/BACKUPS

is /testfolder/
Does testfolder lie in the root of the directory? or else try type the full path.

user is the user of the remote machine.
And ip the the ip of the remove machine.

Also add the /testfolder/ to the end of your line as shown.

```
rsync -a -r -z -v --progress --partial -e ssh /testfolder/ kyle@192.168.101.104:/Downloads/BACKUPS/testfolder/
```> Do i need anything installed on my desktop for this to work?
you only need rsync & ssh server installed, where rsync is installed by default.

Check that rsync is installed
```
dpkg -i |grep rsync
```install ssh server, on the server.
**```
sudo apt-get install openssh-server
```**

---

### Post by Drenriza on 2011-01-12
Did you figur it out?

---

### Post by neokyle on 2011-01-12
I havnt had a chance to try out what was in your last post yet. Not sure about what I should put for user. My remote machine is a windows desktop. So I'm a little confused as to what I should put for user it's not like with my server where I connect using an ssh client.

---

