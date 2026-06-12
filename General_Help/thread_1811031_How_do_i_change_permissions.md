---
title: "How do i change permissions"
date: 2011-07-24
forum: General Help
---

### Post by shaquille110 on 2011-07-24
Hi there.

I am trying to change permissions of a folder to read/writeable but i am not aware of the command. The folder i wish to change is the /opt/ file, i wish to change the settings because of various scripts i am running which require r/w permissions.

I am a bit of a newbie if you could share the command line it would be appreciated :)

Thanks for the help in advance :)

---

### Post by nothingspecial on 2011-07-24
The command is chmod

Be very very careful

Read this

[http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html)

---

### Post by 3rdalbum on 2011-07-24
Depending on what the scripts do, they might need root permissions (through using the 'sudo' command) or might need to be placed somewhere writable.

It's very bad security practice to loosen the permissions of any system folder.

If these are scripts that you've written, if they need to be run as the user, then you should rewrite them to use the user's home directory rather than requiring a write to /opt/.

---

### Post by shaquille110 on 2011-07-24
Thanks maybe changing the location of the files is best :) Thanks guys :)

---

### Post by shaquille110 on 2011-07-24
Okay what i am trying to install is [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) and yes i know there are alternative easier options but i am used and like to lampp. 

When extract to /opt the file works but i just tried to do it in my user folder it doesn't work at all.

---

### Post by shaquille110 on 2011-07-24
This issue has been resolved.

---

