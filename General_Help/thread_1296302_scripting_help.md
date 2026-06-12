---
title: "scripting help"
date: 2009-10-20
forum: General Help
---

### Post by Porter200el on 2009-10-20
I have 4 windows servers I connect to, I have them all bookmarked so I can access them quickly.  I need to write a script that will take one or more files and copy it to the same dir. on the other 3 servers.  Can anyone help point the way?

---

### Post by falconindy on 2009-10-20
It would help to know how you're accessing the other servers. Samba? SSH?

---

### Post by Porter200el on 2009-10-20
Sorry, Samba :)

---

### Post by Giblet5 on 2009-10-20
Do you have admin privileges on the three windows servers?

Can you install a common service (FTP, SSH, etc) or set up those common folders as shared with write access?

If so, it can be scripted. Otherwise, you'll have to log in to each server and initiate the transfer from the servers, one at a time. Manually.

Micro rant: Windows Server is very useful until you need to do server stuff. This is how the cost of ownership stays low: do little, make it hard, ignore security and proven technologies, throw some paint on it, and overcharge people for the privilege of calling themselves "certified".

---

### Post by Porter200el on 2009-10-20
> **Giblet5 said:**
> Do you have admin privileges on the three windows servers?

Can you install a common service (FTP, SSH, etc) or set up those common folders as shared with write access?

If so, it can be scripted. Otherwise, you'll have to log in to each server and initiate the transfer from the servers, one at a time. Manually.

Micro rant: Windows Server is very useful until you need to do server stuff. This is how the cost of ownership stays low: do little, make it hard, ignore security and proven technologies, throw some paint on it, and overcharge people for the privilege of calling themselves "certified".

I am not an admin on all 4 servers, so I guess I will stick to it manually.  I mean, I do have rw access to all the shares I need, but we do not have FTP or SFTP setup as of yet.

---

### Post by Giblet5 on 2009-10-20
> **Porter200el said:**
> I am not an admin on all 4 servers, so I guess I will stick to it manually.  I mean, I do have rw access to all the shares I need, but we do not have FTP or SFTP setup as of yet.

Well if you have the folders that you need to write-to shared, then you can push the files using a script. Is that the case?

If so, you can use smbclient:

```
for i in server1 server2 server3
do
  smbclient //$i/my_directory <password> -U [domain/]<my_user> << !
put myfile.dat
quit
!
done
```

Pretty automated and fancy, huh. All those bells and whistles I threw in... You owe me now. ;)

---

### Post by Porter200el on 2009-10-20
> **Giblet5 said:**
> Well if you have the folders that you need to write-to shared, then you can push the files using a script. Is that the case?

If so, you can use smbclient:

```
for i in server1 server2 server3
do
  smbclient //$i/my_directory <password> -U [domain/]<my_user> << !
put myfile.dat
quit
!
done
```Pretty automated and fancy, huh. All those bells and whistles I threw in... You owe me now. ;)


That is tight!!  I definitely owe you one!  Only two weeks left for Sam Adams Octoberfest.

---

### Post by Giblet5 on 2009-10-20
> **Porter200el said:**
> That is tight!!  I definitely owe you one!  Only two weeks left for Sam Adams Octoberfest.

Just name your firstborn after me, Pockpe Thalmusian Quordblot.

And mark the thread solved.

---

