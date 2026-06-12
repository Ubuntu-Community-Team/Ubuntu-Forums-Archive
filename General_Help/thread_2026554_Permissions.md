---
title: "Permissions"
date: 2012-07-15
forum: General Help
---

### Post by OpenSage on 2012-07-15
Is there a way to allow someone to have permission to install applications from the Ubuntu Software Center without giving them permissions to install from websites?

I was thinking it would be nice to allow kids or other regular users to install applications from trusted sources like the ones in the Software Center that have a very low risk involved in installing them, but don't want to allow them to be able to download things off of the internet.

I was just thinking it would make the Ubuntu experience for regular users much more enjoyable if they could just try out different software on their own without having to wait for a real system admin to be around to install for them.

---

### Post by ajgreeny on 2012-07-15
> **OpenSage said:**
> I was thinking it would be nice to allow kids or other regular users to install applications from trusted sources like the ones in the Software Center that have a very low risk involved in installing them, but don't want to allow them to be able to download things off of the internet.
Interesting idea, but I suspect that if your kids are clever enough to install things they get direct from internet sites rather than the repositories, they may be savvy enough to overcome your restrictions of any other activities.

You will not find many applications that are installable, or even probably things they would want to install, on the web.  This is not windows where you can get hundreds of .exe installation or setup files from the web and install a lot of dangerous rubbish.
However, if you decide to persevere it is possible to allow all users to use the software-center without the need for a password, by editing the /etc/sudoers file.

Study **sudo visudo** and all that it involves, especially the "User Specifications" section at [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers) for some more info, but be _very_ careful; if you don't really know what you're doing it's best not to even try as you could really mess up your system and find yourself unable to login.

---

### Post by Cheesemill on 2012-07-15
This may work....

[http://ubuntuforums.org/showpost.php?p=12051646&postcount=6](http://ubuntuforums.org/showpost.php?p=12051646&postcount=6)

---

### Post by OpenSage on 2012-07-16
Thanks for trying to help, but I was just wondering if there is a way without having to give admin or sudoer permissions.  Just a way for a regular user to add programs through the software center without having permissions to do anything else that could harm the system.  Thanks again.

---

### Post by ajgreeny on 2012-07-16
> **OpenSage said:**
> Thanks for trying to help, but I was just wondering if there is a way without having to give admin or sudoer permissions.  Just a way for a regular user to add programs through the software center without having permissions to do anything else that could harm the system.  Thanks again.
No, I don't think there is a way to do that, or not one that is safe to do.

You can in theory give everyone permission to do everything but it is a recipe for total disaster and not something I am going to give you information about; actually I think the forum rules do not even allow that information to stay on posts.

This is one of the important security advantages of Linux over windows, and not something that should be disabled if you can avoid it.

---

### Post by Cheesemill on 2012-07-16
If you look at the thread that I linked to in my post #3 above there is an <allow_any> section. Maybe changing this to 'yes' will achieve what you are after.

---

