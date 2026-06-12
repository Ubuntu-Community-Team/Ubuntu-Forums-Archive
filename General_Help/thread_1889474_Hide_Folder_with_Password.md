---
title: "Hide Folder with Password?"
date: 2011-12-01
forum: General Help
---

### Post by jsandhu on 2011-12-01
I am on Ubuntu 11.04 and still a novice, I was wondering if is it possible to hide Folders with a password, I don't want to compress them or encrypt them or anything, just want to hide them so only the person knowing the password can access them, Is it possible?

Thanks in advance.

---

### Post by duke.tim on 2011-12-01
hmm You could always s change the permissions to root (or another user) on a said folder. which would prevent other people logging onto the computer from seeing it. This won't stop people from seeing a folder if it is on an external hard drive (plugged into another computer)

[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

The easiest way to do this would probably be

*Warning I remember reading about this not being advised* Just be careful because in this mode you can delete protected system files and change their permissions as well.
```
gksudo nautilus
```

browse to folder -> right click -> properties -> permissions -> change owner -> change so only owner has access.

The other way to do this is via the terminal.

---

### Post by jsandhu on 2011-12-02
ok, how about if I create a new user, will that user have access to my files?

---

### Post by DapperMe17 on 2011-12-02
Even though you've mentioned that encrytion isn't necessary, this program may be an "easier" way to accomplish what you are looking for. 

Cryptkeeper

See here for a description.....[http://www.makeuseof.com/tag/encrypt-protect-computer-files-cryptkeeper-linux/](http://www.makeuseof.com/tag/encrypt-protect-computer-files-cryptkeeper-linux/)

When the folder is active, it shows....when it is inactive, it's stowed away among the "hidden" files, and is not be visible. 

It also works on a password, like you've mentioned.

---

### Post by jsandhu on 2011-12-02
I installed it and checked it out, does the work but there is one problem, to delete the encrypted folder all you have to do is click on the cryptkeeper icon select the stash right click it and select delete and the folder is gone, so if I have my files saved inside it they're gone with it?

not too safe, it should aleast ask for password before deleting the folder.

---

### Post by 3rdalbum on 2011-12-02
> **jsandhu said:**
> I installed it and checked it out, does the work but there is one problem, to delete the encrypted folder all you have to do is click on the cryptkeeper icon select the stash right click it and select delete and the folder is gone, so if I have my files saved inside it they're gone with it?

not too safe, it should aleast ask for password before deleting the folder.

Use this trick, then: [http://binblog.info/2011/01/30/make-directory-immutable-on-linux/](http://binblog.info/2011/01/30/make-directory-immutable-on-linux/)

---

### Post by jsandhu on 2011-12-02
ok, that is too complicated for me, sorry, I am still a noob.

---

### Post by mutley89 on 2011-12-02
This is the relevant part:
```

sudo chattr +i file_you_want_to_prevent_being_deleted

```That's all there is to it.

To reverse this use:
```

sudo chattr -i [FONT=Verdana]file
[/FONT]
```[FONT=Verdana]
[/FONT]

---

### Post by 3rdalbum on 2011-12-02
> **mutley89 said:**
> This is the relevant part:
```

sudo chattr +i file_you_want_to_prevent_being_deleted

```That's all there is to it.

To reverse this use:
```

sudo chattr -i [FONT=Verdana]file
[/FONT]
```[FONT=Verdana]
[/FONT]

I would create a blank file called ".immutable" (the dot will make it invisible, and also order it first in the list) and then make that file immutable using that method. This will prevent the folder from being deleted.

---

### Post by jsandhu on 2011-12-02
ok so I write that code on an empty file name it .immutable and put it inside the folder I want and then hide the folder with cryptkeeper, right?

so it will be hidden and can't be deleted.

so if my file name is .immutable

the code should read as : -

> sudo chattr -i .immutable

is that right?

---

### Post by jsandhu on 2011-12-02
ok I tried but that didn't worked, the file can still be deleted.

I am definitely doing something wrong.

---

### Post by Valpskott on 2011-12-02
> **jsandhu said:**
> ok so I write that code on an empty file name it .immutable and put it inside the folder I want and then hide the folder with cryptkeeper, right?

so it will be hidden and can't be deleted.

so if my file name is .immutable

the code should read as : -



is that right?

The file .immutable should be blank, that is, it should not have ANY content at all. Just place or create the file inside the folder. Then open the terminal, "cd" yourself to that folder and then run the command "sudo chattr -i .immutable" alternativly if you don't know how to "cd" you can type "sudo chattr -i /YOUR/PATH/TO/FOLDER/.immutable". "sudo" means it will ask you for your password.

(exchange "/YOUR/PATH/TO/FOLDER/" for the acctual path to your folder).

Also, I've never used chattr, so I'm not familliar of the specific switches.

The simplest way to hide something (if the other users are new to linux) is to rename your folder so that it has a "." infront of the name (rename "YOURFOLDER" to ".YOURFOLDER"). If you want to see hidden folders in nautilus (the file explorer) you hit CTRL + H to toggle hidden off and on.

The file ".immutable" would get hidden once named ".immutable" due to the "." in the beginning.

---

### Post by Valpskott on 2011-12-02
if you want to write protect something from GUI (graphical user interface) you can always hit ALT + F2 and type "gksu nautilus" the navigate to your folder -> right click -> properties -> Click Permissions Tab --> And that page will explain itself.

Someone else proposed this solution in this thread. Just giving it my vote due to it being easy for a novice to do.

---

### Post by jsandhu on 2011-12-02
yes sir, I did all that from the terminal created directory with "mkdir" created file with "touch" then "chattr +i" the file and then tried to delete the file from terminal, it didn't, tried deleting the directory, that didn't delete also but when I put the same file inside the cryptkeeper folder and tried deleting the stash again, it was gone in less than 60 seconds, also tried deleting the folder and file by right clicking and selecting move to trash, it deletes the folder and file also, so cryptkeeper can hide the file with password but if someone were to delete the stash from the cryptkeeper icon itself, then the folder and files inside it are gone with it.

back to square one I think..

---

### Post by jsandhu on 2011-12-02
> **duke.tim said:**
> hmm You could always s change the permissions to root (or another user) on a said folder. which would prevent other people logging onto the computer from seeing it. This won't stop people from seeing a folder if it is on an external hard drive (plugged into another computer)

[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

The easiest way to do this would probably be

*Warning I remember reading about this not being advised* Just be careful because in this mode you can delete protected system files and change their permissions as well.
```
gksudo nautilus
```

browse to folder -> right click -> properties -> permissions -> change owner -> change so only owner has access.

The other way to do this is via the terminal.

> **Valpskott said:**
> if you want to write protect something from GUI (graphical user interface) you can always hit ALT + F2 and type "gksu nautilus" the navigate to your folder -> right click -> properties -> Click Permissions Tab --> And that page will explain itself.

Someone else proposed this solution in this thread. Just giving it my vote due to it being easy for a novice to do.

yes I tried it sir, I can set permissions for that folder so only I have access to it but I am in a situation where someone might use this comp with my username and password and they can access that folder, that is why I was searching for an option to hide it with a password, which was found, through cryptkeeper which hides the folder and files pretty well but don't protect them from being deleted.

but anyways, thanks everyone for trying to help, I really appreciate it.

---

