---
title: "creating limited user for vsftpd"
date: 2011-02-04
forum: General Help
---

### Post by ddosterschill on 2011-02-04
so i've seen dozens of threads describing how to create various account types and how to do so for the purpose of securing vsftpd, however, after trying this myself i've encountered nothing but problems. here's what i'm trying to do:

create a user for vsftpd that can
[LIST]
[*]access my media drive(s), both internal and external
[*]upload to a specific folder on a specific drive
[*]be secured by a password and encryption
[*]not do much of anything else
[/LIST]

it's not even necessary that this user be local or have any kind of local privileges, e.g. be able to login or have shell access.

any help or even a link would be greatly appreciated. also im a new linux convert from windows. thanks for the great environment and programs.

dd

---

### Post by ddosterschill on 2011-02-10
Bump. Any help or general direction would be greatly appreciated.

---

### Post by asmoore82 on 2011-02-10
If you just want security and encryption, you can remove/purge all traces
of vsftpd and just install openssh-server.
```
sudo apt-get install openssh-server
```
The installs the SSH remote login services and opens only 1 port - #22.
But, SSH also gets used as a secure tunnel for many other services:
it's the default transport for modern versions of `rsync`;
and the one you want is - sFTP.

You can connect to this from any modern Gnome Desktop with
"Places -> Connect to Server" => "Service Type -> SSH"

And you can also connect from any Linux/Windows system with Filezilla.
Just tell Filezilla port 22 and it will know what to do.

The only reason for using plain old port 21 FTP these days is for
anonymous read-only access - in other words, a public download server.

---

### Post by ddosterschill on 2011-02-10
great advice asmoore82. this is exactly the info i was looking for. in fact, in my down time at school i've already implemented your suggestion. however, this leaves me with my corollary question: how do i create a user account specifically for sftp?

the thing is i'd like to give some specific users access to my content without enabling the whole world to do the same. 

also, my fixation with local user accounts is partially due to a desire to better understand account permissions and develop some sys admin skills. once again, any help is much appreciated. thanks!

dd

---

### Post by asmoore82 on 2011-02-10
You can just create limited User accounts and they will have sFTP access.

They will be able to use the entire filesystem with the limited privileges
of their account. This also gives them the ability to log in to your machine
with SSH and get a shell. To restrict this, you could make these changes
to "/etc/ssh/sshd_config"

Change this line:
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
to this:
```
Subsystem sftp internal-sftp
```

And assuming the user account is sftpuser, add this to the end:
```
Match User sftpuser
  X11Forwarding no
  AllowAgentForwarding no
  AllowTcpForwarding no
  ForceCommand internal-sftp
```

You could also Chroot them if you wanted to, but I think that
might be overkill - assuming these are friends of yours.

---

