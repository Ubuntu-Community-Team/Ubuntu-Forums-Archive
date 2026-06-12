---
title: "how do i regain root access on ubuntu?"
date: 2011-12-17
forum: General Help
---

### Post by tongsak77 on 2011-12-17
I just installed Ubuntu on my laptop. I decided to add a user account and I might have accidentally changed the password or something. All I know is now my user password doesnt work. It keeps telling me that Im not in sudoers file. It worked when I added the user account. Now i cant do anything in sudo. Please let me know what I can do to resolve this situation, thank you.

---

### Post by Telengard C64 on 2011-12-17
[LostPassword - Community Ubuntu Documentation](https://help.ubuntu.com/community/LostPassword)

[s]Have you tried it?[/s]

**_EDIT_**

Sorry I misread this important looking sentence:

> It keeps telling me that Im not in sudoers file.

First try [Allowing other users to run sudo](https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo), as I think that is closer to the situation you describe. 

If that fails, then try booting to single-user mode as described in my first link.

---

### Post by Frogs Hair on 2011-12-17
Hello and Welcome 

See the link .  [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by tongsak77 on 2011-12-19
Thank you both for replying. I tried to reset my password in recovery mode as suggested but I was not able to. After I type in the new password the computer is telling me there is an *AUTHENTICATION TOKEN MANIPULATION ERROR* !!! I have no idea what that means. So at the moment, I cant do anything in root, sudo or gksudo. Please tell me what I should do if you have any suggestions. Thanks again,



-Tongsak77

---

### Post by MooPi on 2011-12-19
You will need to reboot your computer and access the grub menu. Hit the > Shift key just after the bios screen vanishes to enter grub. Select the kernel with (recovery console).
Now that your in the recovery scroll down to > root prompt
This is where you will need to issue this command
```
adduser [COLOR="Red"]your-user-name-here[/COLOR] admin
```
Reboot and check to see if you have recovered your admin privileges.

---

### Post by tongsak77 on 2011-12-19
Thanks moopi, unfortunately it didnt work. I got :

gpasswd : cannot lock/etc/group; try again later
adduser : '/usr/bin/gpasswd -a vaughn admin' returned error code 1. Existing

Have any idea what that means?

---

### Post by philinux on 2011-12-19
> **tongsak77 said:**
> Thanks moopi, unfortunately it didnt work. I got :

gpasswd : cannot lock/etc/group; try again later
adduser : '/usr/bin/gpasswd -a vaughn admin' returned error code 1. Existing

Have any idea what that means?

I think you need this [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by tongsak77 on 2011-12-19
Philinux, 
          
             Using the link you provided, I tried to do the repair myself but got lost in case 2 where it tells you to type in

sudo cp /etc/sudoers /etc/sudoers.backup 
sudo nano /etc/sudoers

Im not sure how to edit the file myself and Im confused as to what I need to do period.

---

