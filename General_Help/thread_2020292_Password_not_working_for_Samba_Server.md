---
title: "Password not working for Samba Server"
date: 2012-07-08
forum: General Help
---

### Post by Jorel on 2012-07-08
Hi guys,,
 
i need help, im having trouble with my Samba server, i cannot connect with my user and password using my Windows machine, i cannot trace what went wrong, i already added "acl", adduser with password, addgroup, changed the write list to a specific group, restarted smbd and nmbd....
 
please help guys,, im having distro headache now..:confused:

---

### Post by Toz on 2012-07-08
Have you run:
```
sudo smbpasswd -a <username>
```
...where <username> is the username that you are trying to connect with? This will create a samba account for the given user and allow a connection to the samba server.

---

### Post by Jorel on 2012-07-09
Hi Toz,, 
 
I tried that but still no good,,
 
in my smb.conf
 
--------------------------------------
[jorel]
browseable = yes
guest ok = no
path = /jorel/samba/jorel
write list = @linux
create mask = 0755
---------------------------------------
 
my group is linux,, am i still missing something?? 
 
i also uncomment the security = user
 
also, is it true that i needed to input the real username of the machine (computer name) that will connect to my server?
 
:confused:
 
thanks in advance..

---

### Post by SlugSlug on 2012-07-09
Do your ```
WORKGROUP
```'s match

---

### Post by Morbius1 on 2012-07-09
Please post the output of the following commands:
```
testparm -s
```
```
ls -al /jorel/samba
```

---

### Post by Jorel on 2012-07-09
Hi guys,
 
@SlugSlug, yes my
[global] 
workgroup = WORKGROUP
 
and all of my Windows machine are in Workgroup.
---------------------------------------- 
@Morbius1
testparm -s 
 
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[jorel]"
Loaded service file OK.
Server role: ROLE_STANDALONE
[global]
server string =%h server (Samba, Ubuntu)
map to guest = Bad User
obey pam restrictions = yes
pam password change = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully*.
unix password sync = yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
[FONT=Calibri][SIZE=3]dns proxy = no[/SIZE][/FONT]
[SIZE=2]usershare allow guests = yes[/SIZE]
[LEFT][SIZE=2]panic action = /usr/share/samba/panic-action %d[/SIZE]
[SIZE=2]idmap config * : backend = tdb[/SIZE][/LEFT]
 
[LEFT][SIZE=2][jorel][/SIZE][/LEFT]
[SIZE=2]comment = files[/SIZE]
[SIZE=2]path = /jorel/samba/jorel[/SIZE]
[SIZE=2]write list = @linux[/SIZE]
[SIZE=2]create mask = 0755[/SIZE]
[SIZE=2]--------------------------------------------[/SIZE]
[SIZE=2]ls -al /jorel/samba[/SIZE]

[SIZE=2]drwxr-xr-x 8 root root 4096 Jul 8 12:04 .[/SIZE]
[SIZE=2]drwxr-xr-x 4 root root 4096 Jul 8 12:03 ..[/SIZE]
[SIZE=2]drwxr-xr-x 2 root linux 4096 Jul 8 12:03 jorel[/SIZE]

[SIZE=2]thats all.....[/SIZE]

---

### Post by Morbius1 on 2012-07-09
Hm... Well as long as you added all the applicable users to the "linux" group and gave them samba passwords then this should all work.

They won't be able to write to the share of course since your linux permissions won't allow it:
>  [SIZE=2]drwx[COLOR=Blue]**r-x**[/COLOR]r-x 2 root linux 4096 Jul 8 12:03 jorel[/SIZE]
You might want to fix that:
```
sudo chmod 0775 /jorel/samba/jorel
```

---

### Post by Jorel on 2012-07-11
Hi Morbius1, 
 
it finally worked but i did is "chmod 0705" and it got what you told me to remove,,
 
drwx---r-x 3 dady linux 4096 Jul 11 10:59 jorel (i wonder why the "root" is changed into "dady"?)
 
but the next problem is i added some users and it can access also my folder but the good thing is that they cannot write on it,, but i wonder on how to restric other users to access other folders??
 
[jorel]
comment = Jorel shared files
browseable = yes
path = /jorel/samba/jorel
guest ok = no
read only = yes
write list @linux
create mask = 0755
 
i added "tristan" as a user on another group...
 
 
--im almost at the end of the tunnel :D--

---

### Post by Morbius1 on 2012-07-11
> it finally worked but i did is "chmod 0705" and it got what you told me to removeFirst, I never told you to remove it I wanted you by using chmod 775 to make it look like this:
> drwxrwxr-x 3 root linuxSecond, If members of the "linux" group are able to write to the share, other than whoever dady is, with permissions set at 705 then this is some kind of parallel universe thing I've seen only in the movies.

And I don't know why root was replaced by "dady" either. Is that a legitimate user on your system?

---

### Post by Jorel on 2012-07-11
thats why i always mess things down,, i overlooked at 775 to 755,, (i also tried 644, 750, 700 ... hope that doesnt ruin my system) anyway, i fixed that and got:
 
drwxrwxr-x 4
 
and now i remember i did "chown -R dady" thats how i replaced "root" to "dady" and dady is one of the users in the group "linux"...
 
but still some users that i made can access the folders that they are not suppose to access.....

---

### Post by Morbius1 on 2012-07-11
By access do you mean read access or read / write access?

This share does not prevent any authenticated remote user from accessing that share. It only specifies that members of the linux group can write to it:
> [LEFT][SIZE=2][jorel][/SIZE][/LEFT]
[SIZE=2]comment = files[/SIZE]
[SIZE=2]path = /jorel/samba/jorel[/SIZE]
[SIZE=2]write list = @linux[/SIZE]
[SIZE=2]create mask = 0755[/SIZE]If you only want members of the "linux" group to access the share then replace "write list" with "valid users":
>  [LEFT][SIZE=2][jorel][/SIZE][/LEFT]
 [SIZE=2]comment = files[/SIZE]
 [SIZE=2]path = /jorel/samba/jorel[/SIZE]
 [COLOR=Blue]**[SIZE=2]valid users = @linux[/SIZE]**[/COLOR]
 [SIZE=2]create mask = 0755[/SIZE]Then restart samba:
```
sudo service smbd restart
```

---

### Post by Jorel on 2012-07-12
WOW!! it worked whahahah i love you guys....:lolflag:
 
Thank you very much for the help... hope you help me also with my other threads, and hoping soon i can help others also...
 
Thank you very much team...

---

### Post by Jorel on 2012-07-14
Hi guys,
 
can i ask additional help here?
 
because i need to jump in one shared folder into another one, but i noticed an error after jumping a couple of folders, that i needed to contact the admin (im the admin though :() before i can write on the folder, so i always restart my machine before i can start running through my shared folders and write on them again.....
 
is there a way to prevent this from happening??
 
[jorel]
comment = sahred file
browseable = yes
path = /jorel/samba/jorel
guest ok = no
write list = @linux
valid users = @linux
create mask = 0755
 
[shared2]
...
...
write list = @group2, @linux
valid users = @group2, @linux
 
[shared3]
...
...
write list = @group3, @linux
valid users = @group3, @linux
 
and all of the folders are having:
 
drwxrwxr-x 2 root "groupname" 4096 Jul 14 14:13 "sharedfolder" 
 
 
 
thanks in advance again guys...

---

### Post by Jorel on 2012-07-15
hi guys,,
 
can somebody help me please.. because when i saw other post, its for "ntfs" and not "ext4" so im not really sure if its safe to try,,

---

### Post by Morbius1 on 2012-07-15
> because i need to jump in one shared folder into another one, but i  noticed an error after jumping a couple of folders, that i needed to  contact the admin (im the admin though :sad:)  before i can write on the folder, so i always restart my machine before  i can start running through my shared folders and write on them  again.....I'm not sure what's going on there unless you are loosing your connection part of the way through the session. Especially the part about restarting the machine fixing the problem. 

There is something that you really should fix though and after re-reading through this topic it's really my fault. This will work but it looks "funny":
> [jorel]
comment = sahred file
browseable = yes
path = /jorel/samba/jorel
guest ok = no
[COLOR=Blue]** write list = @linux**[/COLOR]
valid users = @linux
create mask = 0755Get rid of the "write list" and replace it with "read only = No":
> [jorel]
 comment = sahred file
 browseable = yes
 path = /jorel/samba/jorel
 guest ok = no
[COLOR=Blue]**read only = No**[/COLOR]
 valid users = @linux
 create mask = 0755You want to allow anyone to write after they gain access ( read only = No ) but restrict who gains access ( valid users ). I should have posted that when I recommended "valid users" originally but I got sloppy and for that I apologize. Do the same with all shares that you have a valid users and a write list in the same share definition.

---

### Post by Jorel on 2012-07-15
Hi Morbius1,
 
Sorry that i panic earlier,, i will try also your suggestions..
 
But i somehow i got it working and hoping nothing will go wrong :)
 
i found a post that i followed "Lars Noodén" guide in this thread 
[http://ubuntuforums.org/showthread.php?t=1923625&highlight=group+permision](http://ubuntuforums.org/showthread.php?t=1923625&highlight=group+permision)
and it worked.. (fingers crossed..)
 
Sorry lars Nooden for bothering you, i just don't know why i cant reply to your email now.. anyway thanks a lot guys... its really hard when a newbie dont know what to do.. hope this threads can help others also...
 
Luv you guys...

---

