---
title: "Azureus update issue."
date: 2010-08-08
forum: General Help
---

### Post by DeadlyOats on 2010-08-08
I installed Azureus from their site.  It works well.  The only problem is when Azureus tries to apply updates, I get this error message:

"The folder <path-where-I-installed-Vuze> is not writable.  This will prevent future software updates from being applied."

There was a link the the Vuze wiki, and the problem is that I (or is it the Azureus updater?) do not have permissions to write to that directory, or words to that effect.

How do I apply the proper permissions so that when an update from Azureus is downloaded, it is applied?

The wiki offers this solution:

> sudo java -cp ./plugins/azupdater/Updater.jar org.gudy.azureus2.update.Updater updateonly `pwd` ~/.azureus

But this looks like something that I have to do manually, each time...

How do I set it up, so that the updater has the permissions and uses the proper password to do it automatically, when I restart Vuze?

I'm using Ubuntu 9.10

---

### Post by DeadlyOats on 2010-08-09
Shameless bump... :oops: (well... some shame is felt...)

---

### Post by Vaphell on 2010-08-09
**ls -la <path-where-you-installed-Vuze>**
first line of the output, with single dot (current dir)
who is the owner and what are the permissions? (rwx...)

vuze doesn't use standard update method but does it separately? that's lame if this is the case.

---

### Post by DeadlyOats on 2010-08-09
Thanks for your reply.

Here's the output from that command...

So, what does this mean?

> total 14892
drwxr-xr-x 3 root root     4096 2010-05-15 01:02 .
drwxr-xr-x 3 root root     4096 2010-05-15 00:40 ..
-rwxr-xr-x 1 root root     5497 2010-04-09 01:19 azureus
-rw-r--r-- 1 root root 13553153 2010-05-15 01:00 Azureus2.jar
-rw-r--r-- 1 root root    36640 2010-05-05 01:55 ChangeLog.txt
-rw-r--r-- 1 root root    17719 2010-04-09 01:19 GPL.txt
-rw-r--r-- 1 root root        0 2010-04-09 01:20 installer.log
drwxr-xr-x 6 root root     4096 2010-05-15 00:40 plugins
-rw-r--r-- 1 root root      456 2010-04-09 01:19 README.txt
-rw-r--r-- 1 root root  1473511 2010-04-09 01:19 swt.jar
-rw-r--r-- 1 root root    73723 2010-04-09 01:19 TOS.txt
-rwxr-xr-x 1 root root      106 2010-04-09 01:19 updateAzureus
-rwxr-xr-x 1 root root     5497 2010-04-09 13:42 vuze
-rw-r--r-- 1 root root      249 2010-04-09 01:19 vuze.desktop
-rw-r--r-- 1 root root     5150 2010-04-09 01:19 vuze.png
-rw-r--r-- 1 root root     1464 2010-04-09 01:19 vuze.schemas
-rw-r--r-- 1 root root     7046 2010-04-09 01:19 vuze.torrent.png



> vuze doesn't use standard update method but does it separately? that's lame if this is the case.

Vuze downloads the update, Vuze_Installer.tar.bz2, just outside of the vuze folder, but then is unable to apply the update because it finds the vuze folder unwritable...

If I had installed the vuze from the ubuntu repository, it would not be able to be updated when the updates became available from Azureus, and Vuze would generate messages saying it's not the right version, and some features would not work.  This is why I got the package straight from Vuze's site.  I don't get the it's not compatible messages anymore, but now it can't update itself....  I can't win....

---

### Post by DeadlyOats on 2010-08-09
Shameful bump.  :redface:

---

### Post by Vaphell on 2010-08-09
it's unwritable because it's owned by root and without sudoing you are just an ordinary user who cannot touch that stuff. Without gaining admin rights with sudo you simply can't put things there by default. That's why you always are prompted for a password when ubuntu update manager pops up.

Options i see
1. see if running vuze from terminal with **gksu vuze/azureus/whatever_its_called** allows it to update. If so you could modify its launcher to involve gksu. Drawback is that it's a bad idea to run software with admin rights when it has no business having them.

2. you can try to set permissions manually. Go to the dir in question and change it so it allows 'others' to write
rwxr-xr-x = triplets of read/write/execute for owner, group, everybody else. 'root root' means that user root belonging to group root owns these
**sudo chmod o+w <stuff>** should work, modify that dir, its subdirs and files (o+w means add 'write' to 'others')

3. find a ppa repository with fresh versions of vuze and add it to repo list to overcome version freeze of official ubu repos. The most elegant solution.

---

### Post by DeadlyOats on 2010-08-10
I ended up trying option two.  The padlocks disappeared from the folders.  I only did option 2 to the folders, and not to the contents.  It seems the updates took.  At least I din't get the "blah, blah, blah is not writable" error message.  Plus, checking out the "About" menu option in the Help menu option, shows the latest version number.

I only applied method number 2 to the folders and sub-folders, but not to the contents of those folders.  That's O.K., right?

Option 3 could not be made to work, because it seems there are no vuze ppa repositories for Ubuntu, with current updates.

Reading the FAQ at Vuze/Azureus makes me wonder why Ubuntu modifies the vuze package to a point that breaks it?  Does Ubuntu hate Vuze/Azureus?

Update:

I rebooted the machine, and restarted Vuze.  No error messages, which means the updates took.

Thanks, Vaphell.  This seems to have worked.

I still find it puzzling that Ubuntu would cripple an application package and then include it in their repository.  They may as well not include the package at all...  Why do they do that?

---

