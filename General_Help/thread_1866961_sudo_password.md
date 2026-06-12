---
title: "sudo password"
date: 2011-10-22
forum: General Help
---

### Post by tlfcbb on 2011-10-22
Hi guys,

I went into user accounts in 11.10 and changed password to none.  I was hoping this would mean that I no longer had to submit a password at login.  However, I still had to input the password when I restarted.

It has caused me a problem however.  When I use sudo in the terminal it no longer recognises my password.  Also, when I try to update the system I cannot authenticate the changes because the password is not recognised. 

I have tried to go back into user accounts and reset my password but again I cannot unlock the box as a password is required.  I have tried leaving the box blank but it does not help.  

Can I reset my sudo password when my previous one no longer works?

Any help would be greatly appreciated.

Thanks

---

### Post by haqking on 2011-10-22
> **tlfcbb said:**
> Hi guys,

I went into user accounts in 11.10 and changed password to none.  I was hoping this would mean that I no longer had to submit a password at login.  However, I still had to input the password when I restarted.

It has caused me a problem however.  When I use sudo in the terminal it no longer recognises my password.  Also, when I try to update the system I cannot authenticate the changes because the password is not recognised. 

I have tried to go back into user accounts and reset my password but again I cannot unlock the box as a password is required.  I have tried leaving the box blank but it does not help.  

Can I reset my sudo password when my previous one no longer works?

Any help would be greatly appreciated.

Thanks

yes you can

see here [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by tlfcbb on 2011-10-22
Thanks haqking.

I followed the guide but when I put in the new password I got the message "authentication token manipulation error - password unchanged".

I checked this out on line and the following solution worked for me:

While in the normal (not recovery) mode hit control+Alt+F1. This will bring up a prompt. 

At the prompt type sudo passwd username (replace unermane with your username)

Type in and repeat your new password when prompted.

Hit control+Alt+F7 to return to your current session.

Hope this helps someone else with this problem.

Thanks again haqking as without your help I would never have got to the solution.

---

### Post by haqking on 2011-10-22
> **tlfcbb said:**
> Thanks haqking.

I followed the guide but when I put in the new password I got the message "authentication token manipulation error - password unchanged".

I checked this out on line and the following solution worked for me:

While in the normal (not recovery) mode hit control+Alt+F1. This will bring up a prompt. 

At the prompt type sudo passwd username (replace unermane with your username)

Type in and repeat your new password when prompted.

Hit control+Alt+F7 to return to your current session.

Hope this helps someone else with this problem.

Thanks again haqking as without your help I would never have got to the solution.

cool glad you got it sorted, yeah you can do it from a console also as you see.

Remember to mark the thread as solved using threads tools, cheers

---

