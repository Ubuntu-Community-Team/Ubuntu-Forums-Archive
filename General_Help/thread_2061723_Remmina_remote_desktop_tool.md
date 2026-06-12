---
title: "Remmina remote desktop tool"
date: 2012-09-23
forum: General Help
---

### Post by doomdragon on 2012-09-23
Hey guys. Was wondering if I could get some help please?
I have been playing with FreeNX and installed openssh however
it seems to have provided an issue for me. If I click on the new connection button it will open the dialogue but pops up with the following warning...

[IMG]http://dl.dropbox.com/u/9680067/Selection_005.jpeg[/IMG]

This did not happen until I installed open ssh. I'm sure it's a case of adding remmina to ssh to enable permissions but not sure how to do this. Truly grateful for any help received!

---

### Post by papibe on 2012-09-24
Hi doomdragon.

It looks like a permission problem.

Could you post the result of this command?
```
ls -alR ~/.ssh/
```
Regards.

---

### Post by doomdragon on 2012-09-25
I apologise for my late response. Has been a hectic few days!
As you requested, here is the following;


drwx------  2 root  root   4096 Sep 21 00:09 .
drwxrwxr-x 52 david shared 4096 Sep 25 19:58 ..
-rw-r--r--  1 root  root    391 Sep 21 00:09 known_hosts

hope it helps! 
Cheers for your time, I appreciate it immensely.

---

### Post by papibe on 2012-09-25
Thanks.

Your ~/.ssh directory is owned by root, and that won't allow you to ssh as our regular user.

Change it back to you using this command:
```
sudo chown youruser\: ~/.ssh/
```
Replace 'youruser' with your actual user.

Let us know how it goes.
Regards.

---

### Post by doomdragon on 2012-09-25
I thought it would be something simple like this! 
Just didn't know where the file was located but thank you 
you are a legend! Thanks for your help, hopefully one day
I may be in the position to return the favour.

---

