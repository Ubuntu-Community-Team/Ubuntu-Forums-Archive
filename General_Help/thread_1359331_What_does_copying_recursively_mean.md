---
title: "What does copying recursively mean?"
date: 2009-12-19
forum: General Help
---

### Post by Zilioum on 2009-12-19
I use the command "cp -r" quite often. I know that it means to copy files recursively, but what difference doest that make in comparison to, lets say plain simple "cp"?

---

### Post by Puck7 on 2009-12-19
Without the -r function the directories will not be copied. Paste from [the man file]("http://www.devdaily.com/unix/linux-cp-command-man-page"):
```
-R, -r, --recursive
              copy directories recursively
```

---

### Post by Zilioum on 2009-12-19
Thanks for your answer, but I have already read the manual. I want to know why that "-r" exists and what it means, technically speaking. If you needed it for everything, wouldn't it just be "cp" instead of "cp -r"?

---

### Post by seeker5528 on 2009-12-19
You don't need the '-r' for everything, you only need it if you want to copy recursively.

[http://www.merriam-webster.com/dictionary/recursive](http://www.merriam-webster.com/dictionary/recursive)

Some of the other options work recursively already like the '-a' option, which I use much more commonly than the '-r' option since I typically want my permissions, ownership and symlinks to be preserved.

Later, Seeker

---

### Post by falconindy on 2009-12-19
cp without the recursive flag won't copy directories.

---

### Post by Zilioum on 2009-12-20
Thanks for all your answers, but I still dont know what ubuntu really does when I run "cp -r". I know recursive functions from programming, but what does it have to do with copying a file? 

> cp without the recursive flag won't copy directories.  Why? 

Concerning "cp -a": Where does it put the archives or backups? The manual isnt very clear on that.

I'm just trying to get a more in-depth understanding on what happens with certain commands.

Cheers

---

### Post by jakupl on 2009-12-20
Lets play that you want to copy a directory called "/directory"

in the directory, you have a lot of pictures but and folders with pictures.

when you do: 
```
cp -r /directory/* /here
```

you copy all the pictures and folders, where 
```
cp /directory/* /here
```

will only copy the pictures in the actual directory, not the ones in deeper folders.

----------------------------------------------------------------

Now concerning 
```
cp -a
```

it goes where you want it to go, for instance

```
cp -a /directory/* /here
```

makes it go "/here"

---

### Post by ratcheer on 2009-12-20
In simpler terms, it means copy the directory and all its files and subdirectories and all their files and subdirectories of the subdirectories and all their files, and on and on, recursively, to the bottom of the directory tree from the starting point.

Tim

---

### Post by Zilioum on 2009-12-20
Now it makes sense, thanks a lot! 

But what is the difference between "cp -a" and "cp -r" ? 
In the manual it says: 
>  -a, --archive                 same as -dR --preserve=all
      --backup[=CONTROL]              make a backup of each existing destination file

What does that mean, or for what would you need to use "cp -a"?

Cheers

---

### Post by falconindy on 2009-12-20
> Concerning "cp -a": Where does it put the archives or backups? The manual isnt very clear on that.
the "archive" implication the -a flag means that, among other things, attributes such as permissions and ownership are preserved, which is desirable when using 'cp' to make a backup of files. Normally, when copying, the permissions and owner of the **new** file are attuned to the user performing the copy. Try using sudo to copy a file out of your $HOME and you'll see what I mean. Because of this, the -a flag is used to prevent this from occurring.

'cp -a', as the man page says, is the same as using 'cp -dr --preserve=all'. So it's a recursive copy that wont follow symlinks and won't alter the permissions and ownership of the source files.

---

### Post by Scott O'Nanski on 2010-01-14
> **ratcheer said:**
> In simpler terms, it means copy the directory and all its files and subdirectories and all their files and subdirectories of the subdirectories and all their files, and on and on, recursively, to the bottom of the directory tree from the starting point.

Tim

An this, ladies and gentlemen is an EXCELLENT example of a simple, easy to understand, INTELLIGENT explanation.

Thank you, Tim.

---

