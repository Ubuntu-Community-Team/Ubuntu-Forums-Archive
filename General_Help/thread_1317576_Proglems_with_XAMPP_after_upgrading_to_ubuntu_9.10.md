---
title: "Proglems with XAMPP after upgrading to ubuntu 9.10"
date: 2009-11-06
forum: General Help
---

### Post by martez81 on 2009-11-06
Hi everybody

I had XAMPP set up and working with Ubuntu 9.04 flawlessly. In httpd.conf file root directory was set to harddrive with windows file system where all my web documents are located. 

After upgrade to 9.10 when I start xampp and try to access any document on localhost the browser will return me 403 Access Forbidden page. 
When I changed root folder in httpd.conf to something on linux partition then it would load the web page.

Anybody knows where the problem might be?

---

### Post by chrome101 on 2009-11-08
I,m having the same problem too :mad:

---

### Post by martez81 on 2009-11-08
I think it has something to do with files and folders permission. When I go to permission tab I get "none" for folder access in the "Others" section. When I try to switch it to "create and delete files" It switches back to "none". 

It's just weird that everything worked fine before upgrading to 9.10 hmm

Anybody?

---

### Post by martez81 on 2009-11-08
Ok it's solved.

In order to make it working I had to change permissions when mounting a hard drive.

First I created folder for the mounting point:

mkdir /media/ntfsdrive

Then I added this string at the very end of the file /etc/fstab (it will mount the drive during the boot):

/dev/sda/ /media/ntfsdrive ntfs nls=utf8,umask=0222 0 0

Save changes to fstab and restart ubuntu

---

### Post by headlessspider on 2009-11-16
okay. your solution references an ntfs-formatted drive but how about drives on ext4?

or does this work with ext4 drives?

---

### Post by headlessspider on 2009-11-17
i think i figured it out. [the steps are here]("http://noel.alanguilan.com/2009/11/17/xampp-and-the-koala/"). in short, i moved my development data--html, php pages along with its associated files under the Public folder and then applied the permissions of the Public folder recursively. i had to change my document roots but that's a minor thing.

---

