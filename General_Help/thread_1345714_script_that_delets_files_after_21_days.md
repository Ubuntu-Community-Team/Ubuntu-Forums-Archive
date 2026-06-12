---
title: "script that delets files after 21 days"
date: 2009-12-04
forum: General Help
---

### Post by Nate_is_cool on 2009-12-04
I've been trying to get this script to work for a few days now. I have a folder "Feed", that I have security videos stored in. I only want to hold them for 3 weeks before they should be deleted. problem is my script wont delete the fulders that some of the videos are in. 

EX

/home/administrator/Desktop/Feed/cam1/10-23-09

I want the 10-23-09 and its contents to be deleted. "10-23-09" is just the day - month -etc and there is one for everyday. Ill attach what i have so far

---

### Post by riste on 2009-12-04
I think you can do what you want with something like this:

find /home/administrator/Desktop/Feed/cam1/ -ctime +20 -delete

That should delete files and folders modified at least 21 days ago in that directory.  The first line in your test file would only match files, not folders, because of the -type f switch (and the -name '*.avi' of course).  You can safely check what it'll match by running the find command without the -delete action at the end.

---

### Post by john newbuntu on 2009-12-05
or you could try doing it automatically using logrotate

---

