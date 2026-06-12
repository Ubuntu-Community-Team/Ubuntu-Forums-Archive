---
title: "mpg123 help"
date: 2009-11-04
forum: General Help
---

### Post by Jyscal on 2009-11-04
Greetings all. I was wondering if anyone could please help!  Im trying to figure out how to get mpg123 to play mp3s'I apologise if this has been asked often or is in the wroi forum but am really confused. Having used Windows for many years i am still very new to the amazing world of Linux. I have been through a few Threads on the Forum but none of the commands seem to work for me. For example:  mpg123 song_mp3_file.mp3 gives the error of No such file or cannot open file access error. Any help would be most appreciated.

---

### Post by soapBAR2 on 2009-11-04
Well, you have one of two problems. 

1) The file isn't at the path specified (you have to specify the full path* of the file if your terminal's "current working directory" isn't the same as the directory the file is in)

2) You have a permissions problem. Quick fix (WARNING: NOT SECURITY FRIENDLY) is

```
sudo chmod 777 /full/path/to/file.
```

* There are special shortcut keys. Eg, ~ represents "/home/myusername/, . represents "current working directory" (eg, ./subdir/subsubdir will talk about /current/working/directory/subdir/subsubdir)

==========================================================================

**_Explanation:_**

In linux, permissions are a much bigger deal (it means much better security but then you have problems like this one). Now, to tell what the permission status of the files are, just type

```
ls -l /full/path/to/file
```

and it will return something like

> -rwxrwxrwx 1 user group 0 1970-01-01 00:00 /full/path/to/file

Which is the file information in the form

permission_flags file_count user_owner group_owner filesize creation_time filepath

Now, the permission flag: 
- The first letter means "file type". Common file types are "-" (none/regular file), "d" (directory), "s" (special file), "l" (link file).
The rest is read in 3 sets (of 3 letters each). 

The first "set" is owner, the second "set" is group and the third "set" is everyone else. Now, in each set: The first letter is "read", the second letter is "write", and the third letter is "execute". So, if you had a file with permission flag

> lr-xrw--x

You can read this to mean
- It is a link file
- The user who owns the file can read it, can't write it, but can execute it.
- The group who owns the file can read it, can write it, but can't execute it
- Everyone else can't read it, can't write it, but can execute it.

The tools for editing these are
chmod - Change permission status
chown - Change owner
chgrp - Change group owner

Read through the man pages for a full explanation of these tools. Hint: use -R for recursive (to apply to directories), and remember that chmod takes arguments as numbers, full flag details and also addition/subtraction (eg, > chmod +x /path/to/file sets it to be readable by all).

---

### Post by Jyscal on 2009-11-04
Thanks Very much for The help! Ill definately be learning those shortcuts.  Ok started off at gregory@gregory-laptop:~$And made my way to gregory@gregory-laptop:~/music Where the file are making sure using ls. Even from there it say No file or  directory. In the ~ directory i tried the sudo chmod... with the same result. I also put an ogg in the folder to try that but nothing! The error it gives after No file  is code 22 file access error  but im not sure if that helps. Thanks again

---

### Post by soapBAR2 on 2009-11-04
That's definitely indicating that it's either a permissions problem or you aren't correctly addressing the path. One thing I neglected to mention is that spaces in linux command lines are verboten. If you put a space, the shell thinks the thing after the space is another argument. The way around this is twofold - either enclose the filename in ""s, or use escape characters (\) before filenames. Escape characters tell your shell to "escape" the following character - that is, interpret the next character as a symbol rather than a command. Since the " " can be interpreted as a command, you must escape it if you want to have it interpreted as a character. So, for example

```
/home/user/music/The Examples - 01 - Example.mp3
```
would be escaped to
```
/home/user/music/The\ Examples\ -\ 01\ -\ Example.mp3
```

Also - I highly doubt this is still a permissions error, but try running mpg123 as sudo mpg123. This will absolutely guarantee that you won't run into permission errors (root is all powerful).
[SIZE="4"]
_**Are you using/do you know about tab complete?**_ [/SIZE]
When you type a command, press tab and the system will try and predict what it is you're trying to type (it's almost instant even on old machines - so don't concern yourself about loading times or stressing your computer). This means you don't have to worry about proper escaping in most cases, it means you can get your commands right, and it saves time.

Hints:
- It will only complete as far as is unique - so if you name your music in the ARTIST - SONG.mp3 format, you can type ART<TAB> and it will complete to ARTIST\ -\ and then let you type in the song (or the beginning and then tab complete).
- If you press TAB twice in a row, it'll bring up a list of all the possibilities (it'll ask you if there's so many that it'll flood your screen). 
- It works for both executables (that are in your path, ubuntu has good defaults so you don't need to worry about paths) and filenames.  

So, for example, the command

> mpg123 ~/music/The Examples - 01 - Example.mp3
could be typed by
> mpg<TAB> ~/mu<TAB>/The<TAB>01<TAB>

---

### Post by Jyscal on 2009-11-04
It worked! Thanks so much. I used the mpg<TAB> command and it worked perfectly. Ill keep the others in mind as well though incase it can help someone else one day. Thanks!

---

