---
title: "Folders for all users"
date: 2012-06-25
forum: General Help
---

### Post by gmoos1 on 2012-06-25
Hi everyone,

I'm new to using Ubuntu 12.04 and have a couple of questions that are probably quite simple.

1- Is there a way to let all users on a single machine have access to a folder and the documents inside it?

2- Can all the downloads of all the users be made to go a single folder?

Thanks

---

### Post by shashanksingh on 2012-06-25
Yes. You can.

1.You can create a folder in the filesystem, say /opt/commonfolder
and then change the permissions of this folder to be accesible by all.

```
sudo chmod 777 /opt/commonfolder
```

2. You can change the browser setting to set the default download folder to that common folder

---

### Post by HiImTye on 2012-06-25
yes and yes.

use a symlink to another folder, say /shared/Downloads or /shared/Documents or w/e you want. do the following:

1. make the folder and change ownership of it to you and your 'shared' group:
```
sudo sh -c "mkdir /shared; groupadd shared; chown <yourusername>:shared /shared"
```change <yourusername> to your username.

2. add everyone to the 'shared' group
```
sudo sh -c "for f in /home/*; do sed 's|/home/\(.*\)|useradd -aG shared \1|e'; done"
```you might want to add people individually if you don't want some people in the group or you can simply remove some people from it

3. change permissions
```
sudo chmod -R g=rwx /shared
```you might want to add a cronjob to periodically enforce the permissions change of any new files in the folder (just use step 3 in a cronjob) but this should give you a basic working shared folder. after this, just make the subfolders you want and make soft links to whatever subfolders you need, such as "$HOME/Music/", "$HOME/Documents/", etc..

---

### Post by gmoos1 on 2012-06-25
Cheers Hilmtye, I'm sure that'a a really good explanation of it, but it's way over my head unfortunately :(.

Say I want the folder to be called commonfolder and it is on the desktop, and will be shared with everyone, is there a way to do it without all the code? Or only using fairly simple code?

---

### Post by HiImTye on 2012-06-26
> **gmoos1 said:**
> Cheers Hilmtye, I'm sure that'a a really good explanation of it, but it's way over my head unfortunately :(.

Say I want the folder to be called commonfolder and it is on the desktop, and will be shared with everyone, is there a way to do it without all the code? Or only using fairly simple code?

I made the code as efficient as possible but you can do it using nautilus as root (be very careful here):
```
gksudo nautilus
```you will still need to create and add each user to the shared group and also, change permissions of the folder:
```
sudo groupadd shared[FONT=monospace]
sudo [/FONT]useradd -aG shared <username>
sudo chmod -R g=rwx /<foldername>
```

also, you don't want the folder to be in a user's folder (i.e. on someones' desktop) that's what soft links are for. once you're done in root nautilus, switch to regular nautilus and make soft links to your shared folders (right click on it and choose 'make link') then put those in your user's home folders

---

### Post by gmoos1 on 2012-06-26
I don't really want to go into things I can easily screw up because I am far from competent with Ubuntu.

So there is no place in Ubuntu that all the users can see by default? If so, then it might be easier for me to just copy and paste the folder into everyone's account...

---

