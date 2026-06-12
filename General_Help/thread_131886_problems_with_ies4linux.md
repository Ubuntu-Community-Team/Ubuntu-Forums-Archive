---
title: "problems with ies4linux"
date: 2006-02-17
forum: General Help
---

### Post by cosborn72 on 2006-02-17
I am having problems installing ies4linux, and I'm wondering if anyone can make any suggestions.  I have a feeling I am making a simple mistake, unrelated to the program.

Here is my problem.

-I downloaded the ies4linux-1.3.4.tar.gz file from the ies4linux website.
-Opened and extracted it to my home dir. 
-Opened the folder and clicked on the ies4linux script.
Nothing happens.

More info - I have cabextract 1.1-1 and wine 0.9.8 installed, as per directed on the ies4linux site.
I tried running the script in the console, first with and then without sudo, and received the following message.

chris@housing:~$ cd /home/chris/ies4linux
chris@housing:~/ies4linux$ ls
config  ies4linux  lib  LICENSE  README  winereg
chris@housing:~/ies4linux$ ies4linux
bash: ies4linux: command not found
chris@housing:~/ies4linux$ sudo ies4linux
Password:
sudo: ies4linux: command not found
chris@housing:~/ies4linux$


Any guesses?  I know that I have run shell scripts before, without difficulty.

(And before anyone comments, I don't intend to use IE for browsing - not when I can use firefox, which is much better.  I need IE to get some other software up and running.):)

---

### Post by aysiu on 2006-02-17
Have you tried this? ```
./ies4linux
``` You may also want to make sure the file is executable (check permissions).

---

### Post by cosborn72 on 2006-02-17
That was it!  Thanks for the help!

---

