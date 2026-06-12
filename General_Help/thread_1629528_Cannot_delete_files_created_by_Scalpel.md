---
title: "Cannot delete files created by Scalpel"
date: 2010-11-23
forum: General Help
---

### Post by error691 on 2010-11-23
I ran Scalpel to retrieve some files from an old HDD, what I didn't realise is how much larger the output from Scalpel is than the original disk space.
So what happened is at about 5% of files carved (pass 2/2) my disk space was full and the program aborted.

Then when I rebooted Ubuntu I can't get in unless using Recovery Mode.
I think this is because there is no disk space left. The error I get is to do with Gnome Power Manager not being configured, I never had this error before.

So I went into CLI prompt and performed 'find -maxdepth 2 | grep *.mpg' and I can see a tonne of mpg directores called ./~/mpg-1-6, ./~/mpg-1-7, etc, and they all have lots of files.

Now I have no way of deleting these, I tried using 'sudo rmdir */*mpg' and it cannot find the directory.
When I go to my home folder and 'sudo ls -al' these aren't listed.
The only way I can see them is using the 'find' command.

Can I chain the find command with a delete command somehow?

---

### Post by wilee-nilee on 2010-11-23
Have you tried alt-f2 then gksudo nautilus to get in via root. If you send to trash in root though your better to set the preferences to just delete not to go to root trash. I have never gotten root trash to open. I always have a direct delete anyway so trash means nothing to me anyway, so I haven't like really tried to get root trash open other then clicking on it..

---

### Post by error691 on 2010-11-24
I tried alt-f2, it just asks me to login again.
Then gksudo nautilus, I get an error saying it cannot open display.

I should reiterate that I am in CLI prompt after choosing recovery mode to login.

I cannot get the GUI to work at all, perhaps due to no disk space (since Scalpel used it all).

---

### Post by error691 on 2010-11-24
I'm trying to delete some files and get permission denied.
This is with me using sudo, eg. something like:

sudo find ./ -name *.mpg | xargs rm -Rf

So I tried to chown or chmod the directories/files but also permission denied.

I thought sudo meant you are omnipotent but there seems to be a higher level.
When I installed Ubuntu I don't recall it asking me to create a root account so I can't just su into that... =(

This problem I have is my disk is full and I can't use Ubuntu, so I'm hoping for a solution other than install over the top.

---

### Post by mschira on 2010-11-24
Got any other operating systems installed other than Ubuntu?
M.

---

### Post by stuarttanner on 2010-11-24
you could try typing sudo nautilus in the terminal and deleting files that way?

---

### Post by Verbeck on 2010-11-24
> **stuarttanner said:**
> you could try typing sudo nautilus in the terminal and deleting files that way?
gksudo nautilus
not sudo

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by bonixavier on 2010-11-24
> **error691 said:**
> 
sudo find ./ -name *.mpg | xargs rm -Rf
try ```
sudo find (do you really need sudo for find?) ./-name *.mpg | **sudo** xargs rm -Rf
```

It's a new command after the pipe. Or you could just go sudo su and have a root shell.

---

### Post by s.fox on 2010-11-24
Please create only create one thread per problem.

Threads merged.

---

### Post by error691 on 2010-11-24
Thanks for the suggestions.
I can't get nautilus to run so that option is taken away.

Already tried using find and rm together, the command I used is further up the page.
I just get 'permission denied', even if using sudo.

So that leaves me with no way of deleting these directories and files.
There must be some permissions issue, these files were created by Scalpel.

I also have Windows 7 installed which is how I'm able to get to the forums.
Maybe I will use Ubuntu boot from CD, backup my files onto an external HDD, then wipe Ubuntu off?

---

### Post by bonixavier on 2010-11-24
> **error691 said:**
> Thanks for the suggestions.
I can't get nautilus to run so that option is taken away.

Already tried using find and rm together, the command I used is further up the page.
I just get 'permission denied', even if using sudo.

So that leaves me with no way of deleting these directories and files.
There must be some permissions issue, these files were created by Scalpel.

I also have Windows 7 installed which is how I'm able to get to the forums.
Maybe I will use Ubuntu boot from CD, backup my files onto an external HDD, then wipe Ubuntu off?
You haven't tried "sudo su". No one disobeys root. It's not allowed. Try doing that and using rm to delete the files.

---

