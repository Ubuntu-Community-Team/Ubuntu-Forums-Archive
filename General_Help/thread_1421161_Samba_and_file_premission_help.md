---
title: "Samba and file premission help"
date: 2010-03-03
forum: General Help
---

### Post by bone2006 on 2010-03-03
I have a box that scans a bunch of stuff and it saves the files on my ubuntu server.  So I installed samba on my ubuntu server.  So my scanning box has loggin called scanner and I used the information below.

[Shared]
    path = /home/shared/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = scanner
    force group = scanner

I have /home/shared/ set as 777 and user/group was nobody/nogroup.

Right now all the windows machines are logging in with username scanner.  But I'd like each machine to have certain permissions with their own login.

So scanner box single login and dumps pdf files in /home/shared/user1 /home/shared/user2 .....etc

But right now we're all using the scanner login and password.  I want user1 to only be able to access user1 info and user2 only to access their own folder.

Any help is greatly appreciated.

---

### Post by tad1073 on 2010-03-03
you need to add the users to your fileshare machine, then you set different permissions

---

### Post by bone2006 on 2010-03-04
> **tad1073 said:**
> you need to add the users to your fileshare machine, then you set different permissions 

Just to be clear, there's only one Linux ubuntu server machine.  The scanning is an embedded machine.   All the users are on the ubuntu machine already including creating users for samba with

smbpasswd –a user1

The config file for samba that I posted seems to force a user and group.

---

### Post by FiveSidedPoly on 2010-03-04
What I think tad1073 was trying to point to point you in the right direction.
 
Do you have the user1 and user2 accounts the same as they are on the windows machines?  Because if both Windows users login with "scanner" then they inherit the permissions of "scanner" only right now.
  
Your config file is forcing a user and group (scanner) and the second permissions you mentioned are forcing a different user and group (nobody).
 
[Shared]
path = /home/shared/
valid users = %S
browseable = no
read only = no
guest ok = no
create mask = 0770
directory mask = 0770
 
This should allow only the actual user to see and access their own folder inside /home/shared.  This is if say user1 logins Windows with the "user1" login name, they will see the "user1" folder.
 
Now I know that this isn't exactly what you want, but it may help you move in the right direction, because before you start adjusting groups and folder permissions I suggest you make sure that each user can access his folder only.

---

### Post by bone2006 on 2010-03-06
> **FiveSidedPoly said:**
> What I think tad1073 was trying to point to point you in the right direction.
 
Do you have the user1 and user2 accounts the same as they are on the windows machines?  Because if both Windows users login with "scanner" then they inherit the permissions of "scanner" only right now.
  
Your config file is forcing a user and group (scanner) and the second permissions you mentioned are forcing a different user and group (nobody).
 
[Shared]
path = /home/shared/
valid users = %S
browseable = no
read only = no
guest ok = no
create mask = 0770
directory mask = 0770
 
This should allow only the actual user to see and access their own folder inside /home/shared.  This is if say user1 logins Windows with the "user1" login name, they will see the "user1" folder.
 
Now I know that this isn't exactly what you want, but it may help you move in the right direction, because before you start adjusting groups and folder permissions I suggest you make sure that each user can access his folder only.

Thank you so much for the reply.  I guess with the permissions, I'm not even sure why I have anybody with 7 as wouldn't that allow for write, read and execute? 

I really don't know what create mask means?  I do see my original says 640, which should be user read/write, group read and everybody else nothing.  I'd imagine I would want I would want this, since I really don't want file execution on samba file sharing...am I correct?

Also, why did you change browseable to no? 

I was thinking about this after your post:

[Shared]
path = /home/shared/
browseable = yes
read only = no
guest ok = no
create mask = 0640
directory mask = 0640

It appears if I do adduser that each user has it's own group.  So I put the user scanner in everyboy's group.  So user1 has a group called user1 as well.  That group has user1 and scanner as well.  So that scanner can read/write to that directory and therefore scanner and only user1 can read/write to that directory.

I haven't done this yet, but I think you guys have me on the right direction.

---

### Post by FiveSidedPoly on 2010-03-07
Well I glad that everything is helping you move in the right direction, file sharing always takes quite a bit of trial and error until it is perfect, especially with large networks with lots of users needing complex sharing permissions.  I'm not expert at Samba yet, still quite new myself, but I have used it enough to at least confuse you more. kidding  ;)
 
This is partially why I recommended 0770, even possibly 0777, because this will help you figure out if any users can access it the way you have it now.  It is better/easier to have it open and slowly lock it down then do the reverse.  0640 would be really great in the end, keeping "group" permissions at read/write won't hurt either, especially if you add users to multiple groups and what not.  You can leave it at 0640 to play it safe while you work things out too.
 
I have noticed that when working some file types in a share that leaving file execution on at least for the owner is nice, executing is not just for running a program.  You can leave it off until or if you notice issues.
 
I suggested the setting of "browseable to no" because I had noticed before that if I set it to "yes" then inside the share drive/partition that it shows the home folder as well.  But since using "%S" as valid users only allows the actual user signed in to see their home folder (/home/user1 for example) it seems wasteful to have them open the home folder to see only their shared folder.  Does this make sense?  What it does is make the top folder "home" with the user folder inside of it.  No need to show the "home" folder, just the one the user cares about.  You can change it if your folder structure changes and it is worthwhile.
 
You are correct that adduser does create a group for the user named after the user.  This helps with when you create the user "scanner" because then you don't have to manually create a "scanner group".   You can always add a user to more groups if needed and even create new groups to fit your need.  If you don't know how, below is an example.
 
      sudo addgroup scanner
      
      sudo adduser user1 scanner  (sudo adduser "username" "groupname")
 
 
You can also add the name of a user in the smb.conf after the "valid users =" for specific shares too.
 
You may only want to have scanner only with write access, because if it may allow user1 to also read user2's files. 
 
 
If you haven't checked these resources out, I recommend you do, sorry I should have linked them earlier.
 
[Official Ubuntu Server Guide- Samba portions]("http://https://help.ubuntu.com/9.10/serverguide/C/windows-networking.html")
 
[HowTo: Setup Samba thread by Stormbringer]("http://http://ubuntuforums.org/showthread.php?t=202605")
 
 
I have enjoyed working with Ubuntu Server + Samba, quite more then working 1000+ users with 1000+ groups, folders, etc on Win Server 2003, although I only use Samba at home for my 8 computer network.  :)

---

### Post by bone2006 on 2010-03-07
> **FiveSidedPoly said:**
> Well I glad that everything is helping you move in the right direction, file sharing always takes quite a bit of trial and error until it is perfect, especially with large networks with lots of users needing complex sharing permissions.  I'm not expert at Samba yet, still quite new myself, but I have used it enough to at least confuse you more. kidding  ;)
 
This is partially why I recommended 0770, even possibly 0777, because this will help you figure out if any users can access it the way you have it now.  It is better/easier to have it open and slowly lock it down then do the reverse.  0640 would be really great in the end, keeping "group" permissions at read/write won't hurt either, especially if you add users to multiple groups and what not.  You can leave it at 0640 to play it safe while you work things out too.
 
I have noticed that when working some file types in a share that leaving file execution on at least for the owner is nice, executing is not just for running a program.  You can leave it off until or if you notice issues.
 
I suggested the setting of "browseable to no" because I had noticed before that if I set it to "yes" then inside the share drive/partition that it shows the home folder as well.  But since using "%S" as valid users only allows the actual user signed in to see their home folder (/home/user1 for example) it seems wasteful to have them open the home folder to see only their shared folder.  Does this make sense?  What it does is make the top folder "home" with the user folder inside of it.  No need to show the "home" folder, just the one the user cares about.  You can change it if your folder structure changes and it is worthwhile.
 
You are correct that adduser does create a group for the user named after the user.  This helps with when you create the user "scanner" because then you don't have to manually create a "scanner group".   You can always add a user to more groups if needed and even create new groups to fit your need.  If you don't know how, below is an example.
 
      sudo addgroup scanner
      
      sudo adduser user1 scanner  (sudo adduser "username" "groupname")
 
 
You can also add the name of a user in the smb.conf after the "valid users =" for specific shares too.
 
You may only want to have scanner only with write access, because if it may allow user1 to also read user2's files. 
 
 
If you haven't checked these resources out, I recommend you do, sorry I should have linked them earlier.
 
[Official Ubuntu Server Guide- Samba portions]("http://https://help.ubuntu.com/9.10/serverguide/C/windows-networking.html")
 
[HowTo: Setup Samba thread by Stormbringer]("http://http://ubuntuforums.org/showthread.php?t=202605")
 
 
I have enjoyed working with Ubuntu Server + Samba, quite more then working 1000+ users with 1000+ groups, folders, etc on Win Server 2003, although I only use Samba at home for my 8 computer network.  :)

Thank you so much for all the help, I really appreciate it

---

### Post by FiveSidedPoly on 2010-03-07
Not a problem, post again if you need further help.

---

### Post by Gaurav_Ag on 2010-05-17
```

[global]
    ; General server settings
    netbios name = gaurav
    server string =
    workgroup = MQ
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = no
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gaurav
    force group = gaurav

[Florian]
path = /home/samba/Florian
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0770
force user = florian
force group = florian

```

here i'm making each user again and again..
is there any genral way out to make the user their own directory with specific permissions whnever the come....

---

