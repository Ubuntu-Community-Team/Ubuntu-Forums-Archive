---
title: "sharing folders between two local accounts"
date: 2010-05-15
forum: General Help
---

### Post by hedge.hog on 2010-05-15
Hi, 
I was hoping this would be simple, so suspect I don't know the Ubuntu way:
- Two local user accounts
- Both want full access to all current and upcoming content of a folder of one of the accounts, e.g. family pictures.

I couldn't seem to get linking to work, if I create a file or update it the other account sometimes loses access - seems to depend on the application.
Personal file sharing seems to be a better way to go, but I can't seem to make the shared folder appear anywhere under ~/Documents.  
The reason for wanting to make this folder under ~/Documents is so that an application that doesn't show the PFS folder like nautilus does, will still let me have access to the shared contents.

Is there a way to 'hack' PFS to be linked/mounted under ~/Documents ?

Appreciate any hints or tips.

---

### Post by gadolinio on 2010-05-15
> **hedge.hog said:**
> Hi, 
I was hoping this would be simple, so suspect I don't know the Ubuntu way:
- Two local user accounts
- Both want full access to all current and upcoming content of a folder of one of the accounts, e.g. family pictures.

I couldn't seem to get linking to work, if I create a file or update it the other account sometimes loses access - seems to depend on the application.
Personal file sharing seems to be a better way to go, but I can't seem to make the shared folder appear anywhere under ~/Documents. 
The reason for wanting to make this folder under ~/Documents is so that an application that doesn't show the PFS folder like nautilus does, will still let me have access to the shared contents.

Is there a way to 'hack' PFS to be linked/mounted under ~/Documents ?

Appreciate any hints or tips.

Errr please excuse my ignorance/lack-of-understanding... what's PFS? :S 
What you want to do can be achieved by setting permissions correctly. I don't know how to make upcoming files fully accessible by both accounts, but I could make a shell script to give those permissions when you click a launcher. That way, when you add new files or modify anything with one account, you can click the launcher to re-give full permissions to any account. You can also do it before an attempt to modify them, so that you have no trouble.

Let's say the shared folder is /home/user1/Documents/share.
First create, for each user, a text file with this content:
```

#!/bin/bash

sudo chmod a=rxw -R /home/user1/Documentos/share

```Let's say you save it in each user's home folder, and the file is called "fullpermissions". So you have "/home/user1/fullpermissions" and "/home/user2/fullpermissions".

Then create a panel launcher, for each user, with these characteristics:
Type: application in terminal
name: whatever you want
Command: sh /home/user1/fullpermissions
(and "sh /home/user2/fullpermissions" for user2).

Well, everytime a user modifies the files inside the folder, a click on the launcher will reset the permissions to read&write&execute for everyone for every file.
I know this isn't the best and straightforward solution, but could do the job, at least.
Hope you find this useful...

---

### Post by hedge.hog on 2010-05-15
> **gadolinio said:**
> Errr please excuse my ignorance/lack-of-understanding... what's PFS? :S 

Hope you find this useful...

Sorry should have been more explicit PFS is Personal File Sharing (on Lucid: System>Preferences>Personal File Sharing).

Thanks for the script suggestion, I was hoping there was some in-built way I had missed.  I'll probbaly try what you suggest.
I did wonder about the sudo passord prompt, which would mean the file creator would have to run the script.

Best wishes.

---

### Post by gadolinio on 2010-05-15
> **hedge.hog said:**
> Sorry should have been more explicit PFS is Personal File Sharing (on Lucid: System>Preferences>Personal File Sharing).

Thanks for the script suggestion, I was hoping there was some in-built way I had missed.  I'll probbaly try what you suggest.
I did wonder about the sudo passord prompt, which would mean the file creator would have to run the script.

Best wishes.

Yes, the sudo prompt is a hassle. But I was thinking that you could use the script, give the password, and then use the application you want or manage files manually without any problem until you switch to another account, where you would probably have to run the script again. Am I right?
I did some research in the web and found many sites about this subject; they proposed using chmod in the same way, which wouldn't do the job with upcoming files. One of those sites even said that there wasn't a solution for what you want to achieve, unless you use a directory in a different partition.
I tried using SGID, but it doesn't solve the problem with new files; these are owned by the user who created them, and even if other users belong to the same group the permissions are read only for the group :S

---

### Post by sisco311 on 2010-05-15
> **hedge.hog said:**
> Hi, 
I was hoping this would be simple, so suspect I don't know the Ubuntu way:
- Two local user accounts
- Both want full access to all current and upcoming content of a folder of one of the accounts, e.g. family pictures.


[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

> **hedge.hog said:**
> 

Is there a way to 'hack' PFS to be linked/mounted under ~/Documents ?

Appreciate any hints or tips.

Once you created the shared directory, you can create symbolic links to it in the users home:
```
ln -s -T /home/shared /home/username/Documents/Pictures
```

---

### Post by Morbius1 on 2010-05-15
(1) "Personal File Sharing" is for sharing the "Public" folder and only the "Public" folder with others on your home network. It has nothing to do with sharing them between local login users.

[COLOR=Blue] EDIT: Please ignore the following. I was directing you to sisco311's howto. No need to do that since he showed up himself. :)[/COLOR]

(2) If you want all local users to have read/write access to current and future directories and files then I would suggest **bindfs.**

For example if you add a line in /etc/fstab that looks like this:
```
bindfs#/home/user1/Documents/Share /home/user1/Documents/Share fuse perms=0666:+X 0 0
```* All directories will save with mode = 777 ( read / write access to everyone )
* All files will save with mode = 666 ( read / write access to everyone )

You'll need to install bindfs first though: **sudo apt-get install bindfs**

For other fun facts and better examples see: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by HiImTye on 2010-05-15
make your second account belong to the same group as the first account.
right click on the folder you want to share then go to properties > permissions
where it says 'group' change permissions to 'read/write'

alternatively, you could give read/write to 'others' and not have to mess with groups.

finally, click 'apply permissions to all files and folders' or w/e at the bottom

---

### Post by Morbius1 on 2010-05-15
I do not believe that any attempt to use standard linux file permissions will result in the desired affect that the original poster wants.

Every time user1 saves a file to the target directory, it will save as owner=user1, group=user1, and mode=0644. User1 can read/write but everyone else will only be able to read.

Perhaps I misunderstood the OP's original requirement. I saw it as user1 being able to write to user2's file. That's why I suggested bindfs.

---

### Post by gadolinio on 2010-05-15
> **Morbius1 said:**
> I do not believe that any attempt to use standard linux file permissions will result in the desired affect that the original poster wants.

Every time user1 saves a file to the target directory, it will save as owner=user1, group=user1, and mode=0644. User1 can read/write but everyone else will only be able to read.

Perhaps I misunderstood the OP's original requirement. I saw it as user1 being able to write to user2's file. That's why I suggested bindfs.

Right. I also understand this is the problem. Sisco311's HowTo deals with that issue; I've downloaded it and will try it out later. Thanks, btw!

---

### Post by hedge.hog on 2010-05-15
> **sisco311 said:**
> [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)



Once you created the shared directory, you can create symbolic links to it in the users home:
```
ln -s -T /home/shared /home/username/Documents/Pictures
```


Thank you sisco311!
That does indeed do what I wanted to do.

Best wishes.

---

