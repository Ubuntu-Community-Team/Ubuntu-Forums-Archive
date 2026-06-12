---
title: "User/Groups help"
date: 2012-06-05
forum: General Help
---

### Post by Sarteck on 2012-06-05
I currently have two users on this computer:
**sarteck** (my own account)
**family** (may family's account)

I wanted to make a directory **/home/family/Documents/the_directory*** to be accessible to both me and my family to put images in, take images out, edit existing images, etc., for the website I'm working on for them.

To this end, I created a group called **webmasters** using the GUI from the System->"Users and Groups" thingie on the Xubuntu menu.

Afterwards, I added myself and my family to the webmasters group.
```
$ sudo usermod -a -G webmasters sarteck
$ sudo usermod -a -G webmasters family
```

I then changed the appropriate permissions:
```
$ sudo chmod -R 770 /home/family/Documents/the_directory
$ sudo chgrp -R webmasters /home/family/Documents/the_directory
```

After trying to "cd" into the directory, I get the following error:
```
$ cd /home/family/Documents/the_directory/
bash: cd: /home/family/Documents/the_directory/: Permission denied
```

I check to make sure everything is kosher:
```
$ ls -l /home/family/Documents
total 4
drwxrws--- 2 family webmasters 4096 Jun  1 19:09 the_directory
```

(I'm not sure what the 's' is for, tbh.)

So then I check groups to see what's going on:
```
$ groups sarteck
sarteck : sarteck adm dialout cdrom plugdev lpadmin admin sambashare webmasters
```

Seems fine... but then on a whim I do "groups" without the username:
```
$ groups
sarteck adm dialout cdrom plugdev lpadmin admin sambashare
```

Is this normal behaviour?


I changed the directory attributes to 777 (instead of 770), and I can access it just fine.  However, I don't want it accessible by Other--just the people I assign to the webmasters group.






So, to my question: how do I make a directory owned by a group, so that members of that group can have read/write/execute permissions to the directory, and NOT allow others access?

My second question: why is it that "sarteck" is recognized as a member of "webmasters" but when logged in as sarteck doing the default "groups" command does not list the "webmasters" group?










*NOTE: The directory's actual name is "**[2012.06.01]--Moccassin Pics**", but if I put in that each time (and the properly escaped name for commands) it just looks like gibberish, so I chose the simpler "**the_directory**" for readability.

---

### Post by bab1 on 2012-06-05
> **Sarteck said:**
> I currently have two users on this computer:
**sarteck** (my own account)
**family** (may family's account)

I wanted to make a directory **/home/family/Documents/the_directory*** to be accessible to both me and my family to put images in, take images out, edit existing images, etc., for the website I'm working on for them.

To this end, I created a group called **webmasters** using the GUI from the System->"Users and Groups" thingie on the Xubuntu menu.

Afterwards, I added myself and my family to the webmasters group.
```
$ sudo usermod -a -G webmasters sarteck
$ sudo usermod -a -G webmasters family
```

I then changed the appropriate permissions:
```
$ sudo chmod -R 770 /home/family/Documents/the_directory
$ sudo chgrp -R webmasters /home/family/Documents/the_directory
```

After trying to "cd" into the directory, I get the following error:
```
$ cd /home/family/Documents/the_directory/
bash: cd: /home/family/Documents/the_directory/: Permission denied
```

I check to make sure everything is kosher:
```
$ ls -l /home/family/Documents
total 4
drwxrws--- 2 family webmasters 4096 Jun  1 19:09 the_directory
```

(I'm not sure what the 's' is for, tbh.)

So then I check groups to see what's going on:
```
$ groups sarteck
sarteck : sarteck adm dialout cdrom plugdev lpadmin admin sambashare webmasters
```

Seems fine... but then on a whim I do "groups" without the username:
```
$ groups
sarteck adm dialout cdrom plugdev lpadmin admin sambashare
```

Is this normal behaviour?

I changed the directory attributes to 777 (instead of 770), and I can access it just fine.  However, I don't want it accessible by Other--just the people I assign to the webmasters group.
~~~~

So, to my question: how do I make a directory owned by a group, so that members of that group can have read/write/execute permissions to the directory, and NOT allow others access?

My second question: why is it that "sarteck" is recognized as a member of "webmasters" but when logged in as sarteck doing the default "groups" command does not list the "webmasters" group?

*NOTE: The directory's actual name is "**[2012.06.01]--Moccassin Pics**", but if I put in that each time (and the properly escaped name for commands) it just looks like gibberish, so I chose the simpler "**the_directory**" for readability.

Let's *not* use intermediary tools.  What does the following terminal command show?```
less /etc/group |grep webmasters
```

The /etc/group file is the database of groups and the members of those groups.  By your description the webmasters group should look something like this```
webmasters:x:1003:sarteck,family
```

---

### Post by Sarteck on 2012-06-06
```
 $ less /etc/group |grep webmasters
**webmasters:x:1002:family,sarteck**
```

So, yeah, that's looking like it should.  :<  Or I assume so.

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> ```
 $ less /etc/group |grep webmasters
**webmasters:x:1002:family,sarteck**
```

So, yeah, that's looking like it should.  :<  Or I assume so.
Yes it is correct.  In theory all you need is to have all the users in the group and the group permissions be rws (the s you didn't understand).  That is the sgid bit.  It sets the gid for the folder and everything created in it.  This means if you create a file or a folder the group should always be *webmasters *.  This is not a optimal thing in your /home dirs.  Those should be User Private Groups (UPG).  The way debian is by default.

Some how you set the permissions with either **chmod g+s** or **chmod 2770** or some such. 

The correct ending can be easily achieved,  Rather than spending  all night futzing with this, I would prefer to get all the info from you first and then provide the strategy (with explanations).  Is there an external disk involved here.  Did you explicitly set the sgid bit earlier in time?

---

### Post by Sarteck on 2012-06-06
I did set it with **chmod 2770** a few days ago when I was first putzing around with it, yes.  To be perfectly honest, I'm not sure why--it's just something I remember doing a long time ago in my first forays into Linux when setting a directory to be group accessible.  If that's something I'm not supposed to do, I don't mind undoing it. XP

There is no external disk, no network--it's all to be on the same partition of the same disk.


Would you reccomend something outside the /home directories (maybe in /var, I suppose)?  As of right now, there's only 15-20 images in there, so it's no big deal to start from scratch and just move the images to a new directory.  Or would it be better to create a new directory in /home not associated with any user?


I'm open to ideas and suggestions--my main issue was me wondering why the command "groups" lists "sarteck" as part of the "webmasters" group when giving "sarteck" as the argument, but NOT listing it when no argument was given.  (As I understand it, it's supposed to give the groups of the current user when no arguments are given, and the current user is indeed "sarteck", heh.)

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> I did set it with **chmod 2770** a few days ago when I was first putzing around with it, yes.  To be perfectly honest, I'm not sure why--it's just something I remember doing a long time ago in my first forays into Linux when setting a directory to be group accessible.  If that's something I'm not supposed to do, I don't mind undoing it. XP

There is no external disk, no network--it's all to be on the same partition of the same disk.


Would you reccomend something outside the /home directories (maybe in /var, I suppose)?  As of right now, there's only 15-20 images in there, so it's no big deal to start from scratch and just move the images to a new directory.  Or would it be better to create a new directory in /home not associated with any user?


I'm open to ideas and suggestions--my main issue was me wondering why the command "groups" lists "sarteck" as part of the "webmasters" group when giving "sarteck" as the argument, but NOT listing it when no argument was given.  (As I understand it, it's supposed to give the groups of the current user when no arguments are given, and the current user is indeed "sarteck", heh.)

Answering your last question first.  This is probably because you have not logged out and then back in.  I'll bet the current /etc/groups file will be reflected then.

I think public (group) data should be in it's own branch of the file system.  This way there is no interference to the "Debian way" of UPG.  So I would start with a complete new structure.  One example of this is my Samba shares.  They are all located in the directory /smb (completely away from /home).  Does something like /data work for you?  Do you have another preference?  The only other thing that I need to know is what is the output of this command```
umask
```

---

### Post by Sarteck on 2012-06-06
```
$ umask
**0002**
```

I vaguely remember reading a long time ago on some forum or another that adding a directory to the root directory is a Bad Thing (tm), though it could be either that I read it wrong or that the user who wrote it was wrong.  Anyways, it's cool to just add a root-level directory like that?  Won't screw with anything?  If so, then yeah, that would be optimal for me.


I would ideally like the directory to be owned by root, and to have all files be readable/writeable to only the **webmasters** group.  If such a thing is possible, I'd like all new files dropped in the directory (and sub-directories, if possible) to inherit those permissions.

To go about something like that, would I:```
sudo mkdir /data
sudo chgrp webmasters /data
sudo chmod 070 /data
```Afterwards, would it be possible to do that future-files-inherit-permissions thing?



EDIT: also, no, I have not yet logged out--I had thought the permissions would take place immediately, heh.  I'll log out in a few, I suppose--doing something at the moment that I don't want to cut out right in the middle of.

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> ```
$ umask
**0002**
```

I vaguely remember reading a long time ago on some forum or another that adding a directory to the root directory is a Bad Thing (tm), though it could be either that I read it wrong or that the user who wrote it was wrong.  Anyways, it's cool to just add a root-level directory like that?  Won't screw with anything?  If so, then yeah, that would be optimal for me.

If you look at all the directories in / (including /home) you will see that that are all owned by root.
[/UOTE]
I would ideally like the directory to be owned by root, and to have all files be readable/writeable to only the **webmasters** group.  If such a thing is possible, I'd like all new files dropped in the directory (and sub-directories, if possible) to inherit those permissions.
[/QUOTE]We're both in agreement here.  :-)> 

To go about something like that, would I:```
sudo mkdir /data
sudo chgrp webmasters /data
sudo chmod 070 /data
```Afterwards, would it be possible to do that future-files-inherit-permissions thing?

Sort of.  You can use chown like this *root:webmasters *so it looks like this```
sudo mkdir /data
sudo chown root:webmasters /data
sudo chmod 2775 /data
```

This provides you with all files created with 0664 permissions and all subdirectories with 2775 permissions. The sgid bit is set and the execute bit on directories allows the user to traverse (descend into) the subdirectories).  Do not be afraid of others ro permissions on the file system.  Nothing is at risk.I have never (in 25+ years) had a ro (read only security threat).

Once you have made the directory see if the group is correct and add a folder and some files.  Tell me what you get.

> 
EDIT: also, no, I have not yet logged out--I had thought the permissions would take place immediately, heh.  I'll log out in a few, I suppose--doing something at the moment that I don't want to cut out right in the middle of.

Sounds good to me.

---

### Post by Sarteck on 2012-06-06
Sorry, been doing the Uncle Mom thing last night and was too tired to update this last night.

First, you were right about the group not taking effect until after I logged out and logged back in.  (I still think that's a weird behaviour; it would be cool if the devs could "correct" it, but I'm not sure if it's necessary that it acts like that.)



Second, creating the /data directory works, and I can add to it A-OK as "sarteck" or as "family".  However, the folders and files added to it are still owned by whomever owned them before, and still have the same permissions as before.  It doesn't "inherit" the webmasters group like I was wanting.

For example, I added two folders to the /data directory this morning while logged in as sarteck, each having a number of images in them.  I was unable to edit the images as "family" however, because the group owning the images was "sarteck" instead of "webmasters".

To accomplish what I need, should I make a cron?  One like...
**sudo chown -R root:webmasters /data && sudo chmod -R 2775 /data**
is what I was thinking.  Or I guess I could get a bit more involved nad have it give 2775 to directories and 2664 to files (since all files will just be images, non-exeutable).

What's your opinion?

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> Sorry, been doing the Uncle Mom thing last night and was too tired to update this last night.

First, you were right about the group not taking effect until after I logged out and logged back in.  (I still think that's a weird behaviour; it would be cool if the devs could "correct" it, but I'm not sure if it's necessary that it acts like that.)
It is what it is.  There is nothing to correct.> 
Second, creating the /data directory works, and I can add to it A-OK as "sarteck" or as "family".  However, the folders and files added to it are still owned by whomever owned them before, and still have the same permissions as before.  It doesn't "inherit" the webmasters group like I was wanting.
Then something has been incorrectly configured.  :-(> 
For example, I added two folders to the /data directory this morning while logged in as sarteck, each having a number of images in them.  I was unable to edit the images as "family" however, because the group owning the images was "sarteck" instead of "webmasters".
What is the output of these to commands```
ls -l /

ls -l /data
```> 
To accomplish what I need, should I make a cron?  One like...
**sudo chown -R root:webmasters /data && sudo chmod -R 2775 /data**
is what I was thinking.  Or I guess I could get a bit more involved nad have it give 2775 to directories and 2664 to files (since all files will just be images, non-exeutable).

What's your opinion?
My philosophy is to get it configured correctly with no un-needed hacks.  Then anyone looking at it will understand what has been done.  This is not some exotic thing.  We just have to config it correctly.

Right now I would just the post the results for what I mentioned above and let me advise you what to do.

---

### Post by Sarteck on 2012-06-06
Ai'ight.  This is what I did earlier:
```
sudo mkdir /data
sudo chown root:webmasters /data
sudo chmod 2775 /data
```


Using the file browser (Thunar, since I'm using Xubuntu), I then dragged and dropped two directories from my desktop into the data directory.






Here's the output that you wanted (snipped for readability):
```
$ ls -l /
[--snip--]
drwxrwsr-x   4 root webmasters  4096 Jun  6 17:46 data
[--snip--]
```

```
$ ls -l /data
total 8
drwxrwxr-x 2 sarteck sarteck 4096 Jun  1 19:02 [2012.06.01]--Moccassin Pics
drwxrwxr-x 2 sarteck sarteck 4096 Jun  6 12:34 [2012.06.06]--Moccassin Pics
```

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> Ai'ight.  This is what I did earlier:
```
sudo mkdir /data
sudo chown root:webmasters /data
sudo chmod 2775 /data
```
Using the file browser (Thunar, since I'm using Xubuntu), I then dragged and dropped two directories from my desktop into the data directory.

Here's the output that you wanted (snipped for readability):
```
$ ls -l /
[--snip--]
drwxrwsr-x   4 root webmasters  4096 Jun  6 17:46 data
[--snip--]
```

```
$ ls -l /data
total 8
drwxrwxr-x 2 sarteck sarteck 4096 Jun  1 19:02 [2012.06.01]--Moccassin Pics
drwxrwxr-x 2 sarteck sarteck 4096 Jun  6 12:34 [2012.06.06]--Moccassin Pics
```

I'll bet this is the problem> [COLOR="Red"]*I then dragged and dropped ...*[/COLOR]

Try these 2 commands and post back what happened```
mkdir -p /data/folder1 folder2

touch /data/test1 /data/test2 /data/folder1/test11

```
[COLOR="Blue"]**Edit:** The commands to check the results are [/COLOR]```
ls -l /data
ls -l /data/folder1
```

---

### Post by Sarteck on 2012-06-06
Yes, that does work... but it's kind of senseless for what it is that I'm trying to do, unfortunately.  My parents aren't going to want to learn command-line creation/editing of files.  They're going to want to move files from the camera's memory card to their desktop, rotate them if necessary, and then drop them into a folder for me to later put on the website.  XD

Here, lemme re-quote what it is that I'm looking to do:
> I would ideally like the directory to be owned by root, and to have all files be readable/writeable to only the **webmasters** group. If such a thing is possible, *I'd like all new files dropped in the directory (and sub-directories, if possible) to inherit those permissions*.

If we're moving or copying files from elsewhere using the command-line, the group permissions are inherited, but if we use something my parents can understand (the file browser, Thunar) the original permissions are kept.

With this in mind, is there still something I can do short of teaching my parents to use the command-line?  Maybe use a different file browser?  Or is it still some misconfiguration I'm missing or something? O.o

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> Yes, that does work... but it's kind of senseless for what it is that I'm trying to do, unfortunately.  My parents aren't going to want to learn command-line creation/editing of files.  They're going to want to move files from the camera's memory card to their desktop, rotate them if necessary, and then drop them into a folder for me to later put on the website.  XD

Here, lemme re-quote what it is that I'm looking to do:


If we're moving or copying files from elsewhere using the command-line, the group permissions are inherited, but if we use something my parents can understand (the file browser, Thunar) the original permissions are kept.

With this in mind, is there still something I can do short of teaching my parents to use the command-line?  Maybe use a different file browser?  Or is it still some misconfiguration I'm missing or something? O.o

Yes you are missing something.  The test (and that is all it was), tells me that any future files created in this file structure will work fine.

The next test is to see if Thunar will create a text file and a folder correctly.  Try making these using Thunar.  What do you get?

Try not to over-think this just yet.  I'll explain it all once we have all the right bits in place.  One of these could be using a different file manager (browser).  I use Gnome with Nautilus.  ;-)

The _existing_ files and folders we will have to chmod.  But the chmod command is not what you think.

---

### Post by Sarteck on 2012-06-06
Ai'ight, I thought that was it, that we were done, heh.


Yes, creating a folder and creating a empty text file using Thunar does work, and does give the correct permissions.  Creating a folder and text file in the subdirectory also gets the correct permissions.

So what is it we have to do when moving files, then?

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> Ai'ight, I thought that was it, that we were done, heh.

Yes, creating a folder and creating a empty text file using Thunar does work, and does give the correct permissions.  Creating a folder and text file in the subdirectory also gets the correct permissions.

So what is it we have to do when moving files, then?

In my set up I can copy a picture with bab:bab ownership to a folder with the structure just like yours and the ownership changes to bab:smbusers.  So I know this works.

Lets try copying a pic (right click >> copy) and the pasting it in /data (not dragging it).  Let me know if the perms change on the pic in /data.

---

### Post by Sarteck on 2012-06-06
Okay, going through it step-by-step like this, I see where I was wrong.

When I moved the folders from my parents' "family" account or from my "sarteck" account using Thunar, the original file permissions were kept.

When I copy/paste, the permissions are inherited, the desired behaviour.  My parents can definitely do that...  (Well, my Mom can; Dad might throw the monitor out the door again.)


Thank you muchly.  And sorry for being impatient.  :P




This is less important, and if it's too much trouble don't worry about it... but is there a way to make it so files cannot be moved into the folder, only copied?  Just to make sure that all file permissions stay how we want it.

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> Okay, going through it step-by-step like this, I see where I was wrong.
Sometimes the end result of testing provides more than just the answers to the initial question.> 

When I moved the folders from my parents' "family" account or from my "sarteck" account using Thunar, the original file permissions were kept.

When I copy/paste, the permissions are inherited, the desired behaviour.  My parents can definitely do that...  (Well, my Mom can; Dad might throw the monitor out the door again.)
It can't be that hard.  I'm 65 years old and I can do it!  Employee re-training.> 

Thank you muchly.  And sorry for being impatient.  :P

This is less important, and if it's too much trouble don't worry about it... but is there a way to make it so files cannot be moved into the folder, only copied?  Just to make sure that all file permissions stay how we want it.
Are we done?  You can copy and past the entire file structure over?  I would do it in pieces so I could check the progress.  At the least check the deepest directory.  You know the one that's 20 subdirectories deep. LOL

As to restricting to copying (no moving).  The only way I know is to have the destination on a separate partition from the source.  :-)  I have to smile here.  I have always maintained my data stores on separate partitions.  The problem that you experienced never happens on my systems.  A drag works as a copy and not a move (by default) when the source destination folders are on separate partitions.

---

### Post by Sarteck on 2012-06-06
> It can't be that hard. I'm 65 years old and I can do it! Employee re-training.Dad does saddles, moccassins, jackets, carvings, and just about anything you can do with your hands.  If it involves any (to use his words) "techno-geek babble," he'll do absolutely anything to avoid it.  (He really did rip the monitor from the computer and threw it out the front door once, but that's because he was pissed at my brother and I (then teenagers) arguing over it more than being pissed at it himself.)  Mom's not much better... but she likes to click click click click -what-am-I-doing click then come fetch me.  :<  So to be honest, I guess this is more for ME to have an easier time than them. XD

> Are we done? You can copy and past the entire file structure over? I would do it in pieces so I could check the progress. At the least check the deepest directory. You know the one that's 20 subdirectories deep. LOLI've only tested a three-directory-deep folder, and everything seemed kosher.  I'm going to mark this solved, and if I run into more trouble I'll just update then, heh.

> As to restricting to copying (no moving). The only way I know is to have the destination on a separate partition from the source. :-) I have to smile here. I have always maintained my data stores on separate partitions. The problem that you experienced never happens on my systems. A drag works as a copy and not a move (by default) when the source destination folders are on separate partitions.I could do that...  I have a Windows Vista partition on here that I haven't used in years (and only then for Sims 2 for my ex, heh), and wouldn't mind getting rid of it.  I'll think on it and look up some info about how to go about it...  (It's marked as my boot partition, so I'm sure the process will be a bit more involved than just formatting it if I want to be able to boot up, heh, but that's another topic for another thread that I hopefully won't have to make.)

---

### Post by bab1 on 2012-06-06
> **Sarteck said:**
> Dad does saddles, moccassins, jackets, carvings, and just about anything you can do with your hands.  If it involves any (to use his words) "techno-geek babble," he'll do absolutely anything to avoid it.  (He really did rip the monitor from the computer and threw it out the front door once, but that's because he was pissed at my brother and I (then teenagers) arguing over it more than being pissed at it himself.)  Mom's not much better... but she likes to click click click click -what-am-I-doing click then come fetch me.  :<  So to be honest, I guess this is more for ME to have an easier time than them. XD

I've only tested a three-directory-deep folder, and everything seemed kosher.  I'm going to mark this solved, and if I run into more trouble I'll just update then, heh.

I could do that...  I have a Windows Vista partition on here that I haven't used in years (and only then for Sims 2 for my ex, heh), and wouldn't mind getting rid of it.  I'll think on it and look up some info about how to go about it...  (It's marked as my boot partition, so I'm sure the process will be a bit more involved than just formatting it if I want to be able to boot up, heh, but that's another topic for another thread that I hopefully won't have to make.)

I would say the original problem is solved, but only partially implemented.  That works for me if it works for you.  If you find that this problem needs revisiting then post back here and I will see it.  It sure sounds like all is well,  I'm not going to get involved with multiple OS partitions in this thread.  :-)  I will say that my data partitions are also on separate spindles (hard drives).  This means that if they fail I replace them and restore the data.  Since I don't need high availability I use no RAID.  Just plain SATA II 1TB disks formatted ext4.

---

