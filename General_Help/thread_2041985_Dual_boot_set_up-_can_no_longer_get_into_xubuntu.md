---
title: "Dual boot set up- can no longer get into xubuntu?"
date: 2012-08-13
forum: General Help
---

### Post by shresthanator on 2012-08-13
Hi everyone I was wondering if you could help me with this problem I have had with my netbook for a while. 

I had set up a dual boot system with xubuntu and windows 7 starter. For a long time I have not been able to get into the xubuntu side. I get to the login screen I type in my password I hit enter and no matter what the screen just flickers and nothing happens. I am taken back to the login again. At first I thought okay...this just has to be the wrong password? However I am absolutely sure that it is not a problem with my typing the wrong password- because when I do type in the wrong password on purpose- it tells me that I have the incorrect password. When I type in the right password it doesn't do that. 

Can somebody please help me out?

---

### Post by Toz on 2012-08-13
It sounds like the permissions on your ~/.Xauthority file are wrong. This is a known issue. The fix it to go to the first tty (Ctrl+Alt+F1) and login to the console there. Then delete the .Xauthority file:
```
rm .Xauthority
```

Then go back to the gui login screen (Ctrl+Alt+F7) and try logging in again.

---

### Post by shresthanator on 2012-08-13
> **Toz said:**
> It sounds like the permissions on your ~/.Xauthority file are wrong. This is a known issue. The fix it to go to the first tty (Ctrl+Alt+F1) and login to the console there. Then delete the .Xauthority file:
```
rm .Xauthority
```

Then go back to the gui login screen (Ctrl+Alt+F7) and try logging in again.
Hmm ctrl alt F1 doesn't seem to be doing anything for me? I am googling this and seems like other people also have had this issue trying to get to the login console

---

### Post by Bucky Ball on 2012-08-13
Perhaps boot into the recovery kernel (second on list) and then choose the drop to a terminal option and try Toz's suggestion.

---

### Post by shresthanator on 2012-08-14
> **Bucky Ball said:**
> Perhaps boot into the recovery kernel (second on list) and then choose the drop to a terminal option and try Toz's suggestion.

Oh yea I did that and I was able to get into the console and login. However I am not able to find the .Xauthority file? I did ls -a and I just don't see it? What directory is it in?

---

### Post by shresthanator on 2012-08-14
I was able to get into the console by just booting into the recovery console mode and I was able to login. However, I cannot find the .Xauthority file- when I try to delete it- it says no such file or directory. Do you know where I can find it?

---

### Post by Toz on 2012-08-14
The file would be located in your home directory. However, if you are in recovery console, you will be logged in as root, so go to /home/your_user_id and look there.

---

### Post by shresthanator on 2012-08-16
> **Toz said:**
> The file would be located in your home directory. However, if you are in recovery console, you will be logged in as root, so go to /home/your_user_id and look there.

I've looked and looked- but really it is not there. Like I have tried ls -a  and I see other files like .xconfig but for the life of me I cannot locate .Xauthority

---

### Post by Toz on 2012-08-16
Hmmm. What about a file called .ICEauthority? Does it exist and is your user account the owner?

---

### Post by shresthanator on 2012-08-16
....yea no .ICEauthority either? Yes I am the only user/owner of this netbook.

---

### Post by Toz on 2012-08-17
What about disk space? Do you have enough free disk space? Try running:
```
df -h
```
...to see how much is available.

Also, have a look at the ~/.xsession-errors log file. Is there anything there showing why you're being kicked out?

---

### Post by shresthanator on 2012-08-17
> **Toz said:**
> Hmmm. What about a file called .ICEauthority? Does it exist and is your user account the owner?



wait...nvm I did find .ICEauthority- and I was able to remove it- but I still have the same problem. I cannot login still.

---

### Post by shresthanator on 2012-08-22
> **Toz said:**
> Hmmm. What about a file called .ICEauthority? Does it exist and is your user account the owner?

so yea I was able to find .ICEauthority and delete that file. But I still have the same problem- I cannot log in still. Any more ideas?

---

### Post by Toz on 2012-08-23
How about post #11. Can you post back the results of:
```
df -h
```
...and the contents of ~/.xsession-errors:
```
pastebinit /home/<your_userid>/.xsession-errors
```
...replace <your_userid> with your actual userid and post back the link that is generated.

---

### Post by shresthanator on 2012-08-29
Ok so I know it is a bit hard to see but here are the results of df -h : 
[http://i.imgur.com/i5SpK.jpg](http://i.imgur.com/i5SpK.jpg) 

And I cannot run pastebinit because its not installed apparently. And I cant really get internet connection to install it because I have to authenticate myself (on a univ internet)

---

### Post by Toz on 2012-08-29
> ```

Filesystem     Size   Used   Avail   Use   Mounted On
/dev/sda5      5.8G   5.6G   0       100%  /
```
You are out of available drive space. You need to delete some files to make some space.

---

