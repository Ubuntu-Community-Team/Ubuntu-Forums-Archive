---
title: "setting file attributes / selective access"
date: 2009-10-27
forum: General Help
---

### Post by yanvolking on 2009-10-27
Hello Community,

I have heard that linux allows establishing different levels of file/directory access to different users :

read only
read and write
read and write and execute

for :

main user (eg administrator)
other specific users or user groups
rest.

In other words If as administrator I want all my files and directories to give me read write and execute possibilities, but only read for the rest of persons using my computer, how do I go about it?

Thanks

---

### Post by Giblet5 on 2009-10-27
> **yanvolking said:**
> Hello Community,

I have heard that linux allows establishing different levels of file/directory access to different users :

read only
read and write
read and write and execute

for :

main user (eg administrator)
other specific users or user groups
rest.

In other words If as administrator I want all my files and directories to give me read write and execute possibilities, but only read for the rest of persons using my computer, how do I go about it?

Thanks

You don't really want to do that for ALL of your files, do you? Don't you want some of them readable only by you?

Well, assuming that you know what you want...

Bring up a terminal window and paste these commands in:

```
sudo find $HOME -type d -exec chmod 755 {} \; -exec chown $LOGNAME:$LOGNAME {} \;

# and

sudo find $HOME -type f -exec chmod 644 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

That will assign exactly the permissions you SAID you want...

[Here is one]("http://www.tuxfiles.org/linuxhelp/filepermissions.html") of MANY overviews of Linux file permissions.

---

### Post by yanvolking on 2009-10-27
Hi Giblet5,

Thanks for the tip.  I looked at teh link you proposed at the bottom of your message and decided to work in symbolic mode rather numeric mode as you suggested.  I can now set permissions for files.  but is a typical instruction for setting permissions for files is (example) 
Add execute permissions for group:
		$ **chmod g+x testfile**
"testfile" being a file;

what are the instructions for setting permissions for directories?

Thanks

---

