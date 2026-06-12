---
title: "File permissions for copied files, on external HDD - help!"
date: 2010-03-24
forum: General Help
---

### Post by Sgt_P on 2010-03-24
I'm sure that the issue I'm having is easily solvable once I gain some understanding about copying files - and file permissions in Ubuntu. Here's my situation:
 
I have an external HDD where I like to back up some files (I mess around with distros on my main machine and feel less stressed knowing the important stuff is backed up). I have an ext4 partition on the external drive where I have copied files, both through the terminal (cp 'filename' /dev/sdc3) and by drag and drop (gnome-terminal).
 
The problem is, once the files are copied, most are inaccessible. I can view them, but some directories and individual files say I do not have permission to open them. Others are accessible. This is from the same user profile that copied them.
 
How do I see what's going on? More importantly, how do I make files on external drives available to any user or OS (that can handle ext4)? I want to make sure that if my whole system gets effed that I could still do a reinstall of my OS and then access those backup files.
 
Thanks in advance.

---

### Post by rnerwein on 2010-03-24
hi
do realy used the device name "/dev/sdc3" as the target for your copying ???
i guess you have to use the mount point.
let's say your mount point of /dev/sdc3 is /backup then you can create there the folders 
/backup/home/your_username, /backup/home/other_username1 ... and so on.
then in a terminal run: 
sudo -i  ( be careful you are running a root shell now !!!!!!! )
chown your_username:your_groupname /backup/home/your_username
run this command for the other users ( with their user and group names )
cd /home/your_username
cp -r ./* /backup/home/you_username
do the same for the other users ( but to their folders )
exit
ciao

---

### Post by kleskjr on 2010-03-24
hi, just yesterday I had similar issue and found the following very useful:

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html)

it is just a line of code but maybe it would be better if you have a look on the whole article in case in the future you will have the same problem

---

### Post by Sgt_P on 2010-03-24
> **rnerwein said:**
> hi
do realy used the device name "/dev/sdc3" as the target for your copying ???
i guess you have to use the mount point.
let's say your mount point of /dev/sdc3 is /backup then you can create there the folders 
/backup/home/your_username, /backup/home/other_username1 ... and so on.
then in a terminal run: 
sudo -i ( be careful you are running a root shell now !!!!!!! )
chown your_username:your_groupname /backup/home/your_username
run this command for the other users ( with their user and group names )
cd /home/your_username
cp -r ./* /backup/home/you_username
do the same for the other users ( but to their folders )
exit
ciao
 
Well, I have a backup directory, so the target is really /dev/sdc3/backup but you got the idea. 
 
Thank you for the suggestion - it helps me understand a bit more. However, it wouldn't solve the problem of having a system crash, reinstall, and THEN accessing these files since your procedure assumes I know the name/group of a user in the future. The link from kleskjr solves it though, giving permissions to 'others'.

---

### Post by Sgt_P on 2010-03-24
> **kleskjr said:**
> hi, just yesterday I had similar issue and found the following very useful:
 
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html)
 
it is just a line of code but maybe it would be better if you have a look on the whole article in case in the future you will have the same problem
 
Great! :) Thanks for the link, I had only searched the Ubuntu forum and only found articles about not being able to copy in the first place. 
 
I will give the commands in that article a go and hopefully be on my way.

---

### Post by kleskjr on 2010-03-24
no probs,
maybe you should use additionally the option -R (--recursive) to change all the files into the drive.
good luck

---

