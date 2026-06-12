---
title: "SAMBA sharing Ubuntu -&gt; Ubuntu"
date: 2011-05-01
forum: General Help
---

### Post by d00derino on 2011-05-01
Howdy guys,

I've been Googling this for days and haven't found a solution that works. Most of the stuff available on the Internet is >2008, and I know there have been serious changes to SAMBA since then.

I use SAMBA to connect my HTPC to my Windows computer, but I also have another Ubuntu computer I'd like to access some files from the SAMBA share onto. What I've found online just didn't work. not to mention there was a huge lack of information available on this topic. It seems everyone wants to use SAMBA to connect Linux to some other OS, but little when you want to go the Linux -> Linux route. 

In any case, I keep getting an "Error 18: Permission denied" type error when I try to use smbmount. I've Googled the error message and all I found didn't apply to my situation. 

I was wondering if there is a more recent, up-to-date guide or an easier way to mount a SAMBA share onto another Linux computer. If not, perhaps I can get some help diagnosed on my problem? Thanks for any help in advance.

---

### Post by Morbius1 on 2011-05-01
Couldn't follow that at all.

From the Ubuntu machine that has the folders you shared post the output of the following commands:
```
net usershare info --long
testparm -s
```From the Ubuntu machine that is trying to access those shares post the output of this command:
```
smbtree
```

---

### Post by d00derino on 2011-05-01
net usershare info --long
```

[if]
path=/home/htpc/Desktop/IF
comment=
usershare_acl=Everyone:R,HTPC\(null):F,
guest_ok=y

```

This was done through the standard Nautilus right-click sharing.

[media] is the share I want to access on the other Ubuntu computer:
```

[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[media]
        path = /media/Repository
        valid users = htpc
        read only = No
        guest ok = Yes

```

smbtree:
```

WORKGROUP
\\HTPC           htpc server (Samba, Ubuntu)
    \\HTPC\if            
    \\HTPC\print$         Printer Drivers
    \\HTPC\media          
    \\HTPC\IPC$           IPC Service (htpc server (Samba, Ubuntu))
\\ERIC-PC        

```

The odd thing is, ERIC-PC isn't the credentials used to get into SAMBA from Windows.

---

### Post by Morbius1 on 2011-05-01
> [media]
        path = /media/Repository
        valid users = htpc
        read only = No
        guest ok = YesYou specified that only one user can access the share. Are you supplying that username: htpc and password from the Ubuntu client?

And did you create a samba password for that user:
```
sudo smbpasswd -a htpc
```On a side note this is only the second time I have ever seen the "null" reference:
> usershare_acl=Everyone:R,HTPC\([COLOR=Blue]null[/COLOR]):F,I didn't understand it in that post and still don't. If you could provide the output of the following command I would appreciate it:
```
ls -al /var/lib/samba/usershares
```

---

### Post by d00derino on 2011-05-01
```

htpc@htpc:~$ ls -al /var/lib/samba/usershares
total 12
drwxrwx--T 2 root sambashare 4096 2011-04-26 19:00 .
drwxr-xr-x 5 root root       4096 2011-03-29 18:54 ..
-rw-r--r-- 1 htpc htpc        123 2011-04-26 19:00 if

```

Two questions. Do I need to create the htpc user on the client (computer trying to access the share, just to make sure), or supply it? Secondly, what command should I use to log in? The best information I could find on the Internet is still hard to follow, as is the man page for smbmount. For example, this is the best "lead" I have to mounting from SAMBA:

```

smbmount "\\\\samba1\\customers" -U rtg2t -c 'mount /customers -u 500 -g 100'
```

And the text doesn't really go into detail on what it means.

---

### Post by Morbius1 on 2011-05-01
> Do I need to create the htpc user on the client (computer trying to access the share, just to make sure), or supply it?No. The server needs that username to grant access so it can be done from any machine.
> Secondly, what command should I use to log in?Don't use any command. If the client is Ubuntu Gnome then just go to Nautilus> Network > ....

Or if you want a command:
```
nautilus smb://htpc
```

---

### Post by d00derino on 2011-05-01
> **Morbius1 said:**
> No. The server needs that username to grant access so it can be done from any machine.
Don't use any command. If the client is Ubuntu Gnome then just go to Nautilus> Network > ....

Or if you want a command:
```
nautilus smb://htpc
```

For some reason, I can't connect using the proper credentials. The same ones I use on Windows are just not getting through the prompt in Nautilus. And I have the proper workgroup: WORKGROUP:

```

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (htpc server (Samba, Ubuntu))
        media           Disk
        print$          Disk      Printer Drivers
        if              Disk
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

        Server               Comment
        ---------            -------
        ERIC-PC
        HTPC                 htpc server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        MSHOME               USER-F48E18CBD5
        WORKGROUP            HTPC

```

GAH! So, I thought the correct course of action would be to create a new SAMBA user the name of my Linux client I want to access files from. Now, I get one step further, but two steps back. When I enter the new user "slave" (fitting for a broken down "bedside" laptop, no?), I can log in but then it says *Unable to mount location: Failed to mount Windows share*. I want to rip my hair out!

```


[media]
        path = /media/Repository
        valid users = htpc, slave
        read only = No
        guest ok = Yes

```

---

### Post by Morbius1 on 2011-05-01
Do you have static ip addresses on all these machines? There is an easy way out of this if you do.

---

### Post by d00derino on 2011-05-01
I don't think so. I just know it as 192.168.1.4, but I do have domain linked to my network IP, and already use it to remote SSH and BitTorrent, so if I need to forward a port I can certainly do that.

---

### Post by Morbius1 on 2011-05-01
Sorry, missed something in your earlier post. "Failed to mount" is usually not a samba issue it's a Linux file permissions issue. Run the following command on the server:
```
 sudo chmod 777 /media/Repository
```
No need to restart samba.

---

### Post by d00derino on 2011-05-01
It still isn't working, and I recursively did it as well.

---

### Post by Morbius1 on 2011-05-01
Set the share to allow guests , force the user to be htpc, and restrict access to the clients by hostname:

> [media]
path = /media/Repository
hosts allow = hostname1, hostname2
force user = htpc
read only = No
guest ok = YesWhere hostname1 is the Windows machine and hostname2 is the other Linux machine. 

[COLOR=Blue]**EDIT:**[/COLOR] The hostnames have to be in lower case I think - it's been a while since I did this by hostname.

Then restart samba:
```
sudo service smbd restart
```Doing things by hostname with samba can be tricky - it would be better by ip address - but give it a shot.

---

### Post by bobwyajnr on 2011-05-01
> **d00derino said:**
> 
```


[media]
        path = /media/Repository
        valid users = htpc, slave
        read only = No
        guest ok = Yes

```


Ah I feel your pain bro! Just been through nearly 24 hours of hell getting my own Samba setup to work.

The users listed in smb.conf must be valid Ubuntu user names (lower case, etc.) and be **seperated by spaces** - this appears to be a bug in the **testparam** utility (which completely ignores this syntax error). Literally was tearing my hair out till I released I had made this error! ](*,)](*,)](*,)

Don't bother with Nautilus for anything - it's pretty useless. **smbclient** is far more useful on the commandline (especially for debugging) e.g.
```
$ smbclient //htpc/media -Uhtpc
```
Which I presume you already are trying on your client Linux-based machine (??)
I tend to use the **mount.cifs** command (or **fstab**) for more permanent share mounting. KDE (Dolphin) has fairly decent Samba support in comparison to Gnome (i.e. it actually works!)

Also it's worth checking:
```
/var/log/samba/samba.log
```
on the HTPC machine. Bump up the loglevel (**smb.conf** parameter) if necessary. The Samba logs are actually quite useful - I have found anyway!

I even went as far as playing about with **wireshark**. It would be perhaps more useful for diagnosing fire-walling type networking issues... Anyway it's in my toolkit for being so well written/powerful!

Hope that helps bit! Remember to sleep! :popcorn:

Bob

---

### Post by d00derino on 2011-05-01
I have the users separated by space in smb.conf, just when you print out the testparms it separates them by comma. *smbclient* works, but it won't let me do anything within it. I get NT_STATUS_ACCESS_DENIED errors.

---

### Post by Morbius1 on 2011-05-01
If your share looks like this:
> [media]
path = /media/Repository
hosts allow = hostname1, hostname2
force user = htpc
read only = No
guest ok = Yes 			 		
There is no request by the server for credentials. It's a guest share. The only thing the sever will check is to see if the requester is from hotname1 or hostname2.

Please post the output of the following:
```
ls -al /media/Repository
```

---

### Post by d00derino on 2011-05-01
> **Morbius1 said:**
> If your share looks like this:

There is no request by the server for credentials. It's a guest share. The only thing the sever will check is to see if the requester is from hotname1 or hostname2.

Please post the output of the following:
```
ls -al /media/Repository
```

I changed the hostname bit back because it stopped Windows from working, but I left guest ok = yes

```
drwx------ 1 htpc htpc  24576 2011-04-22 05:46 .
drwxr-xr-x 3 root root   4096 2011-04-26 21:12 ..
drwx------ 1 htpc htpc      0 2010-05-28 21:40 Backup
drwx------ 1 htpc htpc 524288 2010-05-30 23:21 Fonts
drwx------ 1 htpc htpc      0 2011-01-30 19:53 Graphic Assets
drwx------ 1 htpc htpc      0 2011-03-13 20:45 $RECYCLE.BIN
drwx------ 1 htpc htpc      0 2010-05-29 01:24 System Volume Information
drwx------ 1 htpc htpc      0 2011-04-26 21:08 .Trash-1000

```

---

### Post by Morbius1 on 2011-05-01
Bingo.
```
sudo chmod 777 /media/Repository
```If that doesn't change it to 777 is this an NTFS or FAT32 partition?

---

### Post by bobwyajnr on 2011-05-01
> **d00derino said:**
> I have the users separated by space in smb.conf, just when you print out the testparms it separates them by comma. *smbclient* works, but it won't let me do anything within it. I get NT_STATUS_ACCESS_DENIED errors.

OK I don't want to be rude but you need to post the command and full error directly from the terminal - if you want anyone to be actually able to help you.

Case in point, on my client machine, I type:
```
$ smbclient "//192.168.1.1/Home" -Uguest
Enter guest's password: 
Anonymous login successful
Domain=[ARGYLE-STREET] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_LOGON_FAILURE

```
Now what has happened there? I allow anonymous/guest logins. I login correctly to the Samba server. I then try to access the **Home** share which only allows my user account to access it. At this point I get the **NT_STATUS_LOGON_FAILURE** - as I would expect.

Like I said (previously) add the line:
```
log level = 2

```
to your *smb.conf* file [Global] section.
Give us a dump of the end of your /var/log/samba/samba.log file e.g.
```
$ cat /var/log/samba/samba.log | tail -n 100
```
just after you have tried the **smbclient** command on the other machine.

Remember to give us as much information/detail as you able to!
Debugging Samba problems takes the patience of a saint and lots of rest/ frequent breaks. Otherwise you will just hit a brickwall of frustration and exhaustion - like I did here! ](*,)

Bob

---

### Post by d00derino on 2011-05-01
> **Morbius1 said:**
> Bingo.
```
sudo chmod 777 /media/Repository
```If that doesn't change it to 777 is this an NTFS or FAT32 partition?

I have no idea how to tell, but I did start it with Windows.

Edit: Dur, I'm an idiot today. It's NTFS.

---

### Post by Morbius1 on 2011-05-01
Lets make this as simple as possible. Go back to the share definition again and make it a pure guest share but forcing the user to htpc:
> [media]
path = /media/Repository
force user = htpc
read only = No
guest ok = Yes 			 		

THen restart samba:
```
sudo service smbd restart
```

Everyone and your Aunt Agnes should now have access to that share. 
And no one should be asked for credentials. 

Are you still being requested for authentication?

---

### Post by d00derino on 2011-05-01
> **bobwyajnr said:**
> OK I don't want to be rude but you need to post the command and full error directly from the terminal - if you want anyone to be actually able to help you.

Case in point, on my client machine, I type:
```
$ smbclient "//192.168.1.1/Home" -Uguest
Enter guest's password: 
Anonymous login successful
Domain=[ARGYLE-STREET] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_LOGON_FAILURE

```
Now what has happened there? I allow anonymous/guest logins. I login correctly to the Samba server. I then try to access the **Home** share which only allows my user account to access it. At this point I get the **NT_STATUS_LOGON_FAILURE** - as I would expect.

Like I said (previously) add the line:
```
log level = 2

```
to your *smb.conf* file [Global] section.
Give us a dump of the end of your /var/log/samba/samba.log file e.g.
```
$ cat /var/log/samba/samba.log | tail -n 100
```
just after you have tried the **smbclient** command on the other machine.

Remember to give us as much information/detail as you able to!
Debugging Samba problems takes the patience of a saint and lots of rest/ frequent breaks. Otherwise you will just hit a brickwall of frustration and exhaustion - like I did here! ](*,)

Bob

My mistake.

```

slave@linux-dev:~$ smbclient //htpc/media -Uslave
Enter slave's password:
Domain=[WORKGROUP] OS=[UNIX] Server=[Samba 3.5.4]
smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*
smb: \> cd Backup
cd \Backup\: NT_STATUS_ACCESS_DENIED

```

Also, there is no log that was created on the server machine.

---

### Post by d00derino on 2011-05-01
> **Morbius1 said:**
> Lets make this as simple as possible. Go back to the share definition again and make it a pure guest share but forcing the user to htpc:


THen restart samba:
```
sudo service smbd restart
```

Everyone and your Aunt Agnes should now have access to that share. 
And no one should be asked for credentials. 

Are you still being requested for authentication?

This works! w00t! Small victories! :)

I would still like to password protect the share. Probably would just turn guest off then, right? I just enabled logging (I'm sorry, I missed enabling it before), but since there are no errors now the file isn't created yet.

---

### Post by Morbius1 on 2011-05-01
Let's go one step up. Change the hosts allow to an ip address - just one this time - to see if it works:
```
[media]
path = /media/Repository
hosts allow = 192.168.0.100
force user = htpc
read only = No
guest ok = Yes 
```Change 192.168.0.100 to the ip address of linux-dev.

Then restart samba again.

Is it still a seamless access?

[COLOR=Blue]EDIT: And it should also deny access to the Windows box, BTW.[/COLOR]

---

### Post by bobwyajnr on 2011-05-01
> **d00derino said:**
> This works! w00t! Small victories! :)

I would still like to password protect the share. Let me enable logging and post the .log file for you.

Well the **slave** user could login but not see the folders or files because well the file access was Read/Write/Execute only for the **htpc** user! You could probably turn of guest access again.

I think you probably want *755* for the file/folder access mask? Or do you want to give the **slave** user write access to the shares??

Bob

---

### Post by d00derino on 2011-05-01
> **Morbius1 said:**
> Let's go one step up. Change the hosts allow to an ip address - just one this time - to see if it works:
```
[media]
path = /media/Repository
hosts allow = 192.168.0.100
force user = htpc
read only = No
guest ok = Yes 
```Change 192.168.0.100 to the ip address of linux-dev.

Then restart samba again.

Is it still a seamless access?

[COLOR=Blue]EDIT: And it should also deny access to the Windows box, BTW.[/COLOR]

Yes, on both accounts.

---

### Post by d00derino on 2011-05-01
> **bobwyajnr said:**
> Well the **slave** user could login but not see the folders or files because well the file access was Read/Write/Execute only for the **htpc** user! You could probably turn of guest access again.

I think you probably want *755* for the file/folder access mask? Or do you want to give the **slave** user write access to the shares??

Bob

I want slave to read only, not write.

---

### Post by Morbius1 on 2011-05-01
OK, now add the other ip address:
> [media]
path = /media/Repository
hosts allow = 192.168.0.100, 192.168.0.101
force user = htpc
read only = No
guest ok = YesThen restart samba yet again.

If this all works you will need to give your machines static ip addresses or else they might change the next time those machines boot. There's a way to do that within the os itself but I it's unnecessarily difficult to do for some reason. I use DHCP Reservation on my router to give a specific address to a specific machine. See if your router has this capability.

To answer your late addition to your earlier post: Yes you should have been able to to say guest = no and prompt for credentials but you have to make sure that the client user is a local user on the server and then assign him a samba password.

---

### Post by Morbius1 on 2011-05-01
> I want slave to read only, not write.
Your killin' me :P

Do you want one remote user to have write access and one read only. That can be done - just want to know.

---

### Post by d00derino on 2011-05-01
> **Morbius1 said:**
> Your killin' me :P

Do you want one remote user to have write access and one read only. That can be done - just want to know.

Never-mind, for some reason now it works if I log in as htpc on the slave computer. I just...I just don't get it...

Thanks for all the help guys!

---

### Post by Morbius1 on 2011-05-01
If you ever have to go through this again you might want to nip the bud at the source of the problem and automount that NTFS partition ( hopefully it's an internal partition ) with a set of permissions allowing better samba compatibility. You would do that in fstab. Once set in fstab you can then set up a Samba share definition that will allow all kinds of remote user restrictions for access. But that's another topic :wink:

---

### Post by bobwyajnr on 2011-05-01
> **d00derino said:**
> Never-mind, for some reason now it works if I log in as htpc on the slave computer. I just...I just don't get it...

Thanks for all the help guys!

```
drwx------ 1 htpc htpc  24576 2011-04-22 05:46 .
drwxr-xr-x 3 root root   4096 2011-04-26 21:12 ..
drwx------ 1 htpc htpc      0 2010-05-28 21:40 Backup
drwx------ 1 htpc htpc 524288 2010-05-30 23:21 Fonts
drwx------ 1 htpc htpc      0 2011-01-30 19:53 Graphic Assets
drwx------ 1 htpc htpc      0 2011-03-13 20:45 $RECYCLE.BIN
drwx------ 1 htpc htpc      0 2010-05-29 01:24 System Volume Information
drwx------ 1 htpc htpc      0 2011-04-26 21:08 .Trash-1000
```

That file permissions setup literally means:
User: **htpc** (Group: **htpc**) - Read, Write, Execute
_All other users_: no access

You could probably put that IP address (**hosts allow**) in as:
```
192.168.0
```
i.e. allow the whole subnet... Unless you are really paranoid!

Glad you got your problem sorted anyway!

Bob

---

### Post by d00derino on 2011-05-02
> **bobwyajnr said:**
> ```
drwx------ 1 htpc htpc  24576 2011-04-22 05:46 .
drwxr-xr-x 3 root root   4096 2011-04-26 21:12 ..
drwx------ 1 htpc htpc      0 2010-05-28 21:40 Backup
drwx------ 1 htpc htpc 524288 2010-05-30 23:21 Fonts
drwx------ 1 htpc htpc      0 2011-01-30 19:53 Graphic Assets
drwx------ 1 htpc htpc      0 2011-03-13 20:45 $RECYCLE.BIN
drwx------ 1 htpc htpc      0 2010-05-29 01:24 System Volume Information
drwx------ 1 htpc htpc      0 2011-04-26 21:08 .Trash-1000
```

That file permissions setup literally means:
User: **htpc** (Group: **htpc**) - Read, Write, Execute
_All other users_: no access

You could probably put that IP address (**hosts allow**) in as:
```
192.168.0
```
i.e. allow the whole subnet... Unless you are really paranoid!

Glad you got your problem sorted anyway!

Bob

I kind of am, someone hacked into my machine once...some weird IP remotted in somehow. Of course, we weren't using any kind of wireless protection because my brother can't get his DS online if we have a WPA. I also got caught by my ISP for downloading a movie I own (The Dark Knight) because I can't use the digital copy on Linux based machines, so I thought that it might have been them trying to check my machine, which I don't think is or should be legal at all considering I have tax information backed up and stuff, so I'm a bit paranoid, whether that one case was an isolated incident of a neighbor trying to be cute or something more sinister. 

Either way, I think my problem might have been the htpc user's password. I reset it to see if it would work after I could log in as slave, and that seemed to do it. Odd, considering I use the same password for both, but nevertheless, it works now. 

Thanks again!

---

### Post by Morbius1 on 2011-05-02
I'm glad you sorted this out this was getting weird.

On the "hosts allow" issue:
> You could probably put that IP address (**hosts allow**) in as:
     Code:
     192.168.0 
i.e. allow the whole subnet... Unless you are really paranoid!I think bobwyajnr misunderstood where I was going with that particular rat hole.

If you want to restrict access to a particular share you can do it the traditional way with users and passwords the way you have done it. The way I was suggesting do it was to make a guest share and then use "hosts allow" to restrict which remote machine is allowed access.

So if you have 4 machines on the network you can create one share and use say .. "hosts allow = 192.168.0.100, 192.168.0.102" Then create another share with a "hosts allow = 192.168.0.101". No more users and no more passwords.

Making "hosts allow = 192.168.0." ( and by the way it has to have a trailing "." if you're only using part of the ip address ) would let the whole lan in which it's doing anyway.

Anywho, all of this will only work if you give each machine a static ip address and each machine belongs to only one person.

I'm sorry but if you have the time - I am fixated on one thing that has nothing to do with this thread and that's this:
> [if]
path=/home/htpc/Desktop/IF
comment=
usershare_acl=Everyone:R,HTPC\([COLOR=Blue]null[/COLOR]):F,
guest_ok=y Still trying to figure out why usershares is placing a "null" in that thing as apposed to htpc which it should be doing. Does the htpc machine boot into that user without you having to enter a password by any chance?

---

### Post by bobwyajnr on 2011-05-02
> **d00derino said:**
> Of course, we weren't using any kind of wireless protection because my brother can't get his DS online if we have a WPA.

Really, really bad idea. Someone can easily spoof an LAN IP address to get around this protection. SMB/CIFS should never be used over an insecure network. Good ol' ethernet cable is always first choice for home networking. Failing that perhaps some homeplugs (which network over the ring mains) would work for you guys... Even a second Wireless Access Point for the DS (with no security enabled) - just to access the internet (with no LAN access)...

Get some help if you're not up on home networking. You're asking for trouble if you leave your setup open like this. :(

Bob

---

### Post by bobwyajnr on 2011-05-02
> **Morbius1 said:**
> 
On the "hosts allow" issue:
I think bobwyajnr misunderstood where I was going with that particular rat hole.

If you want to restrict access to a particular share you can do it the traditional way with users and passwords the way you have done it. The way I was suggesting do it was to make a guest share and then use "hosts allow" to restrict which remote machine is allowed access.



I would highly recommend for anyone not rely on this 'feature'! Encrypted passwords for any accounts with R/W Samba share access (or shares containing sensitive information) is the only way to go! Someone could easily sit on **d00derino**'s open WiFi and have a merry old time in WireShark, etc.! Spoofing IP addresses on an open LAN is not too difficult!

The Ubuntu community does not want to start going to the road of many Windows users - neglecting basic security precautions is a really bad idea! I for one don't think it's a good idea to hand out this kind of advice to newbie Linux users!

Just my $.02! :popcorn:

Bob

---

### Post by d00derino on 2011-05-02
> **Morbius1 said:**
> 
I'm sorry but if you have the time - I am fixated on one thing that has nothing to do with this thread and that's this:
Still trying to figure out why usershares is placing a "null" in that thing as apposed to htpc which it should be doing. Does the htpc machine boot into that user without you having to enter a password by any chance?

You hit the nail on the head -- the HTPC machine boots straight into the user. It's something that bothers me on the default settings, even though I understand why it's there. Normally I have one user per computer and think it's asinine how many times I need to already put in my password. I get the security enhancements, but sometimes I think it's just a waste of time.

---

### Post by d00derino on 2011-05-02
> **bobwyajnr said:**
> Really, really bad idea. Someone can easily spoof an LAN IP address to get around this protection. SMB/CIFS should never be used over an insecure network. Good ol' ethernet cable is always first choice for home networking. Failing that perhaps some homeplugs (which network over the ring mains) would work for you guys... Even a second Wireless Access Point for the DS (with no security enabled) - just to access the internet (with no LAN access)...

Get some help if you're not up on home networking. You're asking for trouble if you leave your setup open like this. :(

Bob

Oh, trust me, it's fixed. Sometimes the family dynamic goes awry, and the loudest yeller gets his way. In this case, it was my brother so he could play Pokemon with his friends. I'm pretty upset that Nintendo never released a firmware update that allows access to a network secured with WEP. Or maybe they have, and he never got it. The only free time I have for video games is spent on Mortal Kombat.

I would love to read some Networking tutorials for myself; kind of learn how to be a Sysadmin without having to go back to school. Not for gain, but just as an interest. I figure if I put it out there, maybe someone can point me in the right direction. I've read up on network protocols and how TCP/IP works, but like, where's all the BASH scripts and fun coding stuff that I assume Network Administrators learn?

Again, thanks again everyone!

---

### Post by Morbius1 on 2011-05-02
Thanks for getting back on the "null" question. Like I said it's only come up once before and never got an answer from th OP. I'll add HTPC to my list of things to investigate - it's a long list :)

---

