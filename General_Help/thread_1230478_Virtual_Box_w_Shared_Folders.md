---
title: "Virtual Box w/ Shared Folders"
date: 2009-08-03
forum: General Help
---

### Post by dmcdaniel on 2009-08-03
Hello Everyone,

I have my Virtualbox with Shared Folders working. Problem is, everything is "read only". How can I get it to where I can write to them? I have it mounted to /media/shared. 

Thanks,
dmcdaniel

---

### Post by tjwoosta on 2009-08-03
Go into the virtualbox settings and choose shared folders, click on the folder that you are sharing and choose edit, then uncheck the box that says "read only"

---

### Post by benerivo on 2009-08-03
Provide some more info on what the guest and host os's are, and what the physical location and format of the shared folder is.

---

### Post by dmcdaniel on 2009-08-03
Location of files : //serverip/shared

pointed them to filesystem /media/shared so I could use them w/ Windows XP Pro on Virtual Box

//serverip/shared is Fedora 3
My machine is Ubuntu 8.04 and Virtual Box OSE is Windows XP Pro.

---

### Post by dmcdaniel on 2009-08-03
> **tjwoosta said:**
> Go into the virtualbox settings and choose shared folders, click on the folder that you are sharing and choose edit, then uncheck the box that says "read only"

That box is not checked. I didn't check it when I mapped it. On my Linux box it has a Lock above all the files in /media/shared but no where else.

---

### Post by benerivo on 2009-08-03
Because the error is 'no write permission' i think the problem must lie in either the permission settings of the local folder containing the links, or possibly the folder on the server.

---

### Post by GoldenSun on 2009-08-03
Just a thought.
Why not skip all the shared folder mess and use filezilla between the 2?  It seems to work more reliably that way for me.

---

### Post by dmcdaniel on 2009-08-03
> **benerivo said:**
> Because the error is 'no write permission' i think the problem must lie in either the permission settings of the local folder containing the links, or possibly the folder on the server.

I have permission from the server. I am able to access the files on my main desktop (Ubuntu) and write to them. Its just once I get them inside of Virtual Box OSE I can not for some reason. If I move the file off of the server I can. 

It has to be a permissions issue with /media/shared but i am not sure what I did wrong. I used this command to mount it to /media/shared: 

```
sudo mount -t cifs -0 username=username //serverip/shared /media/shared
```

---

### Post by dmcdaniel on 2009-08-03
> **GoldenSun said:**
> Just a thought.
Why not skip all the shared folder mess and use filezilla between the 2?  It seems to work more reliably that way for me.

The information I am trying to access is databases but they need to be used on Windows for the queries to work correctly. Gotta love access.

---

### Post by dmcdaniel on 2009-08-04
Sorry to bump this but I need to try and figure this out. Its work related and I can't fully switch over to a Ubuntu machine without it. 

Thanks!
dmcdaniel

---

### Post by dmcdaniel on 2009-08-06
Bump

---

### Post by Tee00 on 2009-08-10
I think the problem is Windows cannot write to the ext3 file system. Lunix can write to NTFS with NTFS-3g. I found this driver for windows here [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html). I have never used it, so not sure of reliability.

---

### Post by dmcdaniel on 2009-08-11
> **Tee00 said:**
> I think the problem is Windows cannot write to the ext3 file system. Lunix can write to NTFS with NTFS-3g. I found this driver for windows here [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html). I have never used it, so not sure of reliability.

Amazing. I have to tell you, I was very skeptical to try this at first. I tried it, it worked. Thanks very much for the information!

---

### Post by tjwoosta on 2009-08-11
Strange, I use that driver all the time on my physical windows install, but I have never had to use it for a virutualbox install before. Its always just worked without it for me. Did you have the virutlabox guest additions installed?

---

### Post by dmcdaniel on 2009-08-11
> **tjwoosta said:**
> Strange, I use that driver all the time on my physical windows install, but I have never had to use it for a virutualbox install before. Its always just worked without it for me. Did you have the virutlabox guest additions installed?

Yes, I have the Guest addons installed. Not sure if it was the progy above that worked or if it was something else but its working so im leaving it alone. :)

---

