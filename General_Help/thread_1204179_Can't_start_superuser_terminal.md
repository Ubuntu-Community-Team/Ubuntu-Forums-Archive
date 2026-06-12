---
title: "Can't start superuser terminal"
date: 2009-07-04
forum: General Help
---

### Post by Sukhinov on 2009-07-04
I trying to start superuser terminal (pressing the red icon), it asks my password, but nothing happening after it.

The regular terminal (black icon) works fine. "sudo" command also works.

---

### Post by CrusaderAD on 2009-07-04
You could try making a launcher on the desktop and use the command 
```
sudo gnome-terminal
```
Just a thought. I know you want to use root privledges as little as possible.

---

### Post by michy99 on 2009-07-04
> **capibolso said:**
> You have to have root account enabled, enter the following command.

(snipped)

Done.
Greetz

Please see this concerning forum policy:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Sukhinov on 2009-07-04
$ sudo gnome-terminal
[sudo] password for san:
Failed to contact the GConf daemon; exiting.

:(

---

### Post by Sukhinov on 2009-07-05
I found this: [http://groups.google.com/group/linux.gentoo.user/browse_thread/thread/bda14e09639df9a7?pli=1](http://groups.google.com/group/linux.gentoo.user/browse_thread/thread/bda14e09639df9a7?pli=1)

But I cannot understand anything there :(

---

### Post by CatKiller on 2009-07-05
> **Sukhinov said:**
> "sudo" command also works.

Best use that then. I see no problem in sticking sudo in front of commands that need to be run with root privileges. It takes less than a second to type.

If you really must use the Terminal as root, and 15 minutes just isn't enough for you to get things done before you need to enter your password again, you can use any of
```

sudo -i
sudo -s
sudo su
```to become root in the Terminal. It's exit to stop being root for one or two of those, and logout for one or two. Can't remember which because it's not something I've needed to do in a long time.

I wouldn't recommend any of them. Just use sudo.

Don't use sudo for graphical applications. Use gksudo instead.

---

### Post by Sukhinov on 2009-07-05
OK. But problem persists. I want to have problem-free system.

Look here: [http://www.pubbs.net/debian/200906/8051/](http://www.pubbs.net/debian/200906/8051/)
That is not only my problem. Why do you release the system, where one of the standard applications does not working??

---

### Post by ivanvajar on 2009-07-05
SuperUser Terminal is used by very few people. It is DANGEROUS to use it. sudo is what you need. As for 'standard applications not working': problems emerge with every system, but SuperUser Terminal is something you don't need anyway. If you ever need to be root:> sudo suin Terminal will be the same as SUTerminal. Just type > exitto exit root and return to normal user.

---

### Post by Sukhinov on 2009-07-05
Onscreen keyboard also does not work. The same error!

This application is very important to me, because I have no built-in keyboard in my laptop.

---

### Post by oldos2er on 2009-07-05
> **Sukhinov said:**
> I found this: [http://groups.google.com/group/linux.gentoo.user/browse_thread/thread/bda14e09639df9a7?pli=1](http://groups.google.com/group/linux.gentoo.user/browse_thread/thread/bda14e09639df9a7?pli=1)

But I cannot understand anything there :(

 That's ok; Ubuntu wouldn't understand "emerge" or "portage" anyway.

 You can change the command in root terminal's properties to **gnome-terminal -e "sudo -i"** , and it should work.

---

