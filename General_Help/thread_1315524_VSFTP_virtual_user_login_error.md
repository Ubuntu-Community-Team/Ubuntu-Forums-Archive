---
title: "VSFTP virtual user login error"
date: 2009-11-05
forum: General Help
---

### Post by cobraiti on 2009-11-05
Hi,

I'm trying to work how virtual users work via the tutorial and reference below but haven't had any luck logging in.  It keeps giving me error 530 Login failed

[http://imadethisdesign.blogspot.com/2009/05/how-to-vsftpd-virtual-users-pam.html](http://imadethisdesign.blogspot.com/2009/05/how-to-vsftpd-virtual-users-pam.html)

It's based on one of the guides in ubuntu forms.

Here's what I've done

Step 1
sudo useradd -d /home/vftp genesis
sudo mkdir /home/vftp
sudo chown genesis /home/vftp

Step 2
sudo mkdir /etc/vsftpd
sudo mkdir /etc/vsftpd/vusers

Step 3
sudo gedit /etc/vsftpd.conf

anonymous_enable=NO
local_enable=YES
pam_service_name=vsftpd
guest_enable=YES
user_config_dir=/etc/vsftpd/vusers

Step 4
sudo gedit /etc/pam.d/vsftpd

auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vlogins
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vlogins

Step 5
sudo gedit /etc/vsftpd/vlogins.txt

genesis
test123

Step 5
sudo db3_load -T -t hash -f vlogins.txt /etc/vsftpd/vlogins.db
sudo chmod 600 /etc/vsftpd/vlogins.db

Step 6
sudo gedit /etc/vsftpd/vusers/genesis

write_enable=YES
anon_mkdir_write=YES
anon_other_write=YES
anon_upload_enable=YES
local_root=/home/vftp
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=genesis

Step 6 
sudo service vsftpd restart

All of this worked fine but when I login

I get this

ftp localhost
Name: genesis
Password: test123

Error 530 Login incorrect

Where exactly did I go wrong.  Can't seem to figure why it's not logging in. 

HELP !!!! 
--------------------------------------------------------------------------------------------------------------
Issue 2

What I'm try to do is also get a each virtual user that's created to access only specific folders in a directory

Eg I've created folders in the srv dir

/srv/supplies/orders &
/srv/supplies/products

and I want virtual users Say Genesis to have access to only /srv/supplies/order and another user Exodus to access only /srv/supplies/products

Can someone help with this step by step or point me in the right direction.  I was hoping to resolve this issue as per my attempt above

your help would be truly appreciated.

---

