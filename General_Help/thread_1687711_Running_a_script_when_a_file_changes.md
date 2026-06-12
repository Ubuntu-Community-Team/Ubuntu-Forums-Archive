---
title: "Running a script when a file changes"
date: 2011-02-14
forum: General Help
---

### Post by aetbanan on 2011-02-14
Hi

I am trying to upload a text file containing current playing info from a music player to a ftp server. For the moment I am using Crontab to upload it every minute, but as all songs are not one minute I would like it to run everytime the file is changed instead..
 Is there any way of doing that?

Elias

---

### Post by tredegar on 2011-02-14
Please take a look at **inotify**

---

