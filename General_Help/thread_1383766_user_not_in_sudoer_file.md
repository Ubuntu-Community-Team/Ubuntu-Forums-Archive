---
title: "user not in sudoer file"
date: 2010-01-17
forum: General Help
---

### Post by bg2 on 2010-01-17
I an a relative linux newbie who just installed ubuntu 9.10 workstation (I have enstalled around 4 times on viurtual machines but generally do nothing with Ubuntu other than get Apache, MySql and php going) and was able to do most of want I wanted with the initial user (user1) using sudo.
 
It was painful however to work with Nautilis and Gedit, because everything i tried to do said I did not have the permissions.
 
I then added my user (the initial user) to group root. Nautilis and Gedit then allowed me to easily edit files (I only used to verify I COULD edit files - I did NOTactually edit any)
 
I then rebooted my computer and since then I cannot so anything with sudo. I get a message "user1 is not in the sudoers file". If I do groups user1 I can see user1 is listed as a member of user1 and root. However, Nautilis and Gedit respond with no permission to everything again.
 
I also cannot su to root because it says invalid password (I had not originally set a password for root but it will not accept leaving password blank and now it will not let me sudo to create a password).
 
Can anyone tell me what I need to do to make user1 work with sudo again?
 
Thanks in advance.

---

### Post by sisco311 on 2010-01-17
Boot in recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Don't add your user to the root group. Use sudo/gksu to run an application as root.
[uhelp]community/RootSudo[/uhelp]

Store your site in your home directory:
[uhelp]community/ApacheMySQLPHP#Virtual%20Hosts[/uhelp]

Also check the Sever Guide:
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Learn about file permissions:
[uhelp]community/FilePermissions[/uhelp]

---

### Post by d3v1150m471c on 2010-01-17
What permissions do you have user1 set as? If you go into system>administration>users and groups and see if you have the account set to give yourself these privileges.

Also, if you put "sudo" in a terminal and follow it with a command, you're saying it doesn't work, correct?

---

### Post by d3v1150m471c on 2010-01-17
"Don't add your user to the root group. Use sudo/gksu to run an application as root.
[community/RootSudo]("http://help.ubuntu.com/community/RootSudo")"

Absolutely

---

### Post by bg2 on 2010-01-17
That is correct that is I type sudo followed by any command, I get the message that the user is not in the sudoer file.  But without sudo and without the ability to su to root or log in to as root user (no password), I don't know how to reverse the mistake of having added user1 to grooup root.
 
Any help on how I can get back to taking user1 out of group root and having sudo work again will be greatly appreciated.

---

### Post by sisco311 on 2010-01-17
> **bg2 said:**
> That is correct that is I type sudo followed by any command, I get the message that the user is not in the sudoer file.  But without sudo and without the ability to su to root or log in to as root user (no password), I don't know how to reverse the mistake of having added user1 to grooup root.
 
Any help on how I can get back to taking user1 out of group root and having sudo work again will be greatly appreciated.

Once again:

Boot in recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by bg2 on 2010-01-17
I followed the instructions of the first link you sent and everything went ok.
 
Thanks.

---

