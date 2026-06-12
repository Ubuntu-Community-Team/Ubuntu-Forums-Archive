---
title: "Samba share issue"
date: 2011-06-02
forum: General Help
---

### Post by HTF1 on 2011-06-02
Hello,

Could you please help me to trace the issue with Samba configuration.

I created Samba share on my CentOS machine but for some reason I can write to this shares (from my Ubuntu machine) only if the permissions are fully open (777) even if I access it as a owner of these files on CentOS.

The second problem here is that I also set the sticky bit (1777) so only the creator of the file can modify/delete it and this works fine from two other Windows machines but from Ubuntu I can create a file but right after creation it has a padlock symbol and I have only read permission to this file. 
When I check the logs on CentOS it says that I access Samba share from Ubuntu as a user which is an owner of these files so I don't understand why it's loosing privileges right after creation.
I also set 'admin user' in 'samba.conf' file and I can modify files owned by other users from Windows (if I'm looged in as a this admin user) but on Ubuntu it's just not working.

Please find config files below:

> [global]
    workgroup = ds
server string = SambaBox
netbios name = server
log file = /var/log/samba/smb.log
max log size = 50
security = user
passdb backend = smbpasswd
username map = /etc/samba/smbusers
guest account = smbuser
guest ok = yes


[Storage]
comment = Private storage on local server
path = /home/Storage
writeable = no
write list = userone, usertwo
valid users = userone, usertwo

[Public]
comment = Public storage on local server
path = /home/Storage/Public
valid users = userone, usertwo, userthree
writeable = yes
admin users = userone
'userone' is the main owner

Output from /etc/fstab file on Ubuntu machine:

> #SambaBox
//192.168.1.10/Storage /media/Storage cifs credentials=/home/userone/.smbcred 0 0

.smbcred file:

> username=userone
password=password

---

### Post by jamesisin on 2011-06-02
This is the defacto post on setting up Samba:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

And here is the thread to follow for setting up CIFS to access those shares:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

(This second author is the master of Samba.)

That ought to get you where you need to be.

---

### Post by HTF1 on 2011-06-02
Hello,

Thanks for help. It's solved now.

REF: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

>  Add gid, uid, and nounix options to your fstab line like so:
     Code:
     //netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,[COLOR=Red]gid=1000,uid=1000,nounix[/COLOR],file_mode=0777,dir_mode=0777 0 0


---

### Post by jamesisin on 2011-06-02
Excellent.  Those are the two threads I use for all things Samba so I thought you'd be good.

Be sure to mark this thread as SOLVED under Thread Tools above.

---

