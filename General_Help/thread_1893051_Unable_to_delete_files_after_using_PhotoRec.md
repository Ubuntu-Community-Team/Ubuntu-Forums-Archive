---
title: "Unable to delete files after using PhotoRec"
date: 2011-12-09
forum: General Help
---

### Post by Sxynerd on 2011-12-09
I recently recovered files from an External drive using PhotoRec.  All of my files were placed in my Home Dir and as I sort though them I am trying to delete/move them but I am denied access. 

There is a "Lock" on the file folders, 168 folders in total.  I am signed in as an Administrator.  ( I am the only user on the system.)

Is there a way to delete these files?

Thanks,
Nerd


edit:  When looking at the properties of the files; under permission it says, "You are not the owner, so you cannot change these permissions."

---

### Post by carranty on 2011-12-09
You aren't actually signed in as administrator, you're signed in as a user who can have temporary access to administrator level commands by use of the sudo/gksu command.

Open nautilus by opening a terminal and typing

```
gksu nautilus
```Enter your user password at the prompt and you'll be able to delete the files - just make sure you don't delete anything important!

EDIT : FYI, if you want to change ownership of a file or folder, use the chown command; open a terminal and type

```
sudo chown username:username path/to/folder
```

---

### Post by Sxynerd on 2011-12-15
Thanks, It worked for me a few times but now it has stopped.  

Here is the results it is telling me.


wolvee@Wolvee123:~$ gksu nautilus
Initializing nautilus-dropbox 0.7.1
Initializing nautilus-gdu extension
** (nautilus:10554): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged



..then nothing happens.  The HOME folder opens up but the only thing in it is the "Desktop".

---

### Post by Sxynerd on 2011-12-17
I just don't understand this problem.  I've restarted over and over again but it just doesn't work anymore.  I had several old laptop drives I recovered media from.  IT worked on the first couple but not on the last one.  I have 168folders with tons of crap and no way to delete it.  

I don't want to format it again.  Although this 11.10 is running slow as molasses and I've got a lag that's almost unbearable.  I was doing so well with 10.10. :0(  It makes me wonder why I don't leave well enough alone.

Screenshot.
[http://i44.photobucket.com/albums/f33/wolvee123/Screenshotat2011-12-17163315.png](http://i44.photobucket.com/albums/f33/wolvee123/Screenshotat2011-12-17163315.png)

---

### Post by davidryderuk on 2011-12-17
> EDIT : FYI, if you want to change ownership of a file or folder, use the chown command; open a terminal and type

```
sudo chown username:username path/to/folder
```



+1 for this solution.

The only change I would suggest is to use the * symbol as a wildcard.

e.g. if you have two folders, photorec.1 and photorec.2 you can use the following command to make sure your user owns both of them:

```
sudo chown username:username ~/photorec.*
```

---

### Post by Paqman on 2011-12-17
Just to be a bit more specific: the problem here is that you ran Photorec as root, so all the files it handled are owned by root. In order to modify those files you either need to be root, or your need to change the ownership so they belong to you. If it's your data then the second option seems the obvious solution.

If there's many layers of folders you may want to use:
```
sudo chown -R username:username /path/to/files
```
The -R means recursive, so that all the folders and files within that one will also change owner.

---

### Post by fdrake on 2011-12-17
> **Sxynerd said:**
> wolvee@Wolvee123:~$ gksu nautilus
Initializing nautilus-dropbox 0.7.1
Initializing nautilus-gdu extension
** (nautilus:10554): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged



..then nothing happens. The HOME folder opens up but the only thing in it is the "Desktop".
you cannot delete/edit file that belong to root, but you should be able to see it..
the command that you are using is wrong , do:
```
cd ~ ; gksu nautilus .  #note the period(.)
```

---

### Post by coffeecat on 2011-12-17
> **Sxynerd said:**
> 
..then nothing happens.  The HOME folder opens up but the only thing in it is the "Desktop".

That is because when you use a "gksu nautilus" browser it opens in root's home, not your own. The desktop folder that you see is root's desktop. You need to click on "File System" on the left and then navigate to /home and then to your home folder.

By the way, if you use a gksu nautilus browser to delete things, use a hard delete (shift+delete) otherwise deleted things go into root's trash and are not physically deleted.

Last thing. I agree with Paqman. Far better than using a gksu nautilus is to chown all those files to your ownership.

---

