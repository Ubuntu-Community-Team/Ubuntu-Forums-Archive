---
title: "Upgraded Ubuntu, problems with grub + firefox"
date: 2011-04-29
forum: General Help
---

### Post by not_the_geekiest on 2011-04-29
I recently upgraded Ubuntu, however I have two problems with the upgrade.

1) When ever starting up my computer, after selecting my operating system (from grub2) I receive an error stating "error no argument specified press any key to continue" after pressing any key my computer starts up. How can I remove (fix) the error?

2) immediately after Firefox starts it freezes. I see the screen saying that Firefox has crashed but I am unable to click on any of the choices (restore session, start new session). I tried uninstalling it from the repository and then reinstalling it, however, that had no effect.

I have no problem removing Firefox completely (and losing all of my preferences) in order to solve the problem. The only problem is that I do not know how to reinstall Firefox (other then the way I tried). I also have no problem reinstalling Ubuntu, and I might even do so I just want to wait until I am sure that that would no mess up grub any more.

Thank you in advance for your help.

---

### Post by not_the_geekiest on 2011-04-29
I recently upgraded Ubuntu, however I have two problems with the upgrade.

1) When ever starting up my computer, after selecting my operating system (from grub2) I receive an error stating "error no argument specified press any key to continue" after pressing any key my computer starts up. How can I remove (fix) the error?

2) immediately after Firefox starts it freezes. I see the screen saying that Firefox has crashed but I am unable to click on any of the choices (restore session, start new session). I tried uninstalling it from the repository and then reinstalling it, however, that had no effect.

I have no problem removing Firefox completely (and losing all of my preferences) in order to solve the problem. The only problem is that I do not know how to reinstall Firefox (other then the way I tried). I also have no problem reinstalling Ubuntu, and I might even do so I just want to wait until I am sure that that would no mess up grub any more.

Thank you in advance for your help.

---

### Post by not_the_geekiest on 2011-04-29
Sorry, I posted this in the wrong section here is where it belongs: [http://ubuntuforums.org/showthread.php?p=10738386](http://ubuntuforums.org/showthread.php?p=10738386) .

---

### Post by Sef on 2011-04-29
> Sorry, I posted this in the wrong section here is where it belongs: [http://ubuntuforums.org/showthread.php?p=10738386](http://ubuntuforums.org/showthread.php?p=10738386) . 	

So Locked.

---

### Post by rockstarrem on 2011-04-29
For your second question, try doing this in a terminal if you are sure you don't mind losing any of the Firefox settings and all that.

```

sudo apt-get remove firefox --purge && rm -rf ~/.mozilla

```

---

### Post by carpetStain on 2011-04-29
> **not_the_geekiest said:**
> I recently upgraded Ubuntu, however I have two problems with the upgrade.

1) When ever starting up my computer, after selecting my operating system (from grub2) I receive an error stating "error no argument specified press any key to continue" after pressing any key my computer starts up. How can I remove (fix) the error?

2) immediately after Firefox starts it freezes. I see the screen saying that Firefox has crashed but I am unable to click on any of the choices (restore session, start new session). I tried uninstalling it from the repository and then reinstalling it, however, that had no effect.

I have no problem removing Firefox completely (and losing all of my preferences) in order to solve the problem. The only problem is that I do not know how to reinstall Firefox (other then the way I tried). I also have no problem reinstalling Ubuntu, and I might even do so I just want to wait until I am sure that that would no mess up grub any more.

Thank you in advance for your help.

I have the same issue as the OP (his first question). I have tried reinstalling grub with a live CD (using the guide and grub-install) and it hasn't fixed the issue.

---

### Post by cariboo on 2011-04-29
I merged and unlocked the two threads.

---

### Post by not_the_geekiest on 2011-05-01
> **rockstarrem said:**
> For your second question, try doing this in a terminal if you are sure you don't mind losing any of the Firefox settings and all that.

```

sudo apt-get remove firefox --purge && rm -rf ~/.mozilla

```

I did that and it solved my Firefox problem, thank you.

---

### Post by not_the_geekiest on 2011-05-02
Can someone help me with my problem with grub?

---

### Post by not_the_geekiest on 2011-05-10
I fixed the "Error: No Argument Specified" by adding =root after --set in the /boot/grub/grub.cfg file.

Thank you to all who helped me.

---

