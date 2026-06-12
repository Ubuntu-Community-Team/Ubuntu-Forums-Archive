---
title: "root"
date: 2010-03-17
forum: General Help
---

### Post by joachim10022 on 2010-03-17
How can I enable the root account (for login) in ubuntu 9.10?

---

### Post by sisco311 on 2010-03-17
It's against the [thread=716201]forum policy[/thread] to tell people how to enable the root account for graphical login.

---

### Post by Penguin Guy on 2010-03-17
[COLOR="Red"]Using [FONT="Courier New"]root[/FONT] directly is very dangerous.[/COLOR] It's also against the forums code of conduct to tell people how to do this. Perhaps you could try [google]("http://www.google.com/search?q=how+to+login+as+root+in+ubuntu")?
In most cases you do not need to enable root login, please tell us what you're trying to achieve and we may be able to help you find a safer way to do it.

EDIT: [More info here.]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by mcduck on 2010-03-17
Sorry, but you are not going to get answer to that question on these forums. The forums stick to Ubuntu's security model (using "sudo" for admin tasks) and providing help in enabling root account is forbidden by the forum policy.

The general idea is that anybody who has a good reason to enable root will also be able to figure such a trivial thing without having to ask for it here..

That being said, if you can tell what you are trying to do we can most likely give you instructions how to do it without enabling the root account. :)

edit: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by audiomick on 2010-03-17
Hallo.
From here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
> **Policy**
Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail.There are some good reasons for this. I would suggest reading through the link.

edit: The link also explains how to do pretty much anything for which you might want to enable root.

---

### Post by joachim10022 on 2010-03-17
Ok, thanks
didn't know it is against policy

---

### Post by joachim10022 on 2010-03-17
but how can i access (change) files of other users (someone wants to edit document and wants to do it directly from my account / hassle of logging of).
He can for example not change anything he created from my account, because I am not "the owner/creator".
How do I get the rights to edit, etc his documents from my account?
Preferably without using the terminal.
Thanks

---

### Post by whiskeylover on 2010-03-17
Use "sudo"

---

### Post by sisco311 on 2010-03-17
> **joachim10022 said:**
> but how can i access (change) files of other users (someone wants to edit document and wants to do it directly from my account / hassle of logging of).
He can for example not change anything he created from my account, because I am not "the owner/creator".
How do I get the rights to edit, etc his documents from my account?
Preferably without using the terminal.
Thanks

You can change the permissions/ownership (right click -> Properties -> Permissions tab) of the file: [uhelp]community/FilePermissions[/uhelp].

---

### Post by joachim10022 on 2010-03-17
> **sisco311 said:**
> You can change the permissions/ownership (right click -> Properties -> Permissions tab) of the file: [uhelp]community/FilePermissions[/uhelp].

That is faded out. Or do i have to go to his account and change it there

How can i change and edit files in the "filesystem"?

---

### Post by mcduck on 2010-03-17
I really recommend reading the Root/Sudo documentation I linked above for you, it answers all your questions and explains the reasons much better than anybody will be able to write here.

Anyway, the "sudo" command allows you to execute any temrinal comands as root (or any other user), while "gksudo" allows you to launch any graphical applications as root user.

For example to edit the /etc/fstab file with the graphical text editor, Gedit, you'd run "gksudo gedit /etc/fstab".

edit: here's the link again: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by joachim10022 on 2010-03-17
thanks

---

### Post by whiskeylover on 2010-03-17
> **joachim10022 said:**
> That is faded out. Or do i have to go to his account and change it there

How can i change and edit files in the "filesystem"?

sudo chmod <permissions> <filename>

---

### Post by audiomick on 2010-03-17
> **joachim10022 said:**
> but how can i access (change) files of other users (someone wants to edit document and wants to do it directly from my account / hassle of logging of).
He can for example not change anything he created from my account, because I am not "the owner/creator".
How do I get the rights to edit, etc his documents from my account?
Preferably without using the terminal.
Thanks
You have been given advice on this now, but if you had read the links that were posted, you would not have had to ask.

---

