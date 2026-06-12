---
title: "samba"
date: 2010-08-29
forum: General Help
---

### Post by himel on 2010-08-29
i already read a lot for samba but i can't installed samba. plz help me with a easy way.

just i download "samba-latest.tar.gz" and copy it in my desktop.
now how i install this.


plz help me i know its easy for other but i can't.

---

### Post by davidmohammed on 2010-08-29
samba is readily installed via synaptic manager if you have a minimal install.  Its integrated in ubuntu already depending upon what you want to do.  What do you want to do?

---

### Post by himel on 2010-08-29
> **davidmohammed said:**
> samba is readily installed via synaptic manager if you have a minimal install.  Its integrated in ubuntu already depending upon what you want to do.  What do you want to do?

In Terminal i use:-

sudo apt-get install samba smbfs

or 
 
sudo apt-get install samba smbclient 

its says that
package samba has no installation candidate

**i want to share my file from windows to linux

---

### Post by davidmohammed on 2010-08-29
open nautilus and right click the folder you want to share and choose "sharing options".

Click "share this folder". Give the share name a short name.

You should now be able to browse from windows to your ubuntu via its IP address - or go via "networking" and browse to your ubuntu box.  It may take a few minutes to appear on your windows network.

---

### Post by himel on 2010-08-29
> **davidmohammed said:**
> open nautilus and right click the folder you want to share and choose "sharing options".

Click "share this folder". Give the share name a short name.

You should now be able to browse from windows to your ubuntu via its IP address - or go via "networking" and browse to your ubuntu box.  It may take a few minutes to appear on your windows network.

It says "Sharing service is not installed" then i clicked install service and it says failed.

---

### Post by howefield on 2010-08-29
Have you just installed Ubuntu ?

Perhaps you need to reload/update your software sources.

Open a terminal and type

```
sudo apt-get update
```

Or open System > Administration > Synaptic Package Manager and press the reload button.

If you use the second method, you can then search for samba within Synaptic and install.

---

### Post by himel on 2010-08-29
> **howefield said:**
> Have you just installed Ubuntu ?

Perhaps you need to reload/update your software sources.

Open a terminal and type

```
sudo apt-get update
```Or open System > Administration > Synaptic Package Manager and press the reload button.

If you use the second method, you can then search for samba within Synaptic and install.


yes just i installed ubuntu 10.04. and i've no internet connection so i can't be update. any other way...

---

### Post by howefield on 2010-08-29
> **himel said:**
> yes just i installed ubuntu 10.04. and i've no internet connection so i can't be update. any other way...

Hmm...

---

### Post by himel on 2010-08-29
> **howefield said:**
> Hmm...

so what i do???

is it possible to share my internet connection from windows?

---

### Post by howefield on 2010-08-29
> **himel said:**
> so what i do???

I guess you are back to the file you mentioned in your first post, have you extracted it and read the file called howto4.txt ?

---

### Post by himel on 2010-08-29
> **howefield said:**
> I guess you are back to the file you mentioned in your first post, have you extracted it and read the file called howto4.txt ?

yes i extracted it and read howto4. but i can't understand how i install them

---

### Post by davidmohammed on 2010-08-30
> **himel said:**
> so what i do???

is it possible to share my internet connection from windows?

Yes - you can use "ics" - internet connection sharing.  Type that into google - various stuff on how to set that up.

From ubuntu - make sure your PC is connected to your router - when ICS is working, your wired connection will automatically work on a reboot.

---

### Post by himel on 2010-09-03
{Solved}

i shared my internet connection from windows and update my ubuntu.now it works fine.

---

