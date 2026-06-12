---
title: "How to keep users &amp; groups when resinstall &amp; move /home to new partition?"
date: 2012-01-02
forum: General Help
---

### Post by mashedbear on 2012-01-02
Hi - I am running out of storage space and want to install a new larger HDD to replace one of the two existing internal HDDs in my system.

I plan to use the new HDD for /home ( following [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")) and once /home been moved over to the new HDD, reinstall Ubuntu onto the remaining existing HDD. 

This is different to the current set up where the second HDD is used for rsync backup copies (going forward backups will be on to an external HDD or NAS). 

I want to have  /home on a separate drive & partition so that I am able to maintain users settings, files, if I want to (re)install Ubuntu or switch to another distro. 

My question is if I reinstall Ubuntu how can I maintain the current users settings including and groups & privileges? (so that the users can continue to use /home as they do now).

Thanks for any help / pointers.

---

### Post by nothingspecial on 2012-01-02
Simply......Add them in the same order.

The important thing is that they have the same uid and gid.

Type ```
less /etc/passwd
```

Scroll down to the bottom and you will see the users you have created starting with the one that was created during installation like this
```

nothingspecial:x:1000:1000
```

The next user will be 1001:1001 and the next 1002:1002 and so on.

If you create the users in the order the numbers climb from 1000 on wards they will have the same uid and gid as before and there should be no problem.

---

### Post by papibe on 2012-01-02
Hi mashedbear.

The installation process will recognize all hard drives, and it will present them to you for configuration. If you choose manual, you'll have the option of not formating the new hard drive, and just configure it to be mounted at /home.

Note that there are some settings that are not kept in your home, and you'll have to recreate them after installation. For example, if you added your user to a non standard group.

Also note that after a clean install, several applications will be missed (the ones you installed after the first install). For example, let's say your VLC settings are secure and safe on ~/.config/vlc, however VLC will have to be installed afterwards.

I would recommend doing a backup of your important data before reinstalling your OS (just in case).

Hope it helps.
Regards.

---

### Post by mashedbear on 2012-01-02
Thanks nothingspecial and papibe!

---

