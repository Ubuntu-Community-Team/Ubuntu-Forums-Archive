---
title: "Not root file system is defined. Please correct this from the partitioning menu."
date: 2010-05-18
forum: General Help
---

### Post by ngwh on 2010-05-18
[FONT=Comic Sans MS]Hi Ubuntu users,[/FONT]
[FONT=Comic Sans MS]I am a 12 year old kid. so if i type anything wrong pls correct me. Thanks. Okay, I have been using Ubuntu 9.10 Desktop version for around 1 month then i stoped using after installing windows 7, as I knew that there were the 10.04 version coming. So when it was released i went to torrent download the file and burned it on a cd. After that i insert the cd and use the wubi installer in there as i want to install them side by side. so after installing ubuntu i restarted the system and got into it. After a few minutes it appeared this error message "Not root file system is defined. Please correct this from the partitioning menu." So i was expecting it to be downloading problems. I went on to ubuntu website requested for a CD and it came today. So i inserted the cd did the same thing again. And the error message appeared again. So I was dissapointed. Hopefully somebody can help me solve this thing Thanks! :D[/FONT]
[FONT=Comic Sans MS][/FONT] 
[IMG]http://img30.imageshack.us/img30/1253/dscn0176p.jpg[/IMG]

---

### Post by ngwh on 2010-05-18
Sorry for not resizing

---

### Post by CharlesA on 2010-05-18
How did you install Ubuntu?

I know if you want to get it to dualboot, you need to specify the partitions manually: one should be mounted as "/" and the other should be set for swap.

Is that what you did?

---

### Post by ngwh on 2010-05-18
> **CharlesA said:**
> How did you install Ubuntu?
 
I know if you want to get it to dualboot, you need to specify the partitions manually: one should be mounted as "/" and the other should be set for swap.
 
Is that what you did?
 
erm no i used the wubi installer

---

### Post by CharlesA on 2010-05-18
> **ngwh said:**
> erm no i used the wubi installer

You could try uninstalling it and reinstalling it, but Wubi is an entirely different animal when it comes to the file system.

---

### Post by ngwh on 2010-05-18
> **CharlesA said:**
> You could try uninstalling it and reinstalling it, but Wubi is an entirely different animal when it comes to the file system.
 
with the torrent download which i burned on the cd i tried 3 times already with the cd is my fourth time

---

### Post by CharlesA on 2010-05-18
> **ngwh said:**
> with the torrent download which i burned on the cd i tried 3 times already with the cd is my fourth time

Did you verify the MD5SUM of the iso that was downloaded?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ngwh on 2010-05-18
> **CharlesA said:**
> Did you verify the MD5SUM of the iso that was downloaded?
 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
I did not but i use the official cd its also the same thing

---

### Post by CharlesA on 2010-05-18
If you didn't verify the MD5SUM before burning to a CD, the iso could have been corrupted during download. The only way to make sure is to verify that the MD5SUM matches.

Having a corrupted install cd would explain the error.

---

### Post by ngwh on 2010-05-18
> **CharlesA said:**
> If you didn't verify the MD5SUM before burning to a CD, the iso could have been corrupted during download. The only way to make sure is to verify that the MD5SUM matches.
 
Having a corrupted install cd would explain the error.
 
wait wait but i receive the cds in my mailbox today from ubuntu and its also the same thing

---

### Post by CharlesA on 2010-05-18
What host OS are you using?

Did you get any error messages during installation of Wubi?

---

### Post by ngwh on 2010-05-18
> **CharlesA said:**
> What host OS are you using?
 
Did you get any error messages during installation of Wubi?
 
 
Windows 7 and no error

---

### Post by CharlesA on 2010-05-18
I don't know what else to check then, since I don't use Wubi.

Perhaps make a thread in the Wubi subforum.

---

