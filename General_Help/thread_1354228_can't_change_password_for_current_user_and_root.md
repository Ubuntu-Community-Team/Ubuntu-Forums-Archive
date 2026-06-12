---
title: "can't change password for current user and root"
date: 2009-12-13
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-12-13
Hi,

I've installed ubuntu 9.10 and the default user is eugene which has a password, let's say qwerty. Now I want to change both user and root (sudo ...) password to be something more complicated. I went "User and Groups" settings, unlocked it, change eugene's password, everything ran fine and I got success message. Then I rebooted comp to find out that the password is still qwerty :confused:
The same goes for root password. I googled for 
sudo passwd
command but setting password to my_long_password doesn't seem to have any effect. I still have to use qwerty to execute sudo. :(

---

### Post by Eugene_Bondarenko on 2009-12-13
Oh, never mind, the initial problem is fixed. I had to use
sudo passwd eugene


However now I can't figure out what I changed by sudo passwd.
Also I can't figure out why does sudo use eugene's password. Isn't it supposed to use root's password?

---

### Post by Eugene_Bondarenko on 2009-12-13
Ok, I've done some research and found out about "admin" group. So eugene user is capable of doing root-things because he is part of "admin" group right? And when I sudo, I simply confirm eugene's password. Please correct me here if I am misunderstanding something. If the above logic is true, the only question is what have I changed by "sudo passwd" and what impact does this have?

---

### Post by coffeecat on 2009-12-13
Have a look here. It should explain things for you:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The Ubuntu security/admin model is a little bit different from the model used by many other distros.

---

### Post by audiomick on 2009-12-13
> **Eugene_Bondarenko said:**
> Ok, I've done some research and found out about "admin" group. So eugene user is capable of doing root-things because he is part of "admin" group right? And when I sudo, I simply confirm eugene's password. Please correct me here if I am misunderstanding something. 

Basically right, I think.
As I understand it, the Admin group is more or less "users who are allowed to use sudo"

The command "sudo" itself means "super user do", or in other words "execute the following command as a super user"


> If the above logic is true, the only question is what have I changed by "sudo passwd" and what impact does this have?

Sorry, don't know.

---

### Post by Eugene_Bondarenko on 2009-12-13
Thanks for the responses and for the article. So as far as I understand the above logic I described is correct. And regarding "sudo passwd"...have I enabled root account? If yes, should I disable it now by "sudo usermod -p '!' root"? If you are not sure about "sudo passwd", then is there some way to find out if root is enabled right now?

---

### Post by Iowan on 2009-12-13
The link *suggests* that you were still a word away from setting root password. Dunno if it's conclusive, but you can ```
sudo less /etc/shadow
``` to compare root's password to others. My system doesn't have root enabled, so it's difficult to predict what the file might look like with root enabled.

---

### Post by Eugene_Bondarenko on 2009-12-14
Thanks! I compared the contents of that file to the contents of the file after executing "sudo usermod -p '!' root" and it differs. So it seems that "sudo passwd" enabled root account. The mystery is solved :)

---

