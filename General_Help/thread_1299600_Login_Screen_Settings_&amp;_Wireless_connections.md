---
title: "Login Screen Settings &amp; Wireless connections"
date: 2009-10-24
forum: General Help
---

### Post by Scunnered on 2009-10-24
I am currently using 9.10 RC and had a look at the login settings.  My preference is for the system to automatically login which works fine when I set it to do so. When this is done I then find that there is a password request to enable me to connect to my wireless connection.

If I do not automatically login then the wireless connection does.  Is it not possible for both to happen at once therefore improving login and speeding up the process

I use my system in the main at home and therefore do not have the same need for passwords as I would have using it in an open environment.  When taking the laptop outwith the home I could easily re-set the login to add the extra security layer.

Is there a way to achieve an automatic login for both or is this something I will have to live with ?

---

### Post by Scunnered on 2009-10-30
As 9.10 is now finalised I will in effect bump this post.

I like the idea of an automatic logon but if I have to perform one for the wireless connection then it is counter productive.

Can anyone advise on this

---

### Post by P4man on 2009-10-30
Two things you could try. first try making the wifi available to all users in the network manager settings.

If that doesnt help, I guess you could try and put an empty password on the keyring. Its not very secure as you can imagine. You can do so in applications > accessories > passwords. Change the password for the login keyring set it blank. Keep in mind that means all your keyring passwords are stored unencrypted on disk.

---

### Post by cyberkilla on 2009-10-30
It kinda defeats the purpose of it looking you in automatically, doesn't it?

---

### Post by Scunnered on 2009-10-30
> **cyberkilla said:**
> It kinda defeats the purpose of it looking you in automatically, doesn't it?

You got that one in 1.  P4man's suggestion of an empty password will not work as I have to use the one that I gave to my ISP in order to login to the wireless connection.

If I can automatically connect to my wireless connection without providing a password after loging in why can't the system run both in sequence and save all the bother?

Is this possible or can anyone direct me to whom I should address this question with the view to having it considered for suitable amendment to the automatic login function.

---

### Post by P4man on 2009-10-30
> **Scunnered said:**
>   P4man's suggestion of an empty password will not work as I have to use the one that I gave to my ISP in order to login to the wireless connection.


You misunderstood. Im not saying a blank password on your wifi or mobile broadband. A blank passord on your *keyring* which stores all passwords. By default the keyring password is the same as the login password, and if you log in through gdm, it unlocks. If you do not login (because you set autologin) it does NOT unlock as a security measure, since all your passwords are then visible. If you blank out the keyring password, I believe it will be unlocked always meaning network manager and other apps can access it to retrieve the wifi/broadband password to connect.

---

### Post by P4man on 2009-10-30
but do try the other suggestion first. Make the connection available to all users. I think that removes it from the keyring (since the keyring is only for your user)

[IMG]http://img692.imageshack.us/img692/8868/screenshot012.png[/IMG]

screenie is for my wired connection, but obviously you do that for your wireless connection. Right click network manager > edit connections > select the connection > edit connection > available to all users

---

### Post by Scunnered on 2009-10-30
**P4man**

Many thanks for your reply.

I followed your example and everything works as described.

This makes things easier.

Thanks again

---

