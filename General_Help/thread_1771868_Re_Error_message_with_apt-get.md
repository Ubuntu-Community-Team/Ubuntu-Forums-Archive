---
title: "Re: Error message with apt-get"
date: 2011-05-30
forum: General Help
---

### Post by lifeisamystery on 2011-05-30
ok i need help, i try to open my update manager and i get this message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I try to do a manual update thru the terminal and I get this message:

crystal@crystal-Inspiron-1420:~$ sudo apt-get install update
[sudo] password for crystal: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


PLEASE HELP?!? I havent done any updates in a while and wondered why my comp stopped doing them automatically, so i checked it out and found all that. what happened and how do i fix it??? btw i should mention that i recently upgraded to 11.04 but the updates were working properly for a while afterwards, this has problem has only recently arisen, also my software center wont load up when i try to get new....anything

---

### Post by s.fox on 2011-05-30
Post moved into its own thread.  Please do not hijack other peoples threads, start your own.

Thank you.

---

### Post by drs305 on 2011-05-30
One method to try to clear this error is to open Synaptic (type 'Synaptic' in Dash - upper left - window), go to Settings > Repositories, then untick the top entry in the Ubuntu Software tab ('main'). Then reselect it after a short period. 

This should force your system to refresh the file that is causing the error message, and hopefully the new copy will not cause the same error when you press the "Reload" button.

**Added:** To start a new thread in the same forum, go to the top of the thread and find the upper left line starting with "Ubuntu Forums". The forum you are in is the last entry to the right. Click on that, and there will be a "New Thread" button on the left.

---

### Post by lifeisamystery on 2011-05-30
i am so very sorry!! im new to all this and couldnt remember how to post a new thread, it wont happen again, could you tell me how i can do it right next time please? it would be greatly appreciated, also, do you have any suggestion for my issue i am having?

---

### Post by lifeisamystery on 2011-05-30
i attempted to open my synaptic package manager, and i got this error message:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


help?

---

### Post by drs305 on 2011-05-30
Let's try using the backup status file. Open a terminal, backup the current status file, and use the backup:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpgk/status
```

---

### Post by lifeisamystery on 2011-05-30
[QUOTE=drs305;10883065]Let's try using the backup status file. Open a terminal, backup the current status file, and use the backup:




this is going to sound silly, but how do i "backup the current status file"??

---

### Post by drs305 on 2011-05-30
> **lifeisamystery said:**
> [QUOTE=drs305;10883065]Let's try using the backup status file. Open a terminal, backup the current status file, and use the backup:

this is going to sound silly, but how do i "backup the current status file"??

By running the commands I posted, you will rename the 'status' file to 'status.bad' and that is the backup. "mv" is the linux version of "rename". Then you copy the system's default backup file, 'status-old', to 'status'.

---

### Post by lifeisamystery on 2011-05-30
i hope i understood what you told me to do, i ran the codes in my terminal and got this:

crystal@crystal-Inspiron-1420:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
[sudo] password for crystal: 
mv: cannot stat `/var/lib/dpkg/status': No such file or directory
crystal@crystal-Inspiron-1420:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpgk/status
cp: cannot create regular file `/var/lib/dpgk/status': No such file or directory
crystal@crystal-Inspiron-1420:~$

---

### Post by tgm4883 on 2011-05-30
Answer here [http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by drs305 on 2011-05-30
If the files don't exist it would explain why you are getting an error message. 

Let's try the first suggestion a different way. In previous versions of Ubuntu, if Synaptic wouldn't open you could sometimes untick the entries via Software Sources. In Natty, you get to Software Sources from the Ubuntun Software Center. Open Software Center, then Edit, Software Sources and see if you can access the Repositories as I described in my earlier post.

If not, it may be time to investigate the entire /var/lib/dpkg folder and see if the 'status' and 'status-old' files are really missing. You can open the Nautilus file browswer as root so you can inspect and perform operations on system folders:
```

gksu nautilus /var/lib/dpkg
```

You would normally see folders and files, including the files 'status' and 'status-old'. Take a look and see if they are there. If you don't find any, look in /var/backups. Do you see files named dpkg.status.<some number>.gz ?

---

### Post by lifeisamystery on 2011-05-30
> **tgm4883 said:**
> Answer here [http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

ok I ran the commands in that post, i got further than i have, it connected and went thru the motions of getting the updates, but in the end, i received the same message i got to begin with:

Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.


thats what it says in the terminal after it goes thru the motions of getting the updates. and i still have all the same problems i had before i used the commands in the post you sent me to......

---

### Post by lifeisamystery on 2011-05-30
ok i opened my ubuntu software center and there is no option to edit anything, only to download new things. and i opened my nautilus and found these files:
/var/lib/dpkg/alternatives
/var/lib/dpkg/info
/var/lib/dpkg/parts
/var/lib/dpkg/triggers
/var/lib/dpkg/updates
/var/lib/dpkg/available
/var/lib/dpkg/available-old
/var/lib/dpkg/cmethopt
/var/lib/dpkg/diversions
/var/lib/dpkg/diversions-old
/var/lib/dpkg/format
/var/lib/dpkg/lock
/var/lib/dpkg/statoverride
/var/lib/dpkg/statoverride-old
/var/lib/dpkg/status.bad
/var/lib/dpkg/status-old

i selected the files and "copy-pasted" them into here lol, i also looked in the var/.... and yes i see dpkg.status.o (there are several files going from .0 thru .6) .gz

---

### Post by drs305 on 2011-05-30
You have a copy of /var/lib/dpkg/status-old, so we can try making a copy of it called 'status'.

Since removing the 'lists' file didn't solve it, the problem may very well be with the status file. So try this command. You are missing the 'status' file, which is generating the error message. This will copy the backup file and restore a slightly older version of the 'status' file.
```

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by lifeisamystery on 2011-05-30
thank god that worked, everything is working as it should! are there any additional steps i need to take to make sure this wont happen again? what caused it to happen in the first place??

---

### Post by drs305 on 2011-05-30
> **lifeisamystery said:**
> thank god that worked, everything is working as it should! are there any additional steps i need to take to make sure this wont happen again? what caused it to happen in the first place??

:-)

I don't know what happened to the original *status* file. One of the good things about Linux is that often the error message gives you a clue about what is wrong. In this case, it was a bad Merge list (which I tried to refresh but the simpler method provided by *tgm4883* was to delete it) or a problem with the status file.

Sometimes the status file gets corrupted, which is why the backup 'status-old' exists. The status file usually doesn't just disappear, so hopefully it won't happen again. Actually, reviewing your entries it appears it *did* find a 'status' file and moved it to status.bad. But in the command you quoted it said it couldn't find it. The chances are better you ran the command twice than that the status.bad file already existed.

When you are finished with the thread, please mark it SOLVED via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing !

---

### Post by marimari on 2011-12-04
Hi,

I am having the same problem and I also see the files status-old and status.bad. Nonetheless, when I give the command sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status, nothing happens.

Does anyone have any advice for me??? Thanks a lot for any help!

---

### Post by drs305 on 2011-12-04
> **marimari said:**
> Hi,

I am having the same problem and I also see the files status-old and status.bad. Nonetheless, when I give the command sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status, nothing happens.

Does anyone have any advice for me??? Thanks a lot for any help!

If the command ran without error you won't get any feedback. Many of the terminal commands produce no output unless there is a problem.

Check the date/time of the *status* file to see if it has been updated.

---

### Post by marimari on 2011-12-04
Yes, it worked! Thank you so much!

---

