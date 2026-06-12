---
title: "root can't run Users and Groups"
date: 2010-12-30
forum: General Help
---

### Post by yaye on 2010-12-30
Hello,

I'm running 10.10 64-bit and have configured it for root graphical login for administration of the system.  When I log in as root, I can run all menu items in System -> Administration with the exception of Users and Groups.  When I try running this, the application starts, but I only get an animated spinning disk that doesn't stop, can't modify the users properties and I can't close the application unless I go to System -> Administration -> System Monitor -> Processes tab , highlight users-admin and click End Process.  Anyone have a solution for this problem?

---

### Post by dcstar on 2010-12-31
> **yaye said:**
> Hello,

I'm running 10.10 64-bit and have **configured it for root graphical login for administration of the system**.  When I log in as root, I can run all menu items in System -> Administration with the exception of Users and Groups.  When I try running this, the application starts, but I only get an animated spinning disk that doesn't stop, can't modify the users properties and I can't close the application unless I go to System -> Administration -> System Monitor -> Processes tab , highlight users-admin and click End Process.  **Anyone have a solution for this problem?**

I doubt that anyone will have a solution because the Ubuntu security model is specifically designed **not** to run in this way.

If you want to circumvent the security model then you are on your own.

---

### Post by mcduck on 2010-12-31
+1 to above.

The tool is specifically configured to be used as a normal user, providing the permissions to handle what it does using PolicyKit. It's not going to work if you try to run it as root.

I can, on some level, understand that some people might want to enable root account for terminal use (although I find even that pretty much pointless). But there really isn't a single good reason to log into desktop as root. That's just a plain bad idea.

---

### Post by yaye on 2010-12-31
> **mcduck said:**
> +1 to above.

The tool is specifically configured to be used as a normal user, providing the permissions to handle what it does using PolicyKit. It's not going to work if you try to run it as root.

Thanks for the clue.  I'll try configuring the policy of users-admin .

> **mcduck said:**
> I can, on some level, understand that some people might want to enable root account for terminal use (although I find even that pretty much pointless). **But there really isn't a single good reason to log into desktop as root.** That's just a plain bad idea.

A few years ago, I actually posted a clear example of where root logged into X saved me a lot of time and cutting and pasting of commands as I performed surgery on my hard drive.  That post was removed when the administrators of the Ubuntu Forums removed the thread about root.  I'm not going to waste time posting it again.

---

### Post by yaye on 2010-12-31
> **dcstar said:**
> I doubt that anyone will have a solution because the Ubuntu security model is specifically designed **not** to run in this way.

If you want to circumvent the security model then **you are on your own.**

I prefer my own security model, and I have no problem being "on my own".  When it comes to Linux, I've been largely on my own.  In fact, I've been on my own when creating or modifying autoexec.bat, config.sys, win.ini, system.ini, program.ini, inittab, fstab, xorg.conf, sources.list, etc, etc, etc.

I think I need an Ubuntu Power Users Edition.

---

### Post by yaye on 2011-03-25
I decided to not waste time trying to hack Ubuntu.  New Year, new distro, renewed capabilities.

---

### Post by duanedesign on 2011-04-18
Thread closed.

---

