---
title: "How to auto mount network share at boot"
date: 2011-07-17
forum: General Help
---

### Post by Dragonfire00 on 2011-07-17
Ubuntu newb running 11.04. Seems like allot of other newbs are having trouble mounting the network drive at boot in fstab. Tried a bunch of things and cruising the forums but just ended up being a mess. Finally got it going and I though I would share for others and if I need to do it again later.

Also worth noting is that it is not very secure as the file you save the credentials in is in plain text, but I didn't care at this point.

The source I got it from is outdated so the command took tweeking which I will show below.

First you have to install smbfs
```
sudo apt-get install smbfs
```

Then create a folder inside of the /media directory to mount the share in:

```
sudo mkdir /media/server
```

Create a credentials file in /root so that you can save your password and have it protected by the root account.

```
sudo gedit /root/.cifscredentials
```

Add the following lines to the file and just replace the username/psswd with the ones you use to log into the share.

```
username=Guest
password=
```

Note: If your fileserver allows Guest access you can just leave the file as above. If it is password protected you have to put in your username and password.

Save and close the .cifscredentials file.

Now open up your fstab file so that you can add mounting instructions (recommend backup first "sudo cp /etc/fstab /etc/fstab.bak):

```
sudo gedit /etc/fstab
```

Important note, for me this is slightly different in 11.04 as it required my UID which you can find by typing "id" at the prompt. Add this line to the bottom of the fstab file:


Origional: 
```
//192.168.0.10/SHARENAME /media/Storage cifs auto,iocharset=utf8,uid=USER,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
```

Mine:
```
//10.0.0.2/server /media/server cifs auto,iocharset=utf8,uid=1000,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
```

You have to change the following information:
Change 192.168.0.10 to the IP address or DNS name of your server
Change SHARENAME to the share you want to mount
Change USER to your Ubuntu username

The file_mode=0775,dir_mode=0775 part sets the mounted directory as read/write for all users so long as the SMB username you set in .cifscredentials has read/write access.

Now save the file and run the following command to test to see if you mount now works:

```
sudo mount -a
```

If that worked you should see a new drive icon on your desktop that lets you access your share. Now try rebooting and see if your shares mount automatically. If everything went as planned you will have a nice little drive mounted on your desktop every time you start up.


source: 
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)


edit: Also if your wondering what my share is, I have an ubuntu 64bit server running and there is an SMB share on that (usb hard drive).

---

### Post by seawolf167 on 2011-07-17
You can change the ownership and permissions for your credentials file so only root has access to it for additional security

```
sudo chown root .cifscredentials
sudo chmod 600 .cifscredentials
```

---

### Post by Dragonfire00 on 2011-07-17
> **seawolf167 said:**
> You can change the ownership and permissions for your credentials file so only root has access to it for additional security

```
sudo chown root .cifscredentials
sudo chmod 600 .cifscredentials
```

Good point, thanks! :)

I had to explicitly state the directory if I wasn't root.

```
sudo chown root /root/.cifscredentials
sudo chmod 600 /root/.cifscredentials
```

```
-rw-------  1 root root   39 2011-07-17 15:21 .cifscredentials
```

---

### Post by tokyo-joe on 2011-07-17
What does the "cifs auto" option mean?
What is the difference between a plain "cifs" and a "cifs auto"?

---

### Post by Dragonfire00 on 2011-07-17
> **tokyo-joe said:**
> What does the "cifs auto" option mean?
What is the difference between a plain "cifs" and a "cifs auto"?

I think the 'auto' option might be reference to the autofs (automount) and is used so the system doesn't try to mount the share before the network is up. Not 100% sure though, just found that referenced elsewhere :P including here:  
[http://forums.plexapp.com/index.php/topic/27694-ubuntu-pms-auto-reconnect-cifs-shares/](http://forums.plexapp.com/index.php/topic/27694-ubuntu-pms-auto-reconnect-cifs-shares/)

After searching on the options in the forum, looks like this has been covered in depth here:
[http://ubuntuforums.org/archive/index.php/t-710607.html](http://ubuntuforums.org/archive/index.php/t-710607.html)

---

### Post by tokyo-joe on 2011-07-17
> **Dragonfire00 said:**
> I think the 'auto' option might be reference to the autofs (automount) and is used so the system doesn't try to mount the share before the network is up. Not 100% sure though, just found that referenced elsewhere :P including here:  
[http://forums.plexapp.com/index.php/topic/27694-ubuntu-pms-auto-reconnect-cifs-shares/](http://forums.plexapp.com/index.php/topic/27694-ubuntu-pms-auto-reconnect-cifs-shares/)

After searching on the options in the forum, looks like this has been covered in depth here:
[http://ubuntuforums.org/archive/index.php/t-710607.html](http://ubuntuforums.org/archive/index.php/t-710607.html)

Actually, I am having a problem w/ a RAID drive (not a network drive), but the issue seems to be same: fstab mounting fails because it tries to mount before network starts.
  [http://ubuntuforums.org/showthread.php?t=1806463](http://ubuntuforums.org/showthread.php?t=1806463)

How can I delay fstab mounting to avoid this problem? Is the "auto" option useful in my case? The RAID drive should not require network connection, though...

---

### Post by Dragonfire00 on 2011-07-18
> **tokyo-joe said:**
> Actually, I am having a problem w/ a RAID drive (not a network drive), but the issue seems to be same: fstab mounting fails because it tries to mount before network starts.
  [http://ubuntuforums.org/showthread.php?t=1806463](http://ubuntuforums.org/showthread.php?t=1806463)

How can I delay fstab mounting to avoid this problem? Is the "auto" option useful in my case? The RAID drive should not require network connection, though...

Ya, not sure on the RAID as i don't have it configured. Not sure on the damage but i suppose if there is not much on it you could give it a shot.

---

### Post by corydchurch on 2013-01-15
I have followed these instructions to the T using Ubuntu 12.10. After I do ```
sudo mount -a
``` I get ```
mount error (13): Permission denied
```. Can anyone help?

---

### Post by Elfy on 2013-01-15
Old thread closed. 

Please start a new thread rather than tagging onto an old one.

---

