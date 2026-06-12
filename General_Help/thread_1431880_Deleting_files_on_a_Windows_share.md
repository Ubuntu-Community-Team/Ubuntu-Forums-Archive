---
title: "Deleting files on a Windows share"
date: 2010-03-17
forum: General Help
---

### Post by kestrel1 on 2010-03-17
I am connecting to a Windows 2003 server share from my Ubuntu 9.10 machine. This is not a problem & deleting normal files is fine. What I am actually trying to do is remove a virus from this server. If I have AV software running on the server it is constantly picking up the virus & eventually this kills the server. The AV software is unable to remove the virus on the server, but is able to on desktop machines.
Anyway, I thought use Linux to do the job & get the AV software back on the server. No go. I get a permission denied error when trying to remove the files with rm -f "filename"
Is there anyway around this? I am reluctant to start the server with the Ubuntu live CD as it is in use as a file server. If I could remove the files manually this would be good.
Any ideas?

---

### Post by steviefordi on 2010-03-17
My guess is that you are running AV as admin on the desktop machines but not on the server.

If you know what file(s) you need to delete try right-click launching Windows Explorer, selecting 'run as' to run it as a local admin. Use that session to delete the file(s).

You could alternatively set the AV program to launch as a local admin.

---

### Post by kestrel1 on 2010-03-17
The AV is being run as an admin user on the server, but it is still unable to remove these files. If I try removing them manually from Ubuntu the files are locked & I can't get access to them.
I may have to wait for a quiet time on the network & reboot the server with a live CD & see if I can manually remove the files then. A bit of a pain though. I used to use Clamwin, but this seems to be the problem. It was not picking up the viruses or it would pick it up & say it had removed it when infact it hadn't. God I hate Windows. Maybe I need to setup a Linux file server :-)

---

### Post by Ryan Dwyer on 2010-03-17
If there's a virus on the Windows server which happens to be sitting in a shared folder, deleting it from an Ubuntu client has the same effect as deleting it from a Windows client. If you can't delete it from the server itself, your best bet is to boot from a live CD and delete it.

---

### Post by steviefordi on 2010-03-17
In your original post you specified:

> I get a permission denied error when trying to remove the files with rm -f "filename"

If you were failing to delete due to a file being held open you would get:

```
rm: cannot remove "filename": Device or resource busy
```

If you're sure that it's permission denied, I think it really will be a permissions problem. I'm not sure about Windows 2003, but I recently looked at a sinmilar problem on a friends Vista box. It turns out that event though you are logged in as user with Admin rights, you still have to run programs as Admin in order to exercise those rights (much like sudo in our favourite OS).

If it's not that then it will be that your permissions are not what you think. If you are in an Active Directory setup, eliminate any permissions set there by logging onto the local machine rather than a domain. Check your permissions by looking at the security tab on the properties of the files.

---

### Post by kestrel1 on 2010-03-17
It is a permission denied error. At present I am running an online scan on the system with Eset online scanner. This has so far picked up many more instances of this same virus inf/autorun & vb.AQT trojan. These are the ones that get on to USB flash drives & are a pain in the butt. I will see how the online scan doese, but I will probably end up booting the machine with a live CD to remove all the files by hand.
What a total pain.

---

### Post by steviefordi on 2010-03-17
I'm sure booting with a LiveCD will sort you out. Maybe you can use the find command on the LiveCD with the -exec option to save you removing them all manually - something like:

```
find / -type f -a \( -iname 'virusfile1' -o -iname 'virusfile2' \) -a -exec rm -f '{}' \;
```

should do it I think.

---

### Post by Paddy Landau on 2010-03-17
If it's permission denied, then I would try with sudo:
```
sudo rm -f "*filename*"
```Be sure to type the correct file name; and maybe back it up before you delete, just in case.

---

### Post by mixmaster on 2010-03-17
I thought "Device or resource busy" was the message you got when something was using the file you tried to delete.  In particular, you get this message when you try to delete a running exe.

Presumably your virus is using the file.  I'd go with booting the server from a live CD and seeing if you can zap it that way.

---

### Post by kestrel1 on 2010-03-18
I have used sudo, but this gets the permission denied error. I have run the online scan & it found even more than I thought, mostly in the user areas. It says it has removed them, but I am running it again just to check. If it has I can get the AV software installed on the server & stop further attacks.
I will post back with the results.

---

### Post by Paddy Landau on 2010-03-18
> **kestrel1 said:**
> ... I can get the AV software installed on the server & stop further attacks.
Windows machines really do need both anti-virus and anti-malware software.

---

### Post by kestrel1 on 2010-03-18
This is built in to the AV software.

---

