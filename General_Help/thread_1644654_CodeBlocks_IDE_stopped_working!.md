---
title: "Code::Blocks IDE stopped working!"
date: 2010-12-13
forum: General Help
---

### Post by Sugoi48 on 2010-12-13
I know this might not be the right spot to post this, but I'd been using Code::Block IDE for quite a while, but now it won't open. When I try to run it, it says in the panel "Starting Code::Blocks IDE", but no window opens and it disappears from the panel a few seconds later. I've tried reinstalling a few times with no luck.
Any ideas? Also, where should I post this next time?
Thank you!

---

### Post by ean5533 on 2010-12-13
I don't know if this is the right forum either, but unless/until a mod moves the thread, let's get the ball rolling by trying to run the program from the command line and seeing what errors are spit back out. Open up a terminal and run

```
codeblocks
```

and paste the output.

---

### Post by Sugoi48 on 2010-12-13
Thanks! This is what I got:
[INDENT] nigel@nigel-laptop:~$ codeblocks
Exception: An exception has been raised!

The application encountered an error at configmanager.cpp, on line 211.
The error message is:

TinyXML error: Error document empty.
In file: /home/nigel/.codeblocks/default.conf
At row 0, column: 0.

Code::Blocks Version revision 0 (gcc 4.4.1, build: Sep 13 2009 19:33:51)
nigel@nigel-laptop:~$ 
[/INDENT]It looks like I'm missing files, but I'm not sure which ones. Also, I would've thought that reinstalling would get those files back.

---

### Post by ean5533 on 2010-12-13
> **Sugoi48 said:**
> It looks like I'm missing files, but I'm not sure which ones. Also, I would've thought that reinstalling would get those files back.

Default apt-get policy is not to remove/alter configuration files when uninstalling a program. That means if a file goes missing but the rest of your profile is still there, reinstalling the program won't fix the problem.

There is a way around this: using the **purge** option. Purging a package will uninstall and AND delete all profile settings for that program. In this case that means /home/nigel/.codeblocks/ gets wiped out.

**[COLOR="Red"]WARNING:[/COLOR]** I've never used code::blocks so I don't know what stuff it stores in your profile. It might be important stuff. For example, it MIGHT store projects that you've worked on in there (programs shouldn't do that, but sometimes they do). Make sure you back up any projects and code files that you've used with code::blocks before purging, just to be super safe. Or, if you've already got them saved somewhere else, don't worry about it.

With that warning aside, here's the command to purge a program:

```
sudo apt-get purge PROGRAMNAME
```

Replace PROGRAMNAME with the program you want to completely remove; in this case, codeblocks. After you've done that, try installing again and see if things work better for you.

---

### Post by Sugoi48 on 2010-12-13
I tried the purge and reinstall, but it didn't seem to change anything. Any other ideas?

---

### Post by ean5533 on 2010-12-13
That's really strange. That empty default.conf file should have been deleted when purging code::blocks. Well then, let's try deleting that file manually:

```
rm /home/nigel/.codeblocks/default.conf
```

If for some reason you want to save that file (just in case), rename it instead:

```
mv /home/nigel/.codeblocks/default.conf /home/nigel/.codeblocks/default.conf_BAK
```

Then try starting it up again and see what happens.

---

### Post by Sugoi48 on 2010-12-13
VICTORY IS OURS!
I ran the first bit of code, now everything is back to normal.
Thank you everyone! :D:D:D

---

