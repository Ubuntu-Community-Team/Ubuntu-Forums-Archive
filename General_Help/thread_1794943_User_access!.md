---
title: "User access!"
date: 2011-07-01
forum: General Help
---

### Post by tarciokk on 2011-07-01
Hello,i used ubuntu server amd64bit , so i have 2project in my server. And i created user: **lineage**

How i can give **him** access only for 1 folder /lineage/    he was in main directory "/".
I wana what all folders was disappear for this user,only  /lineage/ left for this user.

So how i can do it? with "putty" ?           I know about chmod. but this is bad becouse if i put chmod for all folders like var/www....     My ftp and website stop working.

Sorry for bad english!

---

### Post by sam_delta on 2011-07-01
your looking into jailing the user into one folder, tell us which protocol is the user using to access the server? ftp? ssh?

sam

---

### Post by tarciokk on 2011-07-01
Ye you right.   wincsp (ftp) for user: lineage.

  i can use shh(putty) and winscp(ftp).

---

### Post by sam_delta on 2011-07-01
if your using vsftp daemon, you can jail a single user to his home directory. So in your case, you would have to change the user's home directory to /lineage/.

After changing the home directory of the user to lineage, edit the file /etc/vsftpd.conf and uncomment the lines (remove the leading # from the lines) that says ```

chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

```

and then, add the user "lineage" (just type lineage on one line) in the file /etc/vsftp.chroot_list.

if you wish to jail every user in the server to its own home, just keep the line "chroot_list_enable=YES" commented.

if you have any question regarding any of the steps above, let us know

sam

---

### Post by tarciokk on 2011-07-01
Thanks,for answer.    I search /etc/vsftpd.conf     , but i don't have this file :-k
Maybe i can try to do something with shh(putty) ? Here my /etc/  folder screen 

[U][]("http://img232.imageshack.us/i/49539229.jpg/")[[IMG]http://img232.imageshack.us/img232/6028/49539229.th.jpg[/IMG]]("http://img232.imageshack.us/i/49539229.jpg/")


[/U]

---

### Post by sam_delta on 2011-07-01
ok, you can use a program called "scponly" to do that, but first, dont do this if lineage is your administrator user (the first user you made in your server).

This method im about to write will create a new user that will be chrooted (jailed). If the user you want to jail is lineage, please delete the user before proceeding. ```
sudo deluser lineage
```.

Now, to make the jail, do the following

1. login via ssh to your server using your administrator account. (you can use putty to login via ssh).

2. Install scponly with the following command ```
sudo apt-get install scponly
```
Make sure you select "YES" when asked if you want to install the scponlyc to enable chroot enviroments.

3. Make the jailed user with the following commands
```
cd /usr/share/doc/scponly/setup_chroot
sudo gunzip setup_chroot.sh.gz
sudo chmod +x setup_chroot.sh
sudo ./setup_chroot.sh
```
When prompted for the username, type "lineage"
When prompted for the home directory, thpe the directory where you want the user to be jailed, i assume that in your case is "/lineage"
When prompted for the writable subdirectory, type any namefolder for the uploaded files, or just type the same as your home directory ("/lineage").

should be done, try and see if the user lineage is jailed.

let us know how it goes.

sam

---

### Post by tarciokk on 2011-07-02
**Thanks!!!  Its work**, but when i connect with wincsp (SCP) in lineage user.  I got some error
 Command 'groups'
failed with return code 1 and error message
/usr/bin/groups: cannot find name for group ID 1003.
I click Ok and it work,but lineage user ** can't  edit,upload files**, in /lineage/   folder , he can only see whem. 



Cannot execute SCP to start transfer. Please make sure that SCP is installed on the server and path to it is included in PATH. You may also try SFTP instead of SCP.
Command failed with return code 255.

---

### Post by tarciokk on 2011-07-02
Please help

---

### Post by sam_delta on 2011-07-02
im a little busy right now, ill check it out and post back later.

sam

---

### Post by tarciokk on 2011-07-04
OK will wait :-(

---

### Post by tarciokk on 2011-07-06
;(

---

### Post by sam_delta on 2011-07-07
sorry, i was out of town. I had a quick look at it, and there are some solutions to the problem, BUT id been thinking and if what you are doing is just transfering files to the server, it would be much more simpler and easy to set up a jail using FTP protocol and using one of the many FTP clients available. to install ftp, simply install vsftp ```
 sudo apt-get install vsftpd
```, to make the jail, make the user, and follow the steps i described in post number 4 of this same thread.

let me know how it goes,
sam

---

### Post by tarciokk on 2011-07-07
i will try

---

