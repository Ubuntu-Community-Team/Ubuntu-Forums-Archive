---
title: "grub"
date: 2005-02-04
forum: General Help
---

### Post by krzys on 2005-02-04
I want to change for a while grub so that my windows starts automatically without grub and after that I would like to restore present state. Hoe can I do this?
regards
kw

---

### Post by Buffalo Soldier on 2005-02-04
UbuntuGuide.org has exactly what you're looking for and many more other things you will want to do in the future [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

And I would suggest you go through the reading list for newbies at [http://ubuntuforums.org/showthread.php?t=13042](http://ubuntuforums.org/showthread.php?t=13042)

---

### Post by krzys on 2005-02-04
interesting for me is the following:


Q: How to permanently disable/enable boot-up service?

   1. Read General Notes
   2. To permanently disable boot-up service

      $ sudo chmod -x /etc/init.d/service_name
   3. To permanently enable boot-up service

      $ sudo chmod +x /etc/init.d/service_name

but there is one problem I dont have file service_name
so what now?

---

### Post by Buffalo Soldier on 2005-02-04
"service_name" = is the service that you would like to terminat during boot-up.

For example the service that you would like to terminat during boot-up is called **rsync** then what you should type at the terminal is...```
sudo chmod -x /etc/init.d/**rsync**
```

---

### Post by krzys on 2005-02-04
there is no effect
maybe i should explain it again
I dont want grub on my hard disk
I want windows to start just as it do it after windows instalation only

---

### Post by Buffalo Soldier on 2005-02-04
I'm curious as why you want to do that. But nevermind, here's a thread that you should read [http://ubuntuforums.org/showthread.php?t=6817&](http://ubuntuforums.org/showthread.php?t=6817&)

---

### Post by crane on 2005-02-04
You should be able to just edit the file
sudo /boot/grub/menu.lst

then change these lines

default		0  <---- set at what ever windows is remember to start counting at 0 not one.
After you change this I would test it first to make sure windows is the default. if not go back and change it again until you get it.

Then change this line

timeout		10

You cshould be able to change it to 0. This will not allow it to time out which means it will boot the default immediatly.

 I would make a linux boot disk before changing all of this. That way when your ready to change it back you can use the boot disk to boot back to linux and change it back.

another suggestion would be to just comment out these lines and make new ones. That way when your ready to change it back all you have to do is comment out the ones you were using and uncomment the old ones. It would look like this.

#timeout		10
timeout		10

the # sign take the line out of the config.

Good Luck

---

