---
title: "Samba File Sharing(Windows system can't see it)"
date: 2009-12-18
forum: General Help
---

### Post by running_rabbit07 on 2009-12-18
I have multiple Ubuntu systems that have no problems moving files back and forth through shared folders. My Windows Vista system does not see any of the Ubuntu systems, but my Ubuntu systems do see the Windows system. 

How do I make my Ubuntu visible to Windows to transfer files?

Thanks for the replies.

---

### Post by bomber991 on 2009-12-18
Hmm I've got the opposite problem with my setup.  My XP laptop was able to see the files on my ubuntu pc but my ubuntu pc can't see the laptops files.

On the "Samba Server Configuration" I added a folder and made sure the visible checkbox was clicked.  Also under access I made sure that "Allow access to everyone" was selected.  Then on the XP computer I think I went to browse network computers, then to workgroup, and then my ubuntu pc showed up under there.

Hopefully someone can offer a better answer, I'm just saying how I've got it setup.

---

### Post by running_rabbit07 on 2009-12-19
Now that I have started checking settings, neither system can see each other. If we had XP, I'd probably have it worked out already on that end. We are doing this so that we can back the Vista system up on the Ubuntu, so that I can upgrade it to Windows 7. I guess tomorrow I'll be buying DVDs to back it up, if I can't get the FTP working.

---

### Post by clhsharky on 2009-12-19
HI

Windows cant read ext4 yet, might that be the problem?
Even with -Ext2 IFS- driver for windows.

Sharky

---

### Post by bomber991 on 2009-12-19
Good luck with the windows7 update.  It's supposed to be quick and easy but my dad kept calling me up asking me questions when he was doing it.  Took him all day :lolflag:

It does seem like if you couldn't get the pc's to see each other using the network that you would still be able to host a local FTP server on one and just transfer the files like that.

---

### Post by running_rabbit07 on 2009-12-19
> **bomber991 said:**
> Good luck with the windows7 update. It's supposed to be quick and easy but my dad kept calling me up asking me questions when he was doing it. Took him all day :lolflag:
 
It does seem like if you couldn't get the pc's to see each other using the network that you would still be able to host a local FTP server on one and just transfer the files like that.
 
I am gonna give that a try next. 
 
If the upgrade doesn't work right the first try, then I will do the clean install. I don't plan on letting it waste too much time.

---

### Post by koepked on 2009-12-19
If you have no other shares configured for samba, and this will only be a temporary share to backup Windows, doing the following in the terminal should work:

1)$ sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
     - This will backup the current samba config file

2)$ sudo gedit /etc/samba/smb.conf
     - Delete everything and paste the following:

```
[global]
    workgroup = MSHOME
    security = user
    encrypt passwords = true
    map to guest = bad user
    guest account = nobody
    create mask = 0644
    directory mask = 0755

[shared]
    comment = File Server
    path = [path to shared folder]
    browseable = no
    read only = no
    valid users = [ubuntu username]
```3)$ smbpasswd -a [ubuntu username]
     - follow the prompts
     - this adds your ubuntu user to the samba password database

4)$ sudo /etc/init.d/samba reload
     - This loads the new config file into samba

At this point, you should be able to see the share from the windows machine with full read/write permissions. You'll have to enter your ubuntu username and password in a popup window when you try to access it from windows. When your done transferring files, if you want to remove the share, just do the following:

$ sudo cp /etc/samba/smb.conf.bak /etc/samba/smb.conf

Repost with any problems

---

### Post by running_rabbit07 on 2009-12-19
Thanks Koepked. I will give it a shot in the morning.

---

### Post by running_rabbit07 on 2009-12-19
> **koepked said:**
> If you have no other shares configured for samba, and this will only be a temporary share to backup Windows, doing the following in the terminal should work:

1)$ sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
     - This will backup the current samba config file

2)$ sudo gedit /etc/samba/smb.conf
     - Delete everything and paste the following:

```
[global]
    workgroup = MSHOME
    security = user
    encrypt passwords = true
    map to guest = bad user
    guest account = nobody
    create mask = 0644
    directory mask = 0755

[shared]
    comment = File Server
    path = [path to shared folder]
    browseable = no
    read only = no
    valid users = [ubuntu username]
```3)$ smbpasswd -a [ubuntu username]
     - follow the prompts
     - this adds your ubuntu user to the samba password database

4)$ sudo /etc/init.d/samba reload
     - This loads the new config file into samba

At this point, you should be able to see the share from the windows machine with full read/write permissions. You'll have to enter your ubuntu username and password in a popup window when you try to access it from windows. When your done transferring files, if you want to remove the share, just do the following:

$ sudo cp /etc/samba/smb.conf.bak /etc/samba/smb.conf

Repost with any problems

When I do this, The Vista system can see the Ubuntu system, but can't do anything with it.

---

### Post by koepked on 2009-12-20
> **running_rabbit07 said:**
> When I do this, The Vista system can see the Ubuntu system, but can't do anything with it.

My apologies, there's something I should have changed for you that may be the issue, in the /etc/samba/smb.conf I posted, change 'browseable = no' to 'browseable = yes'. That might do it; right now, you might be seeing the machine but not the shared folder. Otherwise, you wouldn't have to change the browseable setting if you map the drive in Vista, just put 'xxx.xxx.xxx.xxx\shared' as the location where the x's represent your ubuntu machine's IP.

---

### Post by running_rabbit07 on 2009-12-20
> **koepked said:**
> My apologies, there's something I should have changed for you that may be the issue, in the /etc/samba/smb.conf I posted, change 'browseable = no' to 'browseable = yes'. That might do it; right now, you might be seeing the machine but not the shared folder. Otherwise, you wouldn't have to change the browseable setting if you map the drive in Vista, just put 'xxx.xxx.xxx.xxx\shared' as the location where the x's represent your ubuntu machine's IP.

I still couldn't get it working. Thanks for giving it a try. I went ahead and used the thumb drive to copy everything over. Upgraded the other system from Vista to 7 and tomorrow I will make it a dual boot.

---

