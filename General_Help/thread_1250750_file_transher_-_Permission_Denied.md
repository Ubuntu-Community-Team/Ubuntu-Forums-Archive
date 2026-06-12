---
title: "file transher - Permission Denied"
date: 2009-08-26
forum: General Help
---

### Post by Dr. Frankfurter on 2009-08-26
First time to Linux

trying to move a file from desktop to /home or anywhere else....

here is what i did  

mv  filename /home

error permission denied - same error no matter where i try to move the file.

i really do not know anything about linux so keep that in mind with the response(s)

---

### Post by RedSingularity on 2009-08-26
Use "sudo" before issuing the command.  

sudo mv filename /home

---

### Post by Dr. Frankfurter on 2009-08-27
awesome that worked. Thanks.

---

### Post by skillllllz on 2009-08-27
@shadow121  In my opinion I don't think simply telling him to put sudo in front of the command is ideal. He openly stated that he is a new user and without properly informing new users about the power of the commands we suggest to them, we set them up for potential failure and possible bad habits. I'm sorry if it seems like im jumping on you about this, I am not; I respect you. I do, however, care about our community and the information we share with one another.

@Dr. Frankfurter  "sudo" allows you to execute other commands as an administrator. This is very useful/necessary in many cases, but it is also risky and unecessary in others. Since you are a new user, I would not advise simply putting sudo in front of a command unless you truly understand what you are attempting. Information to help you better understand sudo and gksu, a different but similar command, can he found here: [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo) and here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by SuaSwe on 2009-08-27
In Terminal, when in the folder where the file you want to move is located, type:

```

ls -la

```

This will show hidden (the ones with dots before the file name) and unhidden files and their permissions, like so:

```

**-rw-r--r--  1 owner group**   100000 2009-08-23 17:21 Example.mp3

```

The **[FONT="Courier New"]-rw-r--r--[/FONT]** bit denotes the permission level (in this case read-write access for **owner** and only read access for **group** and other users - see more examples, explanations and advice on changing permissions [[color="blue"]here[/color]]("https://help.ubuntu.com/community/FilePermissions").)

Some files do not allow access by anyone except root because they are system files or otherwise important, so in cases where a file is owned by root, it's unwise to use sudo to move or change it unless you know for sure what it is. :)

---

### Post by bchurchill on 2009-08-27
> **Dr. Frankfurter said:**
> First time to Linux

trying to move a file from desktop to /home or anywhere else....

here is what i did  

mv  filename /home

error permission denied - same error no matter where i try to move the file.

i really do not know anything about linux so keep that in mind with the response(s)

In addition to the above, if you're trying to put a file in a place you want to keep for personal use later you probably want to move it into /home/yourusername (instead of typing that you can type ~ instead).  This is the typical spot for personal files.  Permissions are already setup for you in this folder so you generally don't need to worry about them.  Good luck!

Edit:  to learn more about file permissions, take a look at [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for a reasonably comprehensive overview.

---

### Post by SuaSwe on 2009-08-27
> 
Edit: to learn more about file permissions, take a look at [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for a reasonably comprehensive overview.


Too slow! Look above, I already linked it. ;)

---

### Post by RedSingularity on 2009-08-27
> **skillllllz said:**
> @shadow121  In my opinion I don't think simply telling him to put sudo in front of the command is ideal. He openly stated that he is a new user and without properly informing new users about the power of the commands we suggest to them, we set them up for potential failure and possible bad habits. I'm sorry if it seems like im jumping on you about this, I am not; I respect you. I do, however, care about our community and the information we share with one another.


Not a problem buddy, i should have thought of that :)

---

