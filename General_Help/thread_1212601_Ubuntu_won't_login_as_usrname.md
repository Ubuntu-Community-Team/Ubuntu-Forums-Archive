---
title: "Ubuntu won't login as usrname"
date: 2009-07-13
forum: General Help
---

### Post by mantisdolphin on 2009-07-13
Somehow I lost my /home/[usrname] directory.  When I login to Ubuntu, it tells me that my /home/[usrname] "does not appear" to be there.  Then I get offered a chance to login as root, but with nothing visible on the screen, or  I am recommended to reboot and try recovery mode.  I tried the safe reboot, and it checked the file system, but the only thing I can really do to try to fix the problem is drop into root at a terminal.  I changed the permissions on my home directory and usrname directory, though with no luck.

Then I booted into Puppy Linux, and did a properties on the backup of my username directory from yesterday and the hosed one from today (it's still there and I can see it), comparing them.

So the one I backed up yesterday says, 

"Owner, Group: root, root"
"Extended attributes: None"
"Permissions -rwxrwxrwx"

The hosed one says,

"Owner, Group: ftp, ftp"
"Extended attributes: Not Supported"
"Permissions -rwx------"

Okay, so what, if anything, do I have to do to get my hosed username directory back in line?  How do I change owner, group from "ftp"?  The system had complained that my /home directory "must be owned by user and not writable by others."   That's when I backed up the -rwxrwxrwx one yesterday, changed permissions on the "new" one, and was fine until later today (logged in this morning, tried to log out this evening and found trouble: Ubuntu didn't seem able to access anything in the username directory--themes, wallpaper, etc., started to disappear.  It was weird.)

The backup is on a Windows partition (NTFS I think)--is that giving me a useless list of permissions?

Thanks in advance for any suggestions or advice on this.

---

### Post by shane2peru on 2009-07-13
Yes, more than likely your permissions are not correct on your ntfs partition.  I know that fat32 doesn't do permissions, and would assume that to be the problem with your ntfs too.  You need to re-set your owner for your home directory like this:
```

sudo chmod -Rv username:username /home/username

```
That should get you back in.  

Shane

---

### Post by mantisdolphin on 2009-07-14
Thanks!  

I couldn't get the "username:username" part to work in the recovery booted Bash.  The message was returned to check usage on chmod in man.  

I did do something else though slightly different, and now my window manager seems absent (though I'm posting this from a browser in the affected account!).  

At root I typed in 

```
chmod 777 home 
```

That gave all rights on the /home directory.

Then I went into the /home directory and typed this for the user account:

```
chmod -Rv 750 username
```

Then the screen scrolled lines like crazy, changing to permissions 750 every file in the username directory.  

I logged in no problems!  But I'm having functionality problems in the account, e.g., no window manager seems present.  

What did I do wrong?  Is there anyway to correct it?  Thanks in advance!

---

### Post by shane2peru on 2009-07-14
Really, it would be out of my range to fix your issue.  I wouldn't say it is unfixable, I'm just not sure as to the way of doing it.  What I would do is this, create a new user.  You can do this via command line with:
```

sudo adduser username

```
It will ask for a password and other stuff, when you are done, you should be able to log into the new user, transfer your files and you are all done, then you can delete the old user.  Or you can delete the older user config files, and then move your files, delete that users folder, and re-create that user with the above mentioned command. Then move your files back.  This is a quick fix, and not a full solution for the problem.

Shane

---

### Post by mantisdolphin on 2009-07-16
@shane2peru: Belated thanks for offering ideas!  Most appreciated. :) 

I did get my system back.  The window manager came back once I reinstalled nVidia driver and reinstalled Simple CompizConfig Settings Manager.  I'm not sure which did the trick though.  It does suck not having a window manager though!  No new windows can be called forth.  

I also considered your second suggestion about adduser and copy files over.  And I was close to trying that if some version of the changing permissions approach didn't work.

---

