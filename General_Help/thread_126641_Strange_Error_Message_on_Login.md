---
title: "Strange Error Message on Login"
date: 2006-02-07
forum: General Help
---

### Post by KevRus on 2006-02-07
I haven't booted into Ubuntu in a while, and I finally decided to today and received this error when logging in my profile:

Your $HOME/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permission.

I don't notice anything strange when running Ubuntu and everything else seems to be working fine.  I was able to login as usual.

Another question I have is...For some reason when I run Ubuntu I have this nasty "jump" that occurs every 2 seconds or so.  It can be annoying when gaming or even typing, as there's a delay in the movement every 2 seconds.  What's causing this?

Thanks in advance!

-KevRus

---

### Post by christhemonkey on 2006-02-07
sounds like you should change the permissions of that file.

In a terminal,
```
cd ~
sudo chown your_user_name .dmrc
sudo chmod 644 .dmrc
```

---

### Post by UbuntuConvert on 2006-02-07
I am also getting this message at log on. The message first started after completing the update process on a fresh install and restarting.

@christhemonkey:

I have run the commands you specified, rebooted and checked permissions and they are set as the error msg specifies but I still get the same warning when logging in.

Any other suggestions?

---

### Post by juancnuno on 2006-02-07
I did an ls on my .dmrc and this is what it looks like:
```

$ ls .dmrc
-rw-------  1 nuno nuno 26 2005-10-17 15:45 .dmrc

```
Aren't those 600 permissions, and not 644?  Man, that octal way of specifying permissions is inane.

So yeah, try setting the permissions to 600, so it looks like mine.

---

### Post by christhemonkey on 2006-02-07
Hmm yeah, they make my head hurt!

---

### Post by KevRus on 2006-02-07
I still get the error message after following those commands. :(

Also, this "jump" of the desktop environment is getting annoying.  I look at my system stats and the CPU usage is fine and everything looks normal. O_o

---

### Post by christhemonkey on 2006-02-08
Is the screen sort of flicking when you move the mouse?

---

### Post by KevRus on 2006-02-12
I don't know, it's hard to explain but the actual mouse cursor doesn't seem to flicker.  However, in Firefox for instance, when I scroll down the scrollbar it freezes and stays in its place for a second and then jumps down to where I moved my cursor.  When playing games, the cursor moves fine, but the graphics will freeze for a second, then speed up to catch up with where it should be and do this over and over.

---

### Post by Red Knuckles on 2006-02-12
[QUOTE=juancnuno]I did an ls on my .dmrc and this is what it looks like:
```

$ ls .dmrc
-rw--------  1 nuno nuno 26 2005-10-17 15:45 .dmrc

```
Aren't those 600 permissions, and not 644?  Man, that octal way of specifying permissions is inane.

So yeah, try setting the permissions to 600, so it looks like mine.[/QUOTE]

I'm getting the same error message after using 'Automatix'. When I ran 'ls .dmrc' I got '.dmrc' only. I then ran:
sudo gedit .dmrc
and added:
-rw--------  1 nuno nuno 26 2005-10-17 15:45 .dmrc
but this did not correct the problem. I notice that the error message says '$HOME/.dmrc' but Haven't figured out what that means yet. Anymore advice on this problem???:confused:

---

### Post by Red Knuckles on 2006-02-12
Fruther more I can't find any such file [either '.dmrc' or 'HOME/.dmrc'] on my computer. Is it possible that the file it's looking for has been removed???:confused:  And if so what to do to recreate it??? I thought that's what I did with 'sudo gedit .dmrc'.:rolleyes:

---

### Post by nanotube on 2006-02-12
hey
to get the long output from ls, do the following:
ls -al .dmrc
that will show you detailed information on the file. just "ls .dmrc" will just show you the filename. 
do NOT add "-rw-------- 1 nuno nuno 26 2005-10-17 15:45 .dmrc" to your file, that does not do anything with permissions, just changes the contents of the file, which is not what you want.

---

### Post by nanotube on 2006-02-12
oh, and by the way, "$HOME/.dmrc" means the file .dmrc is in your home dir. usually, your homedir would be /home/username (where username is your actual username on the system). sometimes you might also see "~/.dmrc", the tilde ~ also means "your home dir".

---

### Post by Red Knuckles on 2006-02-13
a

---

### Post by Red Knuckles on 2006-02-13
Woops! I DO have a .dmrc file.:eek:  I forgot there are such things as hidden files. When I run ls -al .dmrc I get:
-rw-r--r--  1 ben ben 52 2006-02-12 18:22 .dmrc

So what do I do or change to get rid of the error message???:rolleyes: When I open .dmrc I get:
.dmrc [~] - gedit

and the file is empty. I'm guessing something should be in the file but I have no idea what it should be?

---

### Post by nanotube on 2006-02-13
hmm, rw-r--r-- is equivalent to 644 permissions, which is what your original error message asks for... 

aha, a little google searching turned up this thread:
[http://forum.deviantart.com/os/unix/528986/](http://forum.deviantart.com/os/unix/528986/)

looks like you should also check to see what permissions your home directory has. run command 
```
ls -al /home/username
```
and see what is says. if it looks like "drwxrwxrwx", then you should change it to drwxr-xr-x, by running the following command:
```
chmod 755 /home/username
```
(and of course, replace the word username with yoru actual username.)

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=nanotube]hmm, rw-r--r-- is equivalent to 644 permissions, which is what your original error message asks for...

aha, a little google searching turned up this thread:
[http://forum.deviantart.com/os/unix/528986/](http://forum.deviantart.com/os/unix/528986/)

looks like you should also check to see what permissions your home directory has. run command
```
ls -al /home/username
```
and see what is says. if it looks like "drwxrwxrwx", then you should change it to drwxr-xr-x, by running the following command:
```
chmod 755 /home/username
```
(and of course, replace the word username with your actual username.)[/QUOTE]

Thanks, Nanotube, The command 'chmod 755 /home/username' corrected the problem for me.:-D  Now I've got 2 more error messages to fix, both involving permissions.

---

### Post by nanotube on 2006-02-13
haha nice, out of the frying pan and into the fire, eh? :)
so what are your other permissions probs?

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=nanotube]haha nice, out of the frying pan and into the fire, eh? :)
so what are your other permissions probs?[/QUOTE]

Um, yeah, well, now I've really screwed the pooch! I tried to change the last line in 'sudo visudo' to:

%admin ALL=(ALL) NOPASSWD: /usr/bin/firestarter

so it wouldn't ask for a password every time I logged in. Don't know if that's normal but I don't remember it doing so until AFTER I ran Automatix. At any rate I now can't do ANYTHING in root. I get an error message like:

ben@ubuntu:~$ sudo apt-get update
Sorry, user ben is not allowed to execute '/usr/bin/apt-get update' as root on localhost.localdomain.

So now I really need help. I'm wondering about some sort of recovery mode. Will try to see if I can find anything to read but any help would be greatly appreciated.

---

### Post by nanotube on 2006-02-13
hmm, not sure how to recover from that one. i would suggest you start a new thread and see if someone offers a solution...

---

### Post by nanotube on 2006-02-13
hey... try the following:
reboot, and in the grub menu choose one of the "recovery mode" kernel options. this should boot up and log you in as root.
when you are in, type "visudo" and edit that line, so that instead of 
```
%admin ALL=(ALL) NOPASSWD: /usr/bin/firestarter
```
it says
```
%admin ALL=(ALL) ALL
```
and then, if you still want to be able to run firestarter without entering your password, add the following line:
```
username ALL=(ALL) NOPASSWD: /usr/bin/firestarter
```
(where of course instead of "username" you put in your actual username on the system).
well, try that and see if that solves your problems. :)

---

### Post by Red Knuckles on 2006-02-14
This thread:

[http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter)

solved the problem of how to have firestarter to start on login without having to enter password. It just starts and there is an icon in the system tray so you KNOW it's working.:)

---

