---
title: "debugging init.d"
date: 2010-03-03
forum: General Help
---

### Post by craigrose on 2010-03-03
Hi.

I have the following script in /etc/init.d/ntfs_ext4_sync.sh.

```
#! /bin/sh
#########################
# START: ntfs_ext4_sync #
#########################

# Synchronises the /home folders for a list of users 
# with an NTFS folder.  
# Unison must be installed and a unison profile 
# in /home/<user name>/.unison created for each user
# called <user name>.prf 
# For simplicity make sure the folder names are the
# same as the user names.
# Run as root.

#USERNAMES="craig lisa daniel stephanie matthew mizzen"
USERNAMES="matthew"

for name in $USERNAMES
do
    echo "Synchronising $name"
    unison $name -perms=0 -silent -batch -ui=text
    chown -R $name:$name /home/$name
    chmod 770 -R /home/$name  
done

#########################
# END: ntfs_ext4_sync   #
#########################

exit 0
```

I believe it to be executable

```
-rwxr-xr-x 1 root root   723 2010-03-02 21:20 ntfs_ext4_sync.sh

```

And it produces the following (correct) output if run manually at terminal

```
mizzen@ubuntu:/etc/init.d$ sudo ./ntfs_ext4_sync.sh
Synchronising matthew
Connected [//ubuntu//home/matthew -> //ubuntu//media/WinUsers/users/Matthew]
mizzen@ubuntu:/etc/init.d$ 

```

The files are synchronised and ownership/permission updated in the Ubuntu home folder.

Now my intention is for the synchronising to happen at Ubuntu start up and shutdown.  You see sometimes this machine is used as a Ubuntu server and sometimes as a Windows 2000 server.

Next step I do this.  Derived from the sample in the man update-rc.d

```
mizzen@ubuntu:/etc/init.d$ sudo update-rc.d ntfs_ext4_sync.sh defaults 98 02
update-rc.d: warning: /etc/init.d/ntfs_ext4_sync.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/ntfs_ext4_sync.sh ...
   /etc/rc0.d/K02ntfs_ext4_sync.sh -> ../init.d/ntfs_ext4_sync.sh
   /etc/rc1.d/K02ntfs_ext4_sync.sh -> ../init.d/ntfs_ext4_sync.sh
   /etc/rc6.d/K02ntfs_ext4_sync.sh -> ../init.d/ntfs_ext4_sync.sh
   /etc/rc2.d/S98ntfs_ext4_sync.sh -> ../init.d/ntfs_ext4_sync.sh
   /etc/rc3.d/S98ntfs_ext4_sync.sh -> ../init.d/ntfs_ext4_sync.sh
   /etc/rc4.d/S98ntfs_ext4_sync.sh -> ../init.d/ntfs_ext4_sync.sh
   /etc/rc5.d/S98ntfs_ext4_sync.sh -> ../init.d/ntfs_ext4_sync.sh
mizzen@ubuntu:/etc/init.d$ 

``` 

However, the script does not appear to run on restart.  Or it possibly runs without output or correct results as the files are not synchronised.

First question is: Have I done everything correctly?
Second: How do I debug my init.d set up?

Thanks
Craig

---

### Post by craigrose on 2010-03-03
Update on the script:

```
#! /bin/sh
#########################
# START: ntfs_ext4_sync #
#########################

# Synchronises the /home folders for a list of users 
# with an NTFS folder.  
# Unison must be installed and a unison profile 
# in /<path to home folder for the logged in user>/.unison created for each user
# called <user name>.prf 
# For simplicity make sure the folder names are the
# same as the user names.
# Run as root.

#USERNAMES="craig lisa daniel stephanie matthew mizzen"
USERNAMES="matthew"

for name in $USERNAMES
do
    echo "Synchronising $name"
    unison $name -perms=0 -silent -batch -ui=text
    chown -R $name:$name /home/$name
    chmod 770 -R /home/$name  
done

#########################
# END: ntfs_ext4_sync   #
#########################

exit 0
```

No real change in the logic just the location where the Unison profiles need to be.  When run from terminal this is the super users home ie /home/mizzen and when trying to run at boot I am assuming this needs to be the root home ie: /root

Still not working though and still can't see how I can debug it.

---

### Post by diesch on 2010-03-03
Add the full paths to the command calls. If it still doesn't work add some
```
 echo something >> /tmp/something.log 
```
so you can see which lines gets executed.

---

### Post by craigrose on 2010-03-04
Thanks diesch.  Now I have confirmed that the script is running on boot up as my log file /tmp/ntfs_ext4_sync.log gets ALL of the echo messages.  But still Unison does not do the update and the /tmp/test2.log is created but empty.  

If I  **$ sudo  /usr/bin/unison matthew -perms=0 -batch -ui=text &> /tmp/test2.log** then I get to see the stdout and stderr in the /tmp/test2.log.  If I **$ sudo /etc/init.d/ntfs_ext4_sync.sh** it works correctly except I get an empty /tmp/test2.log.  

Can anyone explain how I can log the output (stdout and stderr) of the Unison line from within the script?  If I can do that then I have a chance of seeing what's happening during boot.

Amended code below.

```

#! /bin/sh
#########################
# START: ntfs_ext4_sync #
#########################

# Synchronises the /home folders for a list of users 
# with an NTFS folder.  
# Unison must be installed and a unison profile 
# in /<home folder>/.unison created for each user
# called <user name>.prf
# <home folder> = /root 
# For simplicity make sure the folder names are the
# same as the user names.
# Run as root.

#USERNAMES="craig lisa daniel stephanie matthew mizzen"

echo "$(date): Start ntfs_ext4_sync.sh" >> /tmp/ntfs_ext4_sync.log 
USERNAMES="matthew"

for name in $USERNAMES
do
    echo "$(date): Synchronising $name" >> /tmp/ntfs_ext4_sync.log 
    echo "$(date): Starting unison" >> /tmp/ntfs_ext4_sync.log 
#    /usr/bin/unison $name -perms=0 -silent -batch -ui=text
    /usr/bin/unison matthew -perms=0 -batch -ui=text &> /tmp/test2.log 
   echo "$(date): Setting file ownership" >> /tmp/ntfs_ext4_sync.log 
    chown -R $name:$name /home/$name
    echo "$(date): Setting file permissions" >> /tmp/ntfs_ext4_sync.log 
    chmod 770 -R /home/$name  
done

#########################
# END: ntfs_ext4_sync   #
#########################

echo "$(date): Stopping ntfs_ext4_sync.sh" >> /tmp/ntfs_ext4_sync.log 

exit 0

```

---

### Post by craigrose on 2010-03-04
I have worked out how to get error messages to a log file from within my script at boot time using the following

```

/usr/bin/unison $name -perms=0 -batch -ui=text 2>&1 | tee /tmp/test2.log
```

The error that is logging in /tmp/test2.log is

```
Fatal error: exception Util.Fatal("Environment variable HOME not found")
```

Off to Unison to see what this means and will report results back here soon.

---

### Post by craigrose on 2010-03-04
The following script now works.  Added export HOME=/root.  This is the folder where the .prf files are and now Unison can find them.

```

#! /bin/sh
#########################
# START: ntfs_ext4_sync #
#########################

# Synchronises the /home folders for a list of users 
# with an NTFS folder.  
# Unison must be installed and a unison profile 
# in /<home folder>/.unison created for each user
# called <user name>.prf
# <home folder> = /root 
# For simplicity make sure the folder names are the
# same as the user names.
# Run as root.

echo "$(date): Start ntfs_ext4_sync.sh" >> /tmp/ntfs_ext4_sync.log 
USERNAMES="craig lisa daniel stephanie matthew mizzen"
export HOME=/root

for name in $USERNAMES
do
    echo "$(date): Synchronising $name" >> /tmp/ntfs_ext4_sync.log 
    echo "$(date): Starting unison" >> /tmp/ntfs_ext4_sync.log 
    /usr/bin/unison $name -perms=0 -batch -ui=text 2>&1 | tee /tmp/test2.log
    echo "$(date): Setting file ownership" >> /tmp/ntfs_ext4_sync.log 
    chown -R $name:$name /home/$name
    echo "$(date): Setting file permissions" >> /tmp/ntfs_ext4_sync.log 
    chmod 770 -R /home/$name  
done

#########################
# END: ntfs_ext4_sync   #
#########################

echo "$(date): Stopping ntfs_ext4_sync.sh" >> /tmp/ntfs_ext4_sync.log 

exit 0

```

---

