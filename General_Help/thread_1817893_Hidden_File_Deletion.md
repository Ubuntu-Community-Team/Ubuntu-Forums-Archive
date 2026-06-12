---
title: "Hidden File Deletion"
date: 2011-08-03
forum: General Help
---

### Post by cypher95 on 2011-08-03
I ran a rootkit dectector and it flagged two mail files in my bin file that were suspicious. when i looked for the files i couldn't find them. i used ctrl+h to try to locate them all to no avail... should i be worried about these files? there were only two.

---

### Post by fdrake on 2011-08-03
> **cypher95 said:**
> I ran a rootkit dectector and it flagged two mail files in my bin file that were suspicious. when i looked for the files i couldn't find them. i used ctrl+h to try to locate them all to no avail... should i be worried about these files? there were only two.

you probably did not have the right permission to view the folder

try
```
sudo su

ls -alh /bin | less 
```

---

### Post by 3rdalbum on 2011-08-03
When you say it "flagged" them, what exactly was the message?

Was it to the effect of "This is a known rootkit", or "This is something I don't know about"?

Linux changes so quickly that rootkit detectors can't keep up with the changes, and you often get warnings for things that are normal on today's Linux systems.

Also, a rootkit pretty much can't get onto your system unless you open up incoming ports (e.g. installing a web server, installing openssh-server, etc). If you haven't done any of these things, then there's less than a 1% probability you have a rootkit.

---

### Post by cypher95 on 2011-08-04
i ran the app rkhunter and it sent a waring for 2 mail files:
/user/bin/mail and /user/bin/bsd-mailx

---

### Post by fdrake on 2011-08-04
those are just plain mail user agents. I don't think there is nothing to worry about

---

### Post by ChrisWells on 2011-08-04
I think too many people are running these rootkit detectors like Windows AV programs

---

### Post by Habitual on 2011-08-04
```
md5sum /usr/bin/mail and /usr/bin/bsd-mailx
```

google the md5sums.

NOTE: Did you really mean /us***e***r/bin/...?

run it again and VERIFY that path
/user/bin/mail and /user/bin/bsd-mailx

/user is way wrong
/usr is more like it.

---

