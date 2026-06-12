---
title: "I can't access windows share folders on my network &quot;ubuntu 10.04&quot;"
date: 2010-05-06
forum: General Help
---

### Post by thisisspeedy on 2010-05-06
help please any ideas? keeps saying "unable to mount location"

---

### Post by powerofpi on 2010-05-07
Places > Connect to Server...

Service type: Windows Share
Server: (name or ip address)
Share: (share name)
Folder: (leave blank)
User Name: (Windows user name with permissions for share)
Domain Name: (probably WORKGROUP)

Try that, or else let us know how you are trying to access your share.

---

### Post by pernahajder on 2010-05-07
you can use the places/network menu after you install the ntfs-config


```
sudo apt-get install ntfs-config
```

---

### Post by thisisspeedy on 2010-05-07
Thanks but this didn't work. In the "share" box I'm not sure what you mean by share name. 

Also it keeps accessing me for a password when that folder is public folder without a password. 

I really need this to work. 

Thanks again guys.

---

### Post by thisisspeedy on 2010-05-13
any other suggestions? Maybe give me the dummies version of the instructions. Thanks :)

---

### Post by thevalleyboy on 2010-07-01
I agree tried all the above I cannot seem to get Lucid to talk to my Windows 7 public folders either - keeps asking for a password - maybe I'll go back to 9.10 cause it had no issues - installed the Apache items above no luck - opps that was another suggestion - that and the ntfs-config

---

### Post by Reffner on 2010-07-01
Try the connect to server option without specifying a share. Just select "Windows Share" and put in the IP of the PC you're connecting to and hit enter (or press connect).

EDIT--

Also if you are repeatedly prompted for your username and password then check your sharing permissions on your windows box.

---

