---
title: "External USB NTFS disk unable to read files created under Ubuntu"
date: 2011-02-09
forum: General Help
---

### Post by bd1 on 2011-02-09
Using Ubuntu 10.10 (installed via mythbuntu) I'm unable to read or see files/directories created under Ubuntu. I think it started happening after a reboot to Windows. Some of the directories created under Ubuntu have disappeared completely and some of them produce the following error:
/media/storage/videos/Kids Videos$ ls
ls: cannot access Justin Bieber: Input/output error
ls: cannot access Octonauts: Input/output error
rest of directory is seen fine...

Same on some files:
 ls -l
ls: cannot access Dirk Gently.mp4: Input/output error
ls: cannot access Dirk Gently.nfo: Input/output error
ls: cannot access Dirk Gently.srt: Input/output error
ls: cannot access Dirk Gently.tbn: Input/output error
ls: cannot access Human Planet: Input/output error
ls: cannot access Russell Howard's Good News: Input/output error
ls: cannot access The Planets: Input/output error
ls: cannot access Lost Land of the Tiger: Input/output error
total 300160
... cut ...
-????????? ? ?    ?            ?                ? Dirk Gently.mp4
-????????? ? ?    ?            ?                ? Dirk Gently.nfo
-????????? ? ?    ?            ?                ? Dirk Gently.srt
-????????? ? ?    ?            ?                ? Dirk Gently.tbn
... cut ...
d????????? ? ?    ?            ?                ? Human Planet
... cut ...
d????????? ? ?    ?            ?                ? Lost Land of the Tiger
... cut ...
d????????? ? ?    ?            ?                ? Russell Howard's Good News
... cut ...
d????????? ? ?    ?            ?                ? The Planets
... cut ...

Just to make it worse I copied more data onto the disk from windows so may have lost some it completely. It there anyway I can repair this? When trying to check under Windows it says it can't.

HELP! Some of the missing files can be reloaded but others can't.

Update:
Ran chkdsk /f under Windows XP. Some files have reappeared, but there has been a lot of unrecoverable files lost. Conclusion: Ubuntu 10.10 is badly broken for writing to NTFS. As I would like to share between Windows & Ubuntu using the external disk, I'm not sure what to do at this stage.

---

### Post by bd1 on 2011-02-12
Seems all OK. I think the problem started when I was coping DVDs onto the hard disk. I think it may related to:
[http://ubuntuforums.org/showthread.php?t=906028](http://ubuntuforums.org/showthread.php?t=906028)
I think that there is an underlying problem but have no idea what it is.
Now, I'm rebooting to Windows and copying to the internal disk before copying to the external disk. Although this slow, I think it is likely to be more reliable.

---

