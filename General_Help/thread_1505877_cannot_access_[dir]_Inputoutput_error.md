---
title: "cannot access [dir]: Input/output error"
date: 2010-06-09
forum: General Help
---

### Post by Eng.AbuWleeD on 2010-06-09
Hi all, I am a beginner in use Ubuntu .
I have dir in my HD that is very important to me,but when I try cd commad to go in the dir
I got this message:
cannot access `./Lab': Input/output error
also when use ls to view the currently dir and the other dir's also I got this message:
"ls: cannot access Lab: Input/output error
Lab"

with touch:
touch: cannot touch `Lab': Input/output error

with mkdir:
mkdir: cannot create directory `Lab': Input/output error


please tell me how can I recovery my files from this damaged dir please geniuses.

---

### Post by dcstar on 2010-06-10
> **Eng.AbuWleeD said:**
> Hi all, I am a beginner in use Ubuntu .
I have dir in my HD that is very important to me,but when I try cd commad to go in the dir
I got this message:
cannot access `./Lab': Input/output error
also when use ls to view the currently dir and the other dir's also I got this message:
"ls: cannot access Lab: Input/output error
Lab"

with touch:
touch: cannot touch `Lab': Input/output error

with mkdir:
mkdir: cannot create directory `Lab': Input/output error


please tell me how can I recovery my files from this damaged dir please geniuses.

Post the output of:
```

ls -al
```

---

### Post by Eng.AbuWleeD on 2010-06-10
Thanks mr for replay
but when I wrote ls -al

also error message appear :

ls: cannot access Lab: Input/output error
total 20
drwx------ 1 abulwleed abulwleed  4096 2010-06-09 16:15 .
drwx------ 1 abulwleed abulwleed 16384 2010-06-09 20:55 ..
d????????? ? ?         ?             ?                ? Lab

notice there is ?? nested of wxr's 

any other solution?

---

### Post by 3rdalbum on 2010-06-10
Input/Output Error is a horrible error. It usually means that part of your disk is unreadable or unwritable - it seems like it's unreadable in your case. Unreadable parts of the disk are very bad indeed as they often mean that you've lost whatever data was in that part.

You could try FSCK, which stands for FileSystem ChecK. Unmount your disk and run the 'sudo fdisk -l' command to work out the device name of the disk (it'll be something like "/dev/sdf"). Then put it into the following command:

```
sudo fsck /dev/sdf
```

With luck, the immediate problem will be fixed, at which point you should back up your data straight away and throw away the faulty disk.

---

