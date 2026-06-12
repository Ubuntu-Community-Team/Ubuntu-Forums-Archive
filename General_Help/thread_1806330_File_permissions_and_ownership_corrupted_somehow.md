---
title: "File permissions and ownership corrupted somehow"
date: 2011-07-17
forum: General Help
---

### Post by SingingBush on 2011-07-17
For some unknown reason some folders within my *Videos* folder can no longer be accessed.  I did an **ls** in the terminal and it shows the permissions are showing question marks:

```

d????????? ? ? ? ?                ? Season-1
d????????? ? ? ? ?                ? Season-2
d????????? ? ? ? ?                ? Season-3

```

---

### Post by AlphaLexman on 2011-07-17
Did you shutdown properly/completely the last time?

If not, un-mount the drive and run the file system check utility '**fsck**'

---

### Post by SingingBush on 2011-08-02
This just happened again on another folder.  I've raised a [bug report for it]("https://bugs.launchpad.net/ubuntu/+bug/819947") on launchpad.  It happened after doing *chmod* on a folder (the last folder this happened to had also been changed via chmod as well)

I did
```
sudo chmod 644 /path/to/files/
```

then listing them:
```
ls -l /path/to/files/
```

They show up as:
```
-????????? ? ? ? ? ? filename
-????????? ? ? ? ? ? filename
-????????? ? ? ? ? ? filename

```

I've seen a similar thread [here]('http://ubuntuforums.org/showthread.php?p=8176244') but restarting has not helped me.  Also, I am using the default: ext4

---

### Post by SingingBush on 2011-08-02
> **AlphaLexman said:**
> Did you shutdown properly/completely the last time?

If not, un-mount the drive and run the file system check utility '**fsck**'

I've tried booting from a live cd and running:
```
fsck.ext4 -fyv /dev/sda1
```

This didn't help but to be fair I've never used *fsck* before so I don't really know if that was the right thing to do.

---

### Post by AlphaLexman on 2011-08-02
In your first post, you made a reference to **_your_** Videos directory...

You also posted a 'sudo chmod 644 /path/to/files'

You shouldn't need 'sudo' in your $HOME dir

FYI: ALL directories need to be executable in order to read the files inside them.

Maybe you are setting dirs to 644 instead of 755, which might duplicate your problem.

Check the parent directory of the problematic dirs with 'ls -l' and make sure dirs are at least 'drwxr-xr-x' or better.

---

### Post by SingingBush on 2011-08-02
Cheers AlphaLexman.  I can't believe it was that simple.

I should have used
chmod 644 /path/to/files/*****

instead of
chmod 644 /path/to/files/

I've put the folders back to 755 and can now access my files again.

---

### Post by AlphaLexman on 2011-08-02
You never quit learning do you?

---

