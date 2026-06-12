---
title: "Permissions could not be changed"
date: 2010-06-24
forum: General Help
---

### Post by aburbecondita on 2010-06-24
I recently got a T-Mobile Tap and I've been trying to connect it via USB to my laptop running Lucid.

When I open up the icon that shows up on my desktop after connecting it, I can't run the setup files inside. It says: The file '/media/HUAWEI/checksetup.exe' is not marked as executable. If this was downloaded or copied form an untrusted source, it may be dangerous to run. For more details, read about the executable bit.

When I try to change the permissions from ready only, I get: Sorry, could not change the permissions of "checksetup.exe": Error setting permissions: Read-only file system

Can anybody help me out? I tried calling T-Mobile but they said they don't troubleshoot with Linux. They said it's an "older operating system".

---

### Post by Serpher on 2010-06-24
Copy the contents of the device into a folder on your desktop called "tap" then run the following command:

```
sudo chmod 777 ~/Desktop/tap/*
```

---

### Post by aburbecondita on 2010-06-24
:D   Works perfectly, thank you!

---

