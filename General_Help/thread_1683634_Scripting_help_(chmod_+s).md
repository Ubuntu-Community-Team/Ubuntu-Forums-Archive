---
title: "Scripting help (chmod +s)"
date: 2011-02-07
forum: General Help
---

### Post by MSPdwalt on 2011-02-07
I recently deployed an Ubuntu server instance in Amazon Ec2 for one of my clients, they are using it for a QA server for their web apps and their subversion repositories.

I have setup vsftpd with FTPES using this [helpful tutorial]("http://ubuntuforums.org/showthread.php?t=518293") (Just remember to generate the cert) And that is how their developers post sites to QA (users home directory is my doc root)

They have have a few people internally they would like to be able to add users to the system.  I would like these people to be normal users without sudo access, but I would like them to be able to add users using this shell script:

```

#!/bin/bash

# This script is intended to allow customer admins to add new users to the Ec2 server for FTP access

# Prompt's for username and populates the username variable with the response
echo -e "Please enter the username you would like to create: \c"
read username

# Creates the user with the appropriate group membership and home directory for FTPES with VSFTPD

useradd sudo useradd $username -d /web/demo/ -G www-data

echo "Type the users password, you will not see any asterisks as you type, you will be prompted to confirm it"

# Sets the password for the new user account

echo `passwd $username`

echo "If your passwords did not match run ./userpassreset for the user you just created"

echo "Done"


```

I was under the impression that ```
chmod +s
``` should allow me to accomplish this.  I have added my customer admins to a gorup called custadmins and the permissions on my script are:

```
-rwSr-S--- 1 root     custadmins   751 2011-02-07 18:50 newuser
```

when I login as one of my custadmins and issue ```
./newuser
``` or ```
sh newuser
``` I get access is denied.

Am I going about this the wrong way?  Any suggestions would be greatly appreciated.

---

### Post by hawkmage on 2011-02-07
Notice that the S is upper case, this indicates that the execute bit is not set, normily you need both the execute bit set as well as the SUID/SGID bit for it to work.

---

### Post by MSPdwalt on 2011-02-07
I removed the duplicate sudo add user (gotta watch my copy and pastings) lol and I did a ```
chmod u+x 
chmod g+x
-rwsr-s--- 1 root custadmins 738 2011-02-07 20:59 newuser

```

now I can execute it, but the script doesn't appear to be running as root. I still get can't lock /etc/passwd

---

### Post by asmoore82 on 2011-02-07
Shell scripts are not allowed to be setuid. It is a massive security hole.

The proper thing to do is configure the `sudo` system to allow their accounts to add users.
`sudo` provides fine grained control so that you can allow only specific accounts
to do specific administrative actions. `sudo` also nicely logs everything
that these limited admin accounts do.

You should never run authenticated FTP over the wide internet unless it is protected
within an SSH Tunnel or other strong encryption. To that end, it's usually much
easier to dump FTP altogether and use the builtin sFTP features of openssh-server.
Using sFTP is a one-step process: `sudo apt-get install openssh-server`.
Also, you can connect to sFTP from the modern Gnome desktop as easy as
"Places -> Connect to Server" -> "Service type -> SSH"

IMHO, even with encryption, the only thing you should ever use old fashioned
port 21 FTP for is anonymous read-only access - in other words, a public download server.

---

### Post by MSPdwalt on 2011-02-07
Thanks for the info asmoore82.  I am using FTPES (FTP over explicit SSL) the client demanded FTP (they use filezilla) so I demanded encryption.  Any useful links on sudo?[URL="http://ubuntuforums.org/member.php?u=341737"][COLOR=Black][/COLOR]
[/URL]

---

### Post by asmoore82 on 2011-02-07
> **MSPdwalt said:**
> Thanks for the info asmoore82.  I am using FTPES (FTP over explicit SSL)
That's good

> **MSPdwalt said:**
> the client demanded FTP (they use filezilla) so I demanded encryption.
filezilla supports sFTP "out of the box" - just use port 22 and quickconnect.

> **MSPdwalt said:**
> Any useful links on sudo?
```
man sudoers
```
:D Sorry, I couldn't resist.

---

### Post by MSPdwalt on 2011-03-16
The sudoers man page as with most man pages is useless until after you have a basic understanding of the command/file you're trying to use.

I found some more useful links here:

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

---

