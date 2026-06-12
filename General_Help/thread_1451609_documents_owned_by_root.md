---
title: "documents owned by root"
date: 2010-04-10
forum: General Help
---

### Post by cmcanulty on 2010-04-10
I reinstalled 9.10 yesterday and put the home folder on its own partition. Now it has my home folder as owned by me but all the files in it including Documents are owned by root. I did tell it to change ownership on enclosed files with no luck. So I can't paste my backup files into the Documents folder. I can do GKsudo nautilus but it times out every 15 minutes and I have to restart copying the 67GB of files constantly. hope there is a fix for this.

---

### Post by akakingess on 2010-04-10
when you did the chown/chmod did you use the -R (recursive) option so that it would change the permissions for everything within the home folder (files, subdirectories, etc.)? Just a suggestion.

---

### Post by oldfred on 2010-04-10
This link also has instructions on fixing ownership or permissions for a new /home.

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by cmcanulty on 2010-04-10
I tried to change ownership using the properties menu after doing gksudo nautilus. Then I tried the above fix and got this terminal response
```
cmcanulty@Gateway:~$ sudo chown cmcanulty /home/cmcanulty/ .dmrc -R
chown: changing ownership of `/home/cmcanulty/Documents/Florida/My House Hibiscus/.goutputstream-IB8XAV': No such file or directory
chown: cannot access `/home/cmcanulty/.gvfs': Permission denied
chown: cannot access `.dmrc': No such file or directory
cmcanulty@Gateway:~$ ^C
cmcanulty@Gateway:~$ 
[CODE]
```

---

### Post by mikewhatever on 2010-04-10
```
sudo chown -R cmcanulty ~/Documents
```

This should change the ownership of everything in Documents to yourself. To check if it worked, run the following:

ls -l ~/Documents

---

### Post by gadolinio on 2010-04-10
Mmmm try this:

Press alt F2. Type "gksu /usr/bin/x-terminal-emulator", hit enter.
From that terminal, go to the home folder, and do "chmod a=rxw -R username".
Hope that helps...

Edit:
do chmod or chown, depending on what you need. For your entire user folder you should probably use chown.

---

### Post by cmcanulty on 2010-04-10
I think that did it thanks very much

---

### Post by gadolinio on 2010-04-11
> **cmcanulty said:**
> I think that did it thanks very much

You're welcome! Don't forget to mark the thread as [SOLVED], with the Thread Tools.

---

### Post by sisco311 on 2010-04-11
> **cmcanulty said:**
> I tried to change ownership using the properties menu after doing gksudo nautilus. Then I tried the above fix and got this terminal response
```
cmcanulty@Gateway:~$ sudo chown cmcanulty /home/cmcanulty/ .dmrc -R
chown: changing ownership of `/home/cmcanulty/Documents/Florida/My House Hibiscus/.goutputstream-IB8XAV': No such file or directory
chown: cannot access `/home/cmcanulty/.gvfs': Permission denied
chown: cannot access `.dmrc': No such file or directory
cmcanulty@Gateway:~$ ^C
cmcanulty@Gateway:~$ 
[CODE]
```

I guess this command fixed the permissions. ;)

.[gvfs]("http://en.wikipedia.org/wiki/GVFS") is a virtual filesystem, you can simply ignore the permission denied error message. The permissions of .dmrc caused a lot of problems in the past, but it looks like the file is no longer needed, so you can ignore the missing file warning as well.

---

