---
title: "how can i resize trash in kubuntu ??"
date: 2010-09-09
forum: General Help
---

### Post by hossein222 on 2010-09-09
hi. 
my trash size in kubuntu became (0 bit ) and I can't delet anything I must shift+delet
[SIZE=4]how can i resize trash in kubuntu.??????????????[/SIZE]

---

### Post by ankspo71 on 2010-09-10
Hi,
Have you tried to resize your trash by opening dolphin and going to:
Settings > Configure Dolphin > then choose Trash from the category on the left, then change maximum size? I attached a screen-shot.

---

### Post by hossein222 on 2010-09-10
yes my friend , I try it but it dosen't work and the trash is 0 bit now and I can't delet anything
if you have another way to solve this problem please tell me.
thank you so much

---

### Post by hossein222 on 2010-09-10
> **ankspo71 said:**
> Hi,
Have you tried to resize your trash by opening dolphin and going to:
Settings > Configure Dolphin > then choose Trash from the category on the left, then change maximum size? I attached a screen-shot.
 
 
yes my friend , I try it but it dosen't work and the trash is 0 bit now and I can't delet anything
if you have another way to solve this problem please tell me.
thank you so much

---

### Post by Sathors on 2010-10-02
I have exactly the same problem here on kubuntu 10.04, and the size is of 0 bits even if it's configured to go up to 5 Go.

---

### Post by ankspo71 on 2010-10-02
Hi hossein222 and Sathors,

I don't think this is the problem but...
Can it possible that your trash folders are too full?
This command will locate all of your trash folders and report the size of them:
```
sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
```OR```
sudo -s
find / -type d -name '*Trash*' | sudo xargs du -h | sort
exit
```

After using the command above, you can delete the trash folders (or folders and files inside them) by using:
```
(In Kubuntu)
kdesudo dolphin /path/to/trash-folder
(In Ubuntu)
gksudo nautilus /path/to/trash-folder 
```
Then highlight the files or folders that you want to delete and use Shift+Delete to delete them permanently. See the first link below for more information about full trash.

Here is a page that talks about Trash Full problems:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
Here is another good one about trash and other Disk Space problems:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Did either of you move your home folder?
If yes then maybe posts #8 and #9 of this page can help:
[http://ubuntuforums.org/showthread.php?t=1580740](http://ubuntuforums.org/showthread.php?t=1580740)

If none of this helps, then it might be a bug in Kubuntu.

---

### Post by Sathors on 2010-10-03
Thank you for your answer, but the trash directories are all more or less empty (the bigger weights 11Mo).

I think it may be a kde bug.

---

