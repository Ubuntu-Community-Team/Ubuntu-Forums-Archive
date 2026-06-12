---
title: "Strange win2000-samba-password problem"
date: 2006-06-04
forum: General Help
---

### Post by djsroknrol on 2006-06-04
Well....The Mrs. went and changed OS's on her 'puter...I thought she'd go Dapper but opted for win2000 pro...oh well...maybe next time. Right now, I have to deal with it. 

Which brings me to the problem......Her shares are comming up with a password dialog box...no password works...but if you click on "connect", it lets you see the shares...very odd. I've searched for an answer to how could I remove the dialog box on the Ubuntu side to no avail.

When it was all win98 boxes, it was no problem...shares came up without passwords, and nothing has changed as far as conf files.

Maybe someone could make a suggestion as to where I could look or something I've overlooked...

Thanks guys and gals....

---

### Post by link141 on 2006-06-04
I have a simular situation with my personal home network.  I have Kubuntu on the computer that is in my room, and my parents have Win XP on the computer in their room.  Naturally, I have many, many files that I'd like accesss to but the same situation presents itself, even on the Windows XP side of **my** computer.  I think I know why though.  Here's two very posible reasons.  First, Linux supports FAT32 file systems very well.  If your wife (I'm assuming) choose to convert the filesystem to NTFS, which Linux doesn't support that well, then it needs Samba to read the files to it, as opposed to looking at it directely.  This is not as likely as the next reason though.  The more likely reason is that Win 2k and Win XP are network Biased and require Network authentification to read some files and or modify them even if they're set to be shared (edited by other users).  Now if you are logged in as the user, Windows thinks they are your files and as a result, will allow you freedom to your files completely, rather than use the more complicated sharing rules.  If your wife's computer is set without a password (as my parents computer), than there is no password to use with the login prompt, and windows won't accept that.  In other words, Windows supports logging in to share files over the network, rather than using the share rules- which by the way, are a mess to get working.  

My advice is to get your wife to use a password with her computer, and try logging in with her user name and password over Samba, it will work **much** better.  If your worried that your wife must be logged off to do this, Windows will let one user  log in on many computers.  It is basically impossible or a lot of bother to get the share option to work.   

Sorry for the mountian of explaination.  Windows is a big mess with several things though, so just try to use the loggin.  I hope this helps you :).

---

### Post by disturbed1 on 2006-06-04
In windows 2000 add yourself as a user. (right-click my computer, choose manage, users). The username should be the same name in linux
```

$whoami

```

---

### Post by djsroknrol on 2006-06-04
Hey guys..

you're missing the objective of mine...

> Her shares are comming up with a password dialog box...no password works...but if you click on "connect", it lets you see the shares...very odd. I've searched for an answer to how could I remove the dialog box on the Ubuntu side to no avail.

I've tried all of your suggestions to get things working properly. Share seems to be working, but there is something wrong with password, so I'm trying to "remove" a faulty dialog box..I want it to shut up...:D ....any other ideas on this one ?

---

### Post by disturbed1 on 2006-06-04
Make sure you're passing the password in your ffstab.

```
//192.168.1.100/julie    /mnt/julie    cifs    username=$user,password=$pass,noauto,uid=1000,guid=1000 0    0
```

If you're not passing the password in the mount command it will ask you for it everytime.

---

### Post by djsroknrol on 2006-06-05
Just getting back to the problem, so sorry for the bump....

```
//192.168.1.100/julie    /mnt/julie    **cifs    **username=$user,password=$pass,noauto,uid=1000,guid=1000 0    0
```

I was under the impression that cifs was for windows servers...my wife formatted in fat32 and did everything the way she did to install XP. Her 'puter has always been an open workstation. It's asking for a password, but let's me thru without one...any other ideas as to how I could track this one down ?

---

### Post by djsroknrol on 2006-06-05
EDIT:

here's something I failed to notice till now...there are 4 folders that are shared on her rig. Once you connect, and back out, it doesn't ask again if you go back into that folder...same with the other 3. 

Now, any other ideas ?

---

### Post by disturbed1 on 2006-06-05
[quote=djsroknrol]EDIT:

here's something I failed to notice till now...there are 4 folders that are shared on her rig. Once you connect, and back out, it doesn't ask again if you go back into that folder...same with the other 3. 

Now, any other ideas ?[/quote] 
Since you are not passing a password option it will continue to ask you for on the first connect. You have to pass the password option, even if there isn't one, if you want that dialog to disapear, you have to pass the password option. So if you want that dialog to disapear, in your mount script or fstab you have to pass the password option ;)

SMBFS is old, CIFS is an extention of smbfs. Seems to perform better for me. With SMBFS I experienced some FS locking and slow file transfers (~25-30MB/s) with CIFS I haven't experienced any FS locks and get 40-50MB/s transfers.

---

### Post by djsroknrol on 2006-06-06
Hi everyone...

There's a resolution to the problem...it seems that when the Mrs did her install of 2000pro, she turned the guest account off...turning it back on solved the login dialog box problem.

Thanks for everyone's help on this stumper....

---

