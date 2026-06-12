---
title: "No method to open programs?"
date: 2012-02-16
forum: General Help
---

### Post by knownchild on 2012-02-16
just installed ubuntu 11.10 and it will only install/boot with "nomodeset"

I installed my nvidia graphics card driver (nvidia gtx 460 GDM) and enabled compiz, i then restarted and all i see is the following:

[http://youtu.be/ZbWHoYaojWY]("http://youtu.be/ZbWHoYaojWY")

---

### Post by aasdfasdfg on 2012-02-16
Interesting. My first try would be to open a terminal and restart unity.

To get to a terminal:
[LIST]
[*]If it works, the simplest would be the CTRL+ALT+T shortcut
[*]If that doesn't work, could you report what the ALT+F2 shortcut brings up? You may be able to open a terminal emulator from there.
[*]The sure-fire way is to simply switch to another tty momentarily. For instance, press CTRL+ALT+F2. You should see a login screen; enter your username and password, and have full access to a terminal. When you are finished, you can return to the graphical desktop by pressing (most likely) CTRL+ALT+F7; if this doesn't work, your desktop may have spawned in another virtual tty, so you might want to try CTRL+ALT+F8 or 9.
[/LIST]

Once you have access to a terminal, attempt to restart unity. Simply type ```
unity
``` at the terminal prompty, and allow some time for the window manager to restart. Note that if you are executing this from another tty (as in the last bullet point above), you will want to switch back to the graphical desktop instead of waiting for lots of verbose output at the command prompt.

If your issue is that unity is somehow not installed, this should be an easy remedy to fix: simply install unity from the command line. With proper permissions, execute ```
aptitude install unity
```

---

### Post by knownchild on 2012-02-18
I have since installed fedora 16 with all working well, but i will try this: thanks for your reply.

---

### Post by uRock on 2012-02-18
> **aasdfasdfg said:**
>  ```
aptitude install unity
```

Ubuntu doesn't have aptitude installed.```
rabbit@ronnie-desktop:~$ aptitude
The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk
Try: sudo apt-get install <selected package>
```

---

### Post by aasdfasdfg on 2012-02-18
Are you trying to say that aptitude is not installed by default from a LiveCD install?

If this is the case, I was not aware of this. Typically I install by starting with ubuntu-minimal, then running task-sel to pull in typical ubuntu. I just did that with the system I am currently using to install ubuntu 11.10. I have aptitude installed and I don't believe I had to install it manually. Regardless, aptitude is in the main repos of any debian-based distribution and is actually recommended over using apt-get, apt-cache, and the like. In fact, if you go to the project web page, it describes use of tools like apt-get as "obsolete".

[Source]("http://wiki.debian.org/Apt")

---

### Post by philinux on 2012-02-18
> **aasdfasdfg said:**
> Are you trying to say that aptitude is not installed by default from a LiveCD install?
[Source]("http://wiki.debian.org/Apt")

It is not correct and neither is synaptic.

[http://askubuntu.com/questions/69170/why-was-synaptic-packet-manager-removed-from-the-latest-ubuntu-11-10](http://askubuntu.com/questions/69170/why-was-synaptic-packet-manager-removed-from-the-latest-ubuntu-11-10)

Software Center is going to be the be all and end all. Of course power users can install aptitude and synaptic or use apt-get or install gdebi as well. The choice is still there.

---

### Post by aasdfasdfg on 2012-02-18
I am not making any reference to Synaptic or Software Center; that is just the user's choice of GUI.

In your link, it does show that aptitude is no longer installed by default, which is a change I was not aware of. While I am quite puzzled about this, I think we need to bear in mind that the way users interact with their system on a day-to-day basis (with graphical tools) does not represent the best way to give help over the internet. I think it makes sense to continue describing install steps with tools like aptitude or apt-get.

What is the rationale for breaking core Debian functionality?

---

### Post by forrestcupp on 2012-02-18
> **aasdfasdfg said:**
> I think we need to bear in mind that the way users interact with their system on a day-to-day basis (with graphical tools) does not represent the best way to give help over the internet. I think it makes sense to continue describing install steps with tools like aptitude or apt-get.

What is the rationale for breaking core Debian functionality?

The standard with Ubuntu is to use apt-get install instead of aptitude. While at one time Aptitude was very superior, that is not still necessarily the case. Regardless, it's still best to direct people to use apt-get since that's the standard here.

---

### Post by Paqman on 2012-02-18
> **aasdfasdfg said:**
> Are you trying to say that aptitude is not installed by default from a LiveCD install?

If this is the case, I was not aware of this.

It's a relatively recent change (some time in the last couple of releases). It's still installed by default on the server edition, but the thinking was that it didn't bring enough to the desktop to warrant being in the default install.

---

### Post by philinux on 2012-02-18
> **aasdfasdfg said:**
> I am not making any reference to Synaptic or Software Center; that is just the user's choice of GUI.

In your link, it does show that aptitude is no longer installed by default, which is a change I was not aware of. While I am quite puzzled about this, I think we need to bear in mind that the way users interact with their system on a day-to-day basis (with graphical tools) does not represent the best way to give help over the internet. I think it makes sense to continue describing install steps with tools like aptitude or apt-get.

What is the rationale for breaking core Debian functionality?

[http://ubuntuforums.org/showpost.php?p=11464224&postcount=22](http://ubuntuforums.org/showpost.php?p=11464224&postcount=22)

---

