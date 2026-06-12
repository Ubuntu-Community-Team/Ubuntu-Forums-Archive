---
title: "how to use rsync"
date: 2012-04-09
forum: General Help
---

### Post by winzip on 2012-04-09
I have two box in a LAN. Both have ssh open at port 22.
i have staff.zip at machineA. I want to send this to machineB. How do i use rsync here ?both my system has ubuntu 10.04 server OS edition

---

### Post by papibe on 2012-04-09
Hi winzip.

Let's asume that file is on your home directory, and you have the same user on both systems.

Then in machineA you can transfer the file to machineB by doing:
```
rsync -av  staff.zip  machineB:./
```
You can even get it from machineB like this:
```
rsync -av  machineA:staff.zip  ./
```

Hope that helps, and tell us if you need more help with that.
Regards.

---

### Post by winzip on 2012-04-10
> **papibe said:**
> Hi winzip.

Let's asume that file is on your home directory, and you have the same user on both systems.

Then in machineA you can transfer the file to machineB by doing:
```
rsync -av  staff.zip  machineB:./
```
You can even get it from machineB like this:
```
rsync -av  machineA:staff.zip  ./
```

Hope that helps, and tell us if you need more help with that.
Regards.
Thank you. Could you please tell what does av stands for ? 
yes, both the machine have same user. 
I want to put the file in /home/user directory,. 
what is your machineB here ? Ip only ?

---

### Post by papibe on 2012-04-10
Sure.

-a and -v are rsync options.

-a is like a macro (several options). It preserves time, ownership, and can be use to copy whole directories, not just a file.

-v means verbose so it will display what it's doing. Its benefit will be more obvious when you are transferring several files.

About the machine names...

If you have a DNS on your LAN (like your router), you can use the machine's names. If not, you can use the zero configuration protocol and use a name like this: machineA.local

In case none of that work, you would have to use the machine's LAN IP numbers.

Does that clarify things a bit?
Regards.

---

### Post by winzip on 2012-04-10
> **papibe said:**
> Sure.

-a and -v are rsync options.

-a is like a macro (several options). It preserves time, ownership, and can be use to copy whole directories, not just a file.

-v means verbose so it will display what it's doing. Its benefit will be more obvious when you are transferring several files.

About the machine names...

If you have a DNS on your LAN (like your router), you can use the machine's names. If not, you can use the zero configuration protocol and use a name like this: machineA.local

In case none of that work, you would have to use the machine's LAN IP numbers.

Does that clarify things a bit?
Regards.

Thanks. I still have one query left...
What does 'a' means ?
For example 'v' =verbose.
What does 'a' read ?

---

### Post by riderplus on 2012-04-10
> **winzip said:**
> Thanks. I still have one query left...
What does 'a' means ?
For example 'v' =verbose.
What does 'a' read ?
Hi winzip,

You can check yourself with ```
man rsync
```
Then you should see ```
 Here is a short summary of the options available in rsync. Please refer to the detailed description below for a complete description.

        -v, --verbose               increase verbosity
        -q, --quiet                 suppress non-error messages
            --no-motd               suppress daemon-mode MOTD (see caveat)
        -c, --checksum              skip based on checksum, not mod-time & size
        -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
            --no-OPTION             turn off an implied OPTION (e.g. --no-D)
        -r, --recursive             recurse into directories
        -R, --relative              use relative path names

```...and many other options

---

### Post by winzip on 2012-04-10
I checked your command. It does not work.
I get error.  Unexpected remote arg xxx.xxxx.x.xx.
Syntax or usage error code

---

### Post by Cheesemill on 2012-04-10
Instead of using rsync I would use scp in this situation:
```
scp staff.zip user@machineb:/home/user/
```
Replace user with your username and use either the IP address for machine B or its host name (if you have DNS set up on the network).

---

### Post by winzip on 2012-04-10
> **Cheesemill said:**
> Instead of using rsync I would use scp in this situation:
```
scp staff.zip user@machineb:/home/user/
```Replace user with your username and use either the IP address for machine B or its host name (if you have DNS set up on the network).


I want to use  rsync.

I can trasnfer  file using sftp ..no issue.

but I  want to  know  how to  use rsync  ?    so  thats   my query  and also title of this topic !

---

### Post by lukeiamyourfather on 2012-04-10
> **winzip said:**
> I want to use  rsync.

I can trasnfer  file using sftp ..no issue.

but I  want to  know  how to  use rsync  ?    so  thats   my query  and also title of this topic !

I agree that scp is probably the best option here. If you want to use rsync in the server-client sense typically people use the rsync daemon on the machine accepting connections.

[https://help.ubuntu.com/community/rsync#Rsync_Daemon](https://help.ubuntu.com/community/rsync#Rsync_Daemon)

Also check that the firewall is allowing ssh connections (if the firewall is enabled).

---

### Post by forrestcupp on 2012-04-10
You also might want to check out luckyBackup, which is in the repos. It's a pretty good GUI frontend to rsync.

---

### Post by winzip on 2012-04-10
> **lukeiamyourfather said:**
> I agree that scp is probably the best option here. If you want to use rsync in the server-client sense typically people use the rsync daemon on the machine accepting connections.

[https://help.ubuntu.com/community/rsync#Rsync_Daemon](https://help.ubuntu.com/community/rsync#Rsync_Daemon)

Also check that the firewall is allowing ssh connections (if the firewall is enabled).

There is no firewall issue.

SCP works fine.
SSH works fine.
SFTP works fine.
RSYNC does not work.

How to use rsync to send a zip file from  one machine to another ?  Whats is the correct command to transfer files  using rsync ? Or it can not be done using rsync ?

---

### Post by papibe on 2012-04-10
Could you post the actual command that you are using, and the paste the errors too?

Regards.

---

### Post by winzip on 2012-04-10
> **papibe said:**
> Could you post the actual command that you are using, and the paste the errors too?

Regards.

I used the same command  format  posted by you.

*rsync -av  staff.zip  machineB:./*

I   put  real  IP address in place of machineB.

I   put  /home/user  in place of ./

thats all.

I get error:   Unexpected remote arg <IP Address >
Syntax or usage error

---

### Post by papibe on 2012-04-10
> **winzip said:**
> Syntax or usage error
There's something you are missing. It is very difficult to guess without seeing it myself.

If you are rsyncing inside your LAN, there's no security risk to paste what you are doing. For example this kind of addresses:
[LIST]
[*]192.168.1.0 / 255.255.255.0
[*]172.16.0.0 / 255.255.0.0
[*]10.0.0.0 / 255.255.0.0
[/LIST]
are LAN addresses. We all have them. There's no problem in paste it them here. 

Regards.

---

### Post by forrestcupp on 2012-04-10
If you edit /etc/fstab to mount your network directory locally, you can use the luckyBackup GUI frontend to rsync, and never have to worry about any commands.

---

### Post by winzip on 2012-04-11
> **forrestcupp said:**
> If you edit /etc/fstab to mount your network directory locally, you can use the luckyBackup GUI frontend to rsync, and never have to worry about any commands.

Thanks. However i am using ubuntu 10.04 server os. It has no gui.

---

### Post by winzip on 2012-04-11
> **papibe said:**
> There's something you are missing. It is very difficult to guess without seeing it myself.

If you are rsyncing inside your LAN, there's no security risk to paste what you are doing. For example this kind of addresses:
[LIST]
[*]192.168.1.0 / 255.255.255.0
[*]172.16.0.0 / 255.255.0.0
[*]10.0.0.0 / 255.255.0.0
[/LIST]
are LAN addresses. We all have them. There's no problem in paste it them here. 

Regards.

Thanks.
I have transferrer zip file using sftp finally. That was easy and smooth.
Are you sure your command works? 

Can you please check in your box if  the commands working for you .  I exactly followed the command  format  you posted. There is no mistake .

---

### Post by forrestcupp on 2012-04-11
> **winzip said:**
> Thanks. However i am using ubuntu 10.04 server os. It has no gui.

Sorry. I didn't even catch that in the first post.

---

