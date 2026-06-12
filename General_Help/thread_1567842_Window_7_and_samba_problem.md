---
title: "Window 7 and samba problem"
date: 2010-09-04
forum: General Help
---

### Post by Colo2 on 2010-09-04
Ive set up some network folders on my ubuntu machine with samba. XP and Other ubuntu machines are able to access this folder without permissions, this is the way ive set it to, so that people without user account can access. However my windows 7 machine always asks for user login for the ubuntu machine when accessing the network folder. Im confused

please any ideas?

thanks =)

---

### Post by Colo2 on 2010-09-04
No one knows why it's doing this? Win7 wants a user and pass to access both of my ubuntu machines shared docs

---

### Post by Colo2 on 2010-09-04
driving me nuts

---

### Post by mendhak on 2010-09-04
Could you show how you've set it up?

---

### Post by sikander3786 on 2010-09-04
It could be a very simple mistake like same username on the Samba Server Machine and Ubuntu / XP machines but a different named user account on the Windows 7 machine.

Anyway are you able to access the files from Windows 7 after typing the username?

---

### Post by Morbius1 on 2010-09-04
Windows Live Sign-in Assistant.

Do you have it installed?

Uninstal it.

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

---

### Post by jimbop99 on 2010-09-04
Go to your Ubuntu machine. Admin>samba>preference>samba users>select user name>edit user>change the passord to your desired password. Then try accessing the folder from winows 7 using the new password.

---

### Post by Morbius1 on 2010-09-04
Actually it wasn't until after I read jimbop99's post that I realized that I misread your original post. I thought you were trying to access a Win7 share not the other way around.

As for jimbop99's post there shouldn't be any reason to modify or even have a samba user if all your shares are set to allow guest access:
> Ive set up some network folders on my ubuntu machine with samba. XP and  Other ubuntu machines are able to access this folder without  permissions, [COLOR=Blue]this is the way ive set it to, so that people without user  account can access[/COLOR]. However my windows 7 machine always asks for user  login for the ubuntu machine when accessing the network folder. Im  confusedThere is one condition that would fit your circumstance though. There is a design flaw in Windows in that when it accesses the lan it will actually send it's current Windows login name and password along with the request to browse your Ubuntu shares. 

**IF** the Windows login name and the Ubuntu local login name match
**AND** you created a samba user for own Ubuntu login name
**AND** the samba password for the ubuntu login user is not the same as the Windows login password
**THEN** access will be denied and the client windows user will be prompted for authentication.

If that's the case then disable the samba password for your own Ubuntu login name, for example:
```
sudo smbpasswd -d morbius
```And see if the Win7 user can now access without a prompt.
[COLOR=Blue]*Note: to re-enable your samba password:*[/COLOR]
```
sudo smbpasswd -e morbius
```

---

### Post by jimbop99 on 2010-09-04
You can also right click on the folder you want to share and select properties. Select the share tab and check "guest access". Then no password or user name required.

---

### Post by snakebob on 2011-01-12
I also have same problem as this thread' owner
seems couple of proposal arise, i will try above proposal.
 
Thanks gentlman

---

### Post by snakebob on 2011-01-14
> **Morbius1 said:**
> Actually it wasn't until after I read jimbop99's post that I realized that I misread your original post. I thought you were trying to access a Win7 share not the other way around.
 
As for jimbop99's post there shouldn't be any reason to modify or even have a samba user if all your shares are set to allow guest access:
There is one condition that would fit your circumstance though. There is a design flaw in Windows in that when it accesses the lan it will actually send it's current Windows login name and password along with the request to browse your Ubuntu shares. 
 
**IF** the Windows login name and the Ubuntu local login name match
**AND** you created a samba user for own Ubuntu login name
**AND** the samba password for the ubuntu login user is not the same as the Windows login password
**THEN** access will be denied and the client windows user will be prompted for authentication.
 
If that's the case then disable the samba password for your own Ubuntu login name, for example:
```
sudo smbpasswd -d morbius
```And see if the Win7 user can now access without a prompt.
[COLOR=blue]*Note: to re-enable your samba password:*[/COLOR]
```
sudo smbpasswd -e morbius
```
 
Thanks for your instruction but it's all same ...Samba share folder still ask ID/Password login which never work.
 
Anyway, I found this..Could you jump into below link , my thread.
[http://ubuntuforums.org/showthread.php?t=1666849](http://ubuntuforums.org/showthread.php?t=1666849)
 
I want to have your opinion 
Thanks.

---

