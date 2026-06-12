---
title: "Cant Login Ubuntu 11.10"
date: 2012-03-13
forum: General Help
---

### Post by wookNASTY on 2012-03-13
Hi all,

I am having a problem logging into my user account.  I can log in as guest, I have gone through the ctrl+alt+F1 terminal and removed the .Xauthority file a few times to no avail.

Can someone help me solve this problem.  

Thanks in Advance.

---

### Post by raja.genupula on 2012-03-13
reset the password 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by wookNASTY on 2012-03-13
I just tried that, and when I was done entering the new password I got:

"Passwd: Authentication token manipulation error
Passwd: password unchanged"

---

### Post by wookNASTY on 2012-03-13
I just made a new user account with admin privileges, and successfully logged in.  I'm not sure what this tells me, but I think it means something in my home folder under the faulty account is bad.  Any idea how to identify that?

---

### Post by raja.genupula on 2012-03-13
[http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error)

[http://www.ideaexcursion.com/2009/09/11/fixing-authentication-token-manipulation-error-when-changing-passwords-with-passwd/](http://www.ideaexcursion.com/2009/09/11/fixing-authentication-token-manipulation-error-when-changing-passwords-with-passwd/)

---

### Post by ubudog on 2012-03-13
Hi, are you using ecryptfs to encrypt your home directory?

---

### Post by wookNASTY on 2012-03-13
I am honestly not sure.  Is there a quick way to tell?

---

### Post by ubudog on 2012-03-13
> **wookNASTY said:**
> I am honestly not sure.  Is there a quick way to tell?

While installing, did you select "Encrypt my home directory" in the installer?

---

### Post by wookNASTY on 2012-03-13
I can't remember, that was quite a while ago,  Any other way to check?

Thanks for the responses.

---

### Post by ubudog on 2012-03-13
Let's go back to the start.

What happens exactly when you try to log in?

Do you get an error message pop-up?  What does it say (exactly)?

---

### Post by wookNASTY on 2012-03-13
Well, I was using ubuntu, it crashed, and I was unable to do anything, and the screen was messed up, as in, I could see the background, but it seemed as if the windows had moved nearly to the top of the screen, and I was unable to control anything.  So I did ctrl+alt+F1 sudo reboot, to reboot the system.

When I attempted to log in after that, I entered my password, it very, briefly showed a black screen with some white text on it, Too quick for me to read.  After this black screen it returns to the login screen.  It will continue to prompt me to login. It has been the same problem since then.  

I have been iteratively moving one file at a time from the /home/<user>  file to a backup to attempt to isolate the culprit, haven't found anything yet.

Thanks

---

### Post by wookNASTY on 2012-03-13
By the way, [raja.genupula]("http://ubuntuforums.org/member.php?u=1184528"), I used the second link you posted, that worked, to reset my password, but I still have the login issue.

Thanks

---

### Post by ubudog on 2012-03-13
Try getting to the CTL+ALT+F1 console, and running this:
```
rm /home/brokenuser/.Xauthority*
```
(replace brokenuser with the username that can't login)

---

### Post by wookNASTY on 2012-03-13
ubudog:  same problem.

---

### Post by ubudog on 2012-03-13
Weird.  And you typed it with the '*', right?

If so, now try rebooting.

---

