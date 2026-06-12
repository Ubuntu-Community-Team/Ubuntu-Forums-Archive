---
title: "Loss of root access."
date: 2012-08-17
forum: General Help
---

### Post by tony605 on 2012-08-17
I am using Ubuntu 11.10 on a Acer 5738 laptop [Processor: Intel® Core™ 2 Duo (T6400 - 2.0GHz, 800MHz FSB, 2MB)]
I had decided to upgrade to 12.04 when next invited to do so, which happened yesterday 16/08/12. When the “Authentication” prompt came up I typed in my password and was told my authentication has failed. 
I then tried loading 12.04 from the Update Manager, first trying to update my system with the updates that were waiting. Again my authentication failed.
In the terminal, when I enter my password following “sudo” I get the message:
 “user is not in the sudoers file. This incident will be reported.”. 
I changed my password using the “passwd” command and that worked. I can log in OK.
I tried going into the grub menu and got as far as the Remount / read/write and mount all other files  option but got lost after that.
How can I establish myself as the root user? 
I am the only one. 
I don't have a Ubuntu 11.10 disk.

---

### Post by MG&amp;TL on 2012-08-17
When you say 'root user'...do you mean login as root, or as a sudoer (i.e. one who can use the sudo command)?

If you mean 'root' then check here: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") -it's not encouraged on these forums.

If you mean making yourself a sudoer (I don't know why you're not), follow these steps:

1. Boot into recovery mode

2. Select 'root shell' (or similiar).

3. Type:

```
adduser <username> sudo
```

replacing <username> with your username.

4. Reboot. You should now be able to use sudo as your user.

---

### Post by ajgreeny on 2012-08-17
Have you at some point used a sudo command to start a GUI application?  That can occasionally, and depending on the particular application started, lock you out of the use of sudo.  For future reference, if that is the reason read carefully the link from MG&TL

Can you show the output of cat sudoers from the recovery mode, which may show up the problem.  As you can't use sudo you will not be able to do that from your user as it needs root privileges to show the contents of sudoers, and that is what you no longer have.

The default file is:-
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

---

### Post by tony605 on 2012-08-19
Thanks MG&TL for quick response. As the Forum was closed yesterday I've onl just had the chance to get back to you.
Sorry about the confusion over "Root access". What has happened is that I have lost my "sudo" permision so I can't update or do anything that requires authentication. 
I still don't know why.
I'm going to do as you advise. I wonder if ther will be read/write issues, but I'll try and sort them if there are.
I'll let you know haw it goes.
Tony605

---

### Post by tony605 on 2012-08-19
Thanks ajgreeny for your response.
I don't start aplications vis "sudo" comands but use Dash Home and work through the GUI's -icons stc- directly. 
I don't know why my system los my sudoer sccess. I hadn't needed to update anything for a few days and this problem only showed up when I tried to upgrade to 12.04.
I'm going to try and sort it our through rcovery mode.
Thanks again for your interest.
tony605

---

### Post by tony605 on 2012-08-19
Some progress.
I booted in rcovery mode, and once I had established read/write access I entered
adduser <username> sudo 
and rebooted.
 I can now access sudo comands in the terminal, but the authentication screen in Update Manager does not recognise my password.
Shoul I try changing my password? I did that on Friday using "passwd" which did not require sudo access.
Any thoughts?
tony605

---

### Post by MG&amp;TL on 2012-08-19
Yeah, try changing your password again. This is bizarre-can you login with that password then?

---

### Post by tony605 on 2012-08-19
Once again MG&TL thanks for such a quick response.
I changed the password using "passwd". Login fine, sudo access fine no but not recognised when I try to "Authenticate" with Update Manager" or the Sotware "Centre"
In a nother post that came up when i Googled around some sugested using 
"adduser <username> admin" rather than "adduser <username> sudo.
Is that a significant difference. I am the only user here.
What do folks think?
Thanks
tony605

---

### Post by MG&amp;TL on 2012-08-19
That might be it, yes. Give that a go, it won't do any harm.

Can you authenticate with the *users and groups* dialog? If so, try making your account an 'administrator' one. 

I confess I have no idea what wizardry ubuntu uses for its authentication. Although it appears I should know more than I do. :lol:

---

### Post by tony605 on 2012-08-19
Once again MG&TL you're great!
Now I'd got my "sudo" access back I did
       sudo adduser <username> admin
That's done the trick. I've downloaded updates, authenication worked with no fuss.
I still don't know why the problem did what it did, so I'll make a careful note of what I did incase it does it again.
You were very helpful and so promt!
 I know the Ubuntu community is really strong but it's folks like you that make that way.
Thanks
tony605

---

