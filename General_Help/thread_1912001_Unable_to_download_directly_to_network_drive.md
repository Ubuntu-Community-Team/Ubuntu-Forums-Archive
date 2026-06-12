---
title: "Unable to download directly to network drive"
date: 2012-01-19
forum: General Help
---

### Post by Ecip on 2012-01-19
Hey guys!

I have noticed that when I download a file in Transmission (torrent) I can not  select to have the file downloaded to a shared folder on the network. I  tried everything I can think of.
I have to download it onto the computer first, then transfer it over. Very annoying. Any thoughts?

---

### Post by Buntumatic on 2012-01-19
Just wondering, what kind of share is that? NFS?

---

### Post by Ecip on 2012-01-19
errm.. its the Patriot Box Office media player connected to the network. I'm not sure now which file system its formated to but since the PBO is linux based it could be an ext partition.. i'd have to dig a bit to find out.

---

### Post by Ecip on 2012-01-19
I should add that while the media player shows up as a network drive (and I can readily copy and transfer and delete etc), I can not select the network drive as a download location in Transmission. Maybe its just an issue with transmission, i'm not sure. havent tried another torrent client..

Edit: Just tried a different client, same thing... See screenshot of what I mean. The network drive is mounted, but I can not select it.

---

### Post by Ecip on 2012-01-19
SOLVED THE PROBLEM!

Here is what to do (according to THIS post): 
[http://ubuntuforums.org/showthread.php?t=1276052](http://ubuntuforums.org/showthread.php?t=1276052)

> The quick and dirty version is as follows:

- Show hidden files by pressing ctrl+h.
- Browse to username/.gvfs, you'll see your network shares listed there.   If you don't see them, then they aren't mounted.  If you don't see  .gvfs, and a lot of other .foldername listed, then press ctrl+h.

The above method will need to be performed each time you start Ubuntu.   If there is a particular share that you want to connect to every time,  then you can edit /etc/fstab according to the directions provided below.   Thanks to uidb4056 for these.

"You have to edit /etc/fstab as root 
 
Code: 
 
sudo gedit /etc/fstab 
 
and add this line: 
 
Code: 
 
//computername/sharename /home/username/foldertomountname smbfs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_   mode=0777 0 0 
 
You need also create if not exists or edit the file .smbcredentials 
 
Code: 
 
sudo gedit /root/.smbcredentials 
 
and add two lines as: 
 
username=yourusername 
password=yourpassword 
 
Save it and then test you can mount using from terminal 
 
Code: 
 
sudo mount -a 
 
If it works then you will have mounted every time you boot. For sure there can be another ways but this is running for me."

This ought to be a sticky.

---

### Post by Ecip on 2012-01-20
I'm actually quite surprised at this point that no one else has ever had this problem or wondered about it.. it's quite a common feature in.. *cough* ..windows to be able to select a networked drive to download to. lol

---

