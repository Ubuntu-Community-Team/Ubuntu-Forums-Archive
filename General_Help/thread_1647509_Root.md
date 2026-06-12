---
title: "Root?"
date: 2010-12-17
forum: General Help
---

### Post by absentcrisis on 2010-12-17
How do I give my user account all the permissions as a root user so i can run exe files via wine?

---

### Post by oldfred on 2010-12-17
I do not think you need to be root to run programs. I just copied picassa.exe to my programs folder and ran it.

fred@fred-LucidDT:~$ cd /home/fred/.wine/drive_c
[email]fred@fred-LucidDT:~/.wine[/email]/drive_c$ ls -l
total 12
drwxr-xr-x  5 fred fred 4096 2010-06-21 14:20 Program Files
drwxr-xr-x  4 fred fred 4096 2010-06-21 14:19 users
drwxr-xr-x 12 fred fred 4096 2010-10-27 16:14 windows
[email]fred@fred-LucidDT:~/.wine[/email]/drive_c$ cd 'Program Files'
[email]fred@fred-LucidDT:~/.wine[/email]/drive_c/Program Files$ ls -l
total 12112
drwxr-xr-x 2 fred fred     4096 2010-08-31 17:07 Common Files
drwxr-xr-x 4 fred fred     4096 2010-06-21 14:20 Google
drwxr-xr-x 2 fred fred     4096 2010-06-21 14:19 Internet Explorer
-rwxr-xr-x 1 fred fred 12387832 2010-06-21 14:09 picasa36-setup.exe
[email]fred@fred-LucidDT:~/.wine[/email]/drive_c/Program Files$

---

### Post by gobbles414 on 2010-12-17
There is a better solution to your Wine problem than destroying your computer's security by trying to grant root permissions to your user account!

Follow the instructions on the [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) webpage. Essentially, you need to tell Ubuntu to obtain Wine packages from WineHQ instead of Ubuntu's repositories. The reason for this is that Ubuntu's developers recently added a "feature" to Ubuntu which makes it difficult to use Wine.

Please post your progress to this thread. If my idea doesn't help, there are some other solutions to explore.

PS: Please consider more detailed titles for your posts. "Root to run exe files in Wine" would have been better. Thanks.

---

### Post by Rubi1200 on 2010-12-17
You could also start by reading the FAQ:
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

---

### Post by gandaran on 2010-12-17
> **absentcrisis said:**
> How do I give my user account all the permissions as a root user so i can run exe files via wine?
all you have to do is right click the .exe file, from the drop down menu choose properties » permissions and tick the allow execute file box then you will be able to run/install the .exe file

---

### Post by gobbles414 on 2010-12-17
Not necessarily true, gandaran... For example, your solution isn't an option for an executable which is on a CD-ROM. The best way I've found to deal with the "executable bit" and other Wine issues in recent releases of Ubuntu is to use packages from the official Wine repository.

---

