---
title: "Serious permissions problem..."
date: 2012-04-18
forum: General Help
---

### Post by dude1946 on 2012-04-18
First of all, this was really dumb, I know, but I changed the permission on my /lib directory, and now my whole UBUNTU system is inaccessible. ..... What can I so to fix it...

---

### Post by codemaniac on 2012-04-18
Hello dude1946 ,
Welcome to the Ubuntuforums !!
What is meant by **inaccessible** , you cannot boot from it ? 
Or a particular application is cannot be accessible ?

---

### Post by dude1946 on 2012-04-18
Well, I did a restart, and it showed UBUNTU, but then just went to a black screen - no icons or anything.

---

### Post by albandy on 2012-04-18
Try this:

sudo chown root.root /lib
sudo chmod 755 /lib

If you only changed the directory permissions this will work, but if you changed the contents permissions it could be a little more complicated to solve it but possible.

---

### Post by dude1946 on 2012-04-18
I'm sorry - that should be "blank screen" not black screen. Before doing the restart, nothing worked - I couldn't even open the terminal - I got a 'permission denied' message - and as I said, after the restart - nothing...

---

### Post by dude1946 on 2012-04-18
...Well, I'm afraid I changed the contents permissions as well .... Like I said - it's serious...

---

### Post by codemaniac on 2012-04-18
If your hard drives are not encrypted you can just boot off from a live cd .You can see Ubuntu partitions mounted .Then you can change the permissions to /lib.

---

### Post by dude1946 on 2012-04-18
I installed it off of the internet, and don't have a cd ... wil it be a problem getting one?

---

### Post by codemaniac on 2012-04-18
Any live cds or Live usbs would serve the purpose .Puppy /SLax/Ubuntu or anything you desire .Just download the iso and burn it on a cd .You can also do an live USB .
Get ubuntu from the below link .

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by albandy on 2012-04-18
Hold down the right shift key before ubuntu starts to boot. The grub menu will appear. Then select (rescue mode) and press enter.

In a few seconds you will see a recovery menu. Select remount and press enter, then select root and press enter.

then change /lib permissions.

first try with this:
chown root.root /lib
chmod 755 /lib
reboot



Hope this work, if not you have to do a recursive permissions change, but this is dangerous.

---

### Post by dude1946 on 2012-04-18
Thank everyone for all the help. I'm doing the download now... I'll let you know how it turns out. ...

---

### Post by HiImTye on 2012-04-18
```
sudo chown -R root:root /lib
sudo chmod -R ug=rwx,o=rx /lib
```should hopefully fix your problems

if you are doing it from a liveCD then remember change the path from '/lib' to your hard drive's '/lib'

---

### Post by dude1946 on 2012-04-19
I finally got it .... Thanks again to everyone for all of the help. This is my first time posting here, and I really appreciate everyone taking the time to give me good advice...

---

