---
title: "Error message when running apt-get from terminal"
date: 2011-07-09
forum: General Help
---

### Post by ExTruckie on 2011-07-09
Hi all
After a momentary power failure My server did not reboot due to a disk error. I rebooted and ran an disk repair and the machine booted fine. Now if I got to the update manager and try to update I get the following error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I checked the file location listed the file is there (hidden). Should it be a hidden file? If so how do I repair this error?

EDIT: After I posted I went to the preferences of update manager and changed the following, Updates every 2 days from weekly, Changed the server location from US server to main server. The update manager ran and updated 13 files. I don't know what change repaired my issue but a guess is, changing the download location from the US server to the Main server.
Can anyone confirm this?

---

### Post by wojox on 2011-07-09
You should have searched this has been happening a lot. Run these two commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by ExTruckie on 2011-07-10
> **wojox said:**
> You should have searched this has been happening a lot. Run these two commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```


LOL the one time I don't do a search There alot of people having this issue..
I'll file this for future reference.:guitar:

---

### Post by Marky FAQ on 2011-07-10
I think this applies to the old Ubuntu like Gutsy or Fiesty
after I installed Gutsy When I ran update manager it cant get update
I still dont know why. Maybe the OS is a little Obsolete?

---

### Post by wildmanne39 on 2011-07-10
> **Marky FAQ said:**
> I think this applies to the old Ubuntu like Gutsy or Fiesty
after I installed Gutsy When I ran update manager it cant get update
I still dont know why. Maybe the OS is a little Obsolete?Hi, you can not update those because they are to old they are no longer supported.

---

### Post by fireoftroy on 2011-07-10
> **wojox said:**
> You should have searched this has been happening a lot. Run these two commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

I searched and this was the first returned result that was remotely close to the issue at hand, so I'm glad it was here.  I tried this and it worked.  Thanks for the help.

---

