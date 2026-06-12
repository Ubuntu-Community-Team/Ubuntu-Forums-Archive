---
title: "default folder permissions"
date: 2010-11-29
forum: General Help
---

### Post by Dragonbite on 2010-11-29
Running Ubuntu 10.04 LTS and Gnome, I have a Shared folder (/home/SHARE) that I want my wife and I to have read/write permissions to while the kids have read-only access.  We both are part of the same group ("Parents") which, obviously, the kids are not.

The problem is when my wife saves a file in some level of this directory it saves it with her as the owner and her default group as the group.  Most often we are placing pictures in albums under /home/SHARE/Pictures/ with digiKam from our digital camera.

I don't have write access to these files (and vice verse, when I put a file into any subdirectory, she doesn't have write access) until I run ```
sudo chown <username>:Parents -R /home/SHARE 
# makes all files have "Parents" as their group

sudo chmod 775 -R /home/SHARE 
# makes all files have read/write access for the owner and members of the "Parents" group, 
# all else gets only read-only access
```

So how do I get it so when files are saved here they automatically are saved with the specified group and with a chmod of 775 (*owner/group has full access, others have read-only*)?

---

### Post by Dragonbite on 2010-11-29
Running a script may work, except I need to be in sudo (or root) and I'm not sure how to do that automatically.

---

### Post by matt_symes on 2010-11-29
Hi

Take a look at 

[http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html)

at the section[SIZE=1]
[SIZE=2]
Setting the SGID attribute on a directory : chmod g+s[/SIZE][/SIZE]

Kind regards

---

### Post by Dragonbite on 2010-11-30
Thanks!  That is great stuff (dangerous, but great)!

So I did set up all of the children of this directory with the "parent" group and used chmod g+s for the entire directory.```
sudo chgrp  parents -R /home/SHARE
sudo chmod g+s -R /home/SHARE
```

Now I need to look up more on umask and see if I can use that to set the permissions automatically for -rwxrwxr-- (owner & group get read-write, all others get read-only) for this directory only.

Thanks again!

---

### Post by Dragonbite on 2010-11-30
While I'm not quite sure about the numbering process for umask, it sounds like what I need to do is```
#umask 002 /home/SHARE 
```and this will modify the umask ONLY for the directory.  The "0" is full permissions while "2" I believe is read-only.  The default global umask is "022" which means owner-only can modify  their files ("0") while everybody else has read-only ("2").

I'll try this at home and see if this works.

Does anybody have any experience with "umask"?  I've used it, without fully understanding it, when mounting some external drive.  Now I know to be a little more careful about this but if this works it will be great!

---

### Post by WorMzy on 2010-11-30
umask is a way of restricting permissions. You understand the way that octal works with chmod, right? e.g. 7 = rwx, 5 = r-x, 0 = ---, etc.

Well umask works the opposite way, and restricts the permissions that would be granted with the chmod equivalent. So 7 *takes away* read write and execute, 5 takes away read and execute, and 0 doesn't restrict permissions at all.

So, if a person creates a file in a folder with the umask 057, then the permissions on the file will be -rwx-w---- (more or less, execute is usually left off of new files). I believe the umask on Ubuntu is 022, which creates files with -rwxr-xr-x.

---

### Post by sisco311 on 2010-11-30
A umask cannot be specified on a per-directory. 

You could use bindfs to remount the directory with permission settings. 

[thread=1460472]HowTo: Create a shared directory for local users (with bindfs).[/thread]

---

### Post by Dragonbite on 2010-11-30
Here's another question then;  is there anything wrong with setting the umask for the system to "002"?

What I am thinking is that "002" means owner/group has r+w while other has r only.

In Ubuntu, each user is usually set up by default with their own (default) group so their files will be owner/group as r+w, but since they are the only person in the group it effectively means they are the only one that can access those files.

Then, when files are saved in this /home/SHARE location where the group "parents" is automatically assigned, the people in the "parents" group has full access while everybody else has read-only.

Is there a security issue, or potential danger of setting it up as such?  I know it will REQUIRE that each person has their own group, but that's pretty easy to do.

---

### Post by Roasted on 2010-11-30
> **Dragonbite said:**
> While I'm not quite sure about the numbering process for umask, it sounds like what I need to do is```
#umask 002 /home/SHARE 
```and this will modify the umask ONLY for the directory.  

I'm about 99% positive it's all or nothing.

AKA, system-wide or nothing. No such thing as per directory umask settings in this case.  I would LOVE it if that were the case but... doesn't appear to be that way.

---

### Post by WorMzy on 2010-11-30
There's nothing wrong with changing the system-wide umask. It won't change the permissions on already existing files, and most system files are owned by root:root anyway. However, I'm not sure whether installed files adhere to umask or not, but it's probably best not to touch the "others" umask value. 

You can set the default umask in /etc/profile. This value can be changed on a per-user basis by adding "umask ###" to their ~/.bash_profile (assuming they use bash as their shell).

---

### Post by Dragonbite on 2010-11-30
> **WorMzy said:**
> There's nothing wrong with changing the system-wide umask. It won't change the permissions on already existing files, and most system files are owned by root:root anyway. However, I'm not sure whether installed files adhere to umask or not, but it's probably best not to touch the "others" umask value. 

You can set the default umask in /etc/profile. This value can be changed on a per-user basis by adding "umask ###" to their ~/.bash_profile (assuming they use bash as their shell).

If I add "umask 002" to their ~/.bash_profile then when they log in, new files are defaulted to 775, and if somebody else logs in and they have "umask 002" (the current default I think) then it would change until somebody else logs in?

Another alternative I can see is setting up a "sudo chmod 0775 /home/SHARE" for when people in the "parents" group logs out so any files they added will automatically be made more available?  Even better if it doesn't require sudo and can just run in the background even if just for their own files.

---

### Post by WorMzy on 2010-11-30
> **Dragonbite said:**
> If I add "umask 002" to their ~/.bash_profile then when they log in, new files are defaulted to 775, and if somebody else logs in and they have "umask 002" (the current default I think) then it would change until somebody else logs in?

The umasks you listed are the same. :P I assume you mean 022 the second time.

Any files created by that user during that session (with umask 002) will have the 775 permissions (or 664, owing to the lack of executable bit), but other uses won't be affected by it. One user can have umask 022, another can have 002, and another can have 077 while they're all logged in.


> **Dragonbite said:**
> Another alternative I can see is setting up a "sudo chmod 0775 /home/SHARE" for when people in the "parents" group logs out so any files they added will automatically be made more available? Even better if it doesn't require sudo and can just run in the background even if just for their own files. 

If you write a script and but it in a common directory (e.g. /usr/local/bin) you can use visudo to make that script executable (with sudo) by specific users (or a group) without a password. To make the script execute when the user logs off, add a line to ~/.bash_logout calling it.

---

### Post by Dragonbite on 2010-11-30
> **WorMzy said:**
> The umasks you listed are the same. :P I assume you mean 022 the second time.

Any files created by that user during that session (with umask 002) will have the 775 permissions (or 664, owing to the lack of executable bit), but other uses won't be affected by it. One user can have umask 022, another can have 002, and another can have 077 while they're all logged in.


I'm not sure all of that are worth the effort. Can you give an example of how this would be beneficial? Not the technical aspects but the "why".

> **WorMzy said:**
> 
If you write a script and but it in a common directory (e.g. /usr/local/bin) you can use visudo to make that script executable (with sudo) by specific users (or a group) without a password. To make the script execute when the user logs off, add a line to ~/.bash_logout calling it.

Sounds like that would work, but again is it worth the effort?

---

### Post by sisco311 on 2010-11-30
> **WorMzy said:**
> The umasks you listed are the same. :P I assume you mean 022 the second time.

Any files created by that user during that session (with umask 002) will have the 775 permissions (or 664, owing to the lack of executable bit), but other uses won't be affected by it. One user can have umask 022, another can have 002, and another can have 077 while they're all logged in.



Moreover, umask is a per-process setting. You can start an application with a different umask. For example:
```
bash -c "umask 0002 && nautilus --no-desktop /home/SHARE"
```

---

### Post by Dragonbite on 2010-11-30
> **sisco311 said:**
> Moreover, umask is a per-process setting. You can start an application with a different umask. For example:
```
bash -c "umask 0002 && nautilus --no-desktop /home/SHARE"
```

Once you've opened that application, like the nautilus you gave the example of, if I run it and leave Nautilus open while I go do other things (import from digikam into the /home/SHARE folder) it too will be influenced by the "umask 0002", as well as any other program until that nautilus is closed or the "umask" command is run in some other way (associated with another application, runs manually, etc.)?

---

### Post by WorMzy on 2010-11-30
> **Dragonbite said:**
> I'm not sure all of that are worth the effort. Can you give an example of how this would be beneficial? Not the technical aspects but the "why".

Why indeed. I don't run a multi-user system, so it's hard for me to think of examples, but if you have a user with very sensitive documents, setting a umask of 077 would prevent anyone else viewing his/her files (or at least, those files he/she creates *after* that umask is set). Alternatively, you could just remove the group+others execute permission from his/her home directory, thereby preventing them from searching it. But I suppose that method could fall down if the executable bit got set again somehow, whereas the umask method has a certain amount of fallback.

> **Dragonbite said:**
> Sounds like that would work, but again is it worth the effort?

That's a question that only you can answer. :)

The script doesn't need to be one of these fancy multifunction 200-liners you see floating about, and visudo isn't hard to use (despite the name, I think Ubuntu uses nano as an editor by default, rather than vi), so it wouldn't take long to set up.

> Once you've opened that application, like the nautilus you gave the example of, if I run it and leave Nautilus open while I go do other things (import from digikam into the /home/SHARE folder) it too will be influenced by the "umask 0002", as well as any other program until that nautilus is closed or the "umask" command is run in some other way (associated with another application, runs manually, etc.)? 

Any child process generated by the affected process will have the same umask, but any process launched from *outside* that process will have the other umask.

---

### Post by AlphaLexman on 2010-11-30
As I understand, umask works differently for files and directories.
```
umask 022
```
will set new files to "-rw-r--r--"
and directories to "drwxr-xr-x"

Directories need to be executable.

---

### Post by sisco311 on 2010-11-30
> **Dragonbite said:**
> I'm not sure all of that are worth the effort. Can you give an example of how this would be beneficial? Not the technical aspects but the "why".



Sounds like that would work, but again is it worth the effort?

Well, files created in or copied to the directory will be owned by your user, so you don't have to use sudo. I still think that using bindfs is the easiest/best way to accomplish what you want, but anyway here is a script.

Assuming that the directory contains less than 8192 subdirectories, you can use inotify to monitor it and change the permissions of a file (directory) when it's created or moved to the directory:
```
#!/bin/bash

inotifywait -m -r --format '%w''%f' -e modify -e move -e create /home/SHARE | \
while read file; do
  chmod g+w "$file"
done

```

Just add it to the autostart application.

---

