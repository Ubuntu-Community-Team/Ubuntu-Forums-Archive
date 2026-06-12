---
title: "My own computer locked me out of USR"
date: 2010-11-16
forum: General Help
---

### Post by InTheMarket on 2010-11-16
EDIT: [SOLVED]

I've never been able to touch or modify anything in USR. Now it's being a problem, as wine installed itself like 8 times and won't run right. It won't let me delete the files.

How do I get permission to do stuff on USR?

EDIT: I'm set as "administrator" and I've given myself every right, however frivolous or useless. I still can't do anything on usr.

---

### Post by mcduck on 2010-11-16
Then use your admin rights, and use "sudo". That allows you to run any command as root user.

You being an admin user doesn't mean that you'd have permissions to do anything as your own user, it only means that you are allowed to run  things as root, when you specifically request to do so (by using sudo).

You should probably read this one: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by InTheMarket on 2010-11-16
> **mcduck said:**
> Then use your admin rights, and use "sudo". That allows you to run any command as root user.

You being an admin user doesn't mean that you'd have permissions to do anything as your own user, it only means that you are allowed to run  things as root, when you specifically request to do so (by using sudo).

You should probably read this one: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
How do I "Use sudo" though? I tried entering Sudo Root into terminal, but it gives me an interface I don't know how do use.

Also, I discovered not all of usr is locked. Just most of it has a little padlock on the icon, and I can't do anything with it. How to I murder said padlock?

EDIT: Got it. Used the **gksu nautilus **command. DIE, WINE FILES. FEED MY TRASHCAN.

[SOLVED]

---

### Post by mcduck on 2010-11-16
to use "sudo" you simply add it in the beginning of any command you wish to to run as root.

It's actually explained in the doc I linked for you.

for example to remove a file as normal user you'd run this:
```
rm somefile
```
but if you need to do same with rot permissions, you'd do this instead:
```
sudo rm somefile
```

You can of course use it to launch any program or command you want, but if you wish to start a graphical application you should use "gksudo" instead.

For example to edit a text file as root, using Gedit (Gnomes text editor):
```
gksudo gedit somefile.txt
```

The following command would start the file manager as root (be careful with that, it allows you to delete *anything* on your computer, including stuff that's required for the operating system to work at all).
```
gksudo nautilus
```

edit: I just had to add, even when this allows you to do so, you *definitely* shouldn't change the ownership or permissions of any system files or directories to your own user. That *will* break things, most of the stuff is required to have certain ownership and permissions.

---

### Post by InTheMarket on 2010-11-16
All I did was delete wine files so I could reinstall a clean version. I will go to any lengths to play Age of Empires II. Then I stopped with the all-powerful-sudo-user thing.

---

### Post by d3v1150m471c on 2010-11-16
```

gksudo nautilus

```

the above command will open up nautilus, your file browser, with root privileges. I must caution you, this will allow you to do anything to your root directory so be careful. It will also pass root privileges to anything you open a file with. IE: opening a text file while using root nautilus will pass root privileges to gedit as well.

---

