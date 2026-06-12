---
title: "How screwed am I? &gt;&gt;&gt; sudo chmod 777 /usr/bin"
date: 2011-01-21
forum: General Help
---

### Post by bigspoon on 2011-01-21
I was attempting to fix a permission error on postgresql directory
in /usr/bin/pg_ctlcluster when i ran sudo chmod 777 /usr/bin. 

I've read tons of posts that appear to say I'm screwed and have to reinstall. Really? Is this the only option? I'm new to ubuntu but amazed that sudo would let me change permissions on itself to the point where it would be useless.

Can anyone respond with their permissions settings on /usr/bin for 10.10? Maybe it would work to try change /usr/bin back to those permissions. Not sure.

Your help and comments are appreciated

---

### Post by Queue29 on 2011-01-21
You performed the command on the /usr/bin directory and not /usr/bin/* ? In that case the fix is easy. 

```
sudo chmod 755 /usr/bin
```

If you had used the -R (recursive) flag or the file path /usr/bin/* then yea you'd be screwed.

---

### Post by bigspoon on 2011-01-21
Thanks for the response Queue29,

I know I definitely ran 'sudo chmod 777 /usr/bin' and not /usr/bin/*
because it's in my bash history. But still when i try to run anything with sudo i get:

bash: /usr/bin/sudo: Permission denied

Here's a snippet of what it looks like
$ ls -l /usr/bin
-????????? ? ? ? ?                ? strace
-????????? ? ? ? ?                ? strings
-????????? ? ? ? ?                ? strip
-????????? ? ? ? ?                ? sudo
-????????? ? ? ? ?                ? sudoedit
-????????? ? ? ? ?                ? sum
-????????? ? ? ? ?                ? svn
-????????? ? ? ? ?                ? svnadmin


So does that mean my system is hosed?

---

### Post by Queue29 on 2011-01-21
Hrmm.. 777 is supposed to allow all permissions to everybody, so it's odd to see it restricting access. Show me the output of:

```
ls -lha /usr/
```

I'm wondering what the permissions are actually set as on /usr/bin. 

Also, show me

```
ls -lha /usr/bin/sudo
```

If all else fails you might be able to boot to the live cd and change the permissions from there.

---

### Post by MiKOTRON on 2011-01-21
Hi there.  This thread might be some help to you.

[http://ubuntuforums.org/showthread.php?t=958376](http://ubuntuforums.org/showthread.php?t=958376)

---

### Post by 3Miro on 2011-01-21
Get a live CD and boot into it (try Ubuntu and not install Ubuntu). On the CD, use:

```
ls -al /usr
```

to see what the correct permissions on /usr/bin should be. Then you can mount your Ubuntu partition (click on it from Places and then it will appear in /media/something and you should be able to sudo chmod the /media/something/usr/bin folder to whatever it needs to be.

Always keep a live CD handy, it can fix almost everything.

---

### Post by bigspoon on 2011-01-21
Here's the info you wanted Queue29



gcorradini@twinkie:~/$ ls -1ha /usr/
.
..
bin
games
include
lib
lib32
lib64
local
sbin
share
src
gcorradini@twinkie:~/$ ls -1ha /usr/bin/sudo
ls: cannot access /usr/bin/sudo: Permission denied

---

### Post by psusi on 2011-01-21
> **bigspoon said:**
> 
Here's a snippet of what it looks like
$ ls -l /usr/bin
-????????? ? ? ? ?                ? strace
-????????? ? ? ? ?                ? strings
-????????? ? ? ? ?                ? strip
-????????? ? ? ? ?                ? sudo
-????????? ? ? ? ?                ? sudoedit
-????????? ? ? ? ?                ? sum
-????????? ? ? ? ?                ? svn
-????????? ? ? ? ?                ? svnadmin


So does that mean my system is hosed?

That is indeed pretty hosed.  That looks like a corrupt filesystem though, not having anything to do with your chmod.  You should fsck the filesystem.

---

### Post by ajgreeny on 2011-01-21
> I'm new to ubuntu but amazed that sudo would let me change permissions on itself to the point where it would be useless.Unfortunately for you, sudo lets you do almost anything to your system, including deleting the whole system, if that's what you tell it to do.

It sounds as if the executable sudo now has the wrong permissions and it may therefore be difficult to put right, but perhaps the live CD can come to your rescue.

If you boot to that you may be able to reset the permissions of either the whole of the installed /usr/bin, or perhaps just the /usr/bin/sudo for the time being. The permissions I see using ls -l are:-
```
-rwsr-xr-x 2 root root 127668 2011-01-19 18:01 /usr/bin/sudo
```
and I am not sure about the start of this with the -rw[COLOR=Red]s[/COLOR]r; it's normally -rw[COLOR=Red]x[/COLOR]r for an executable, IE  chmod 755

[COLOR=Red]I AM NOT AT ALL SURE ABOUT THIS, HOWEVER, SO WAIT FOR MORE ANSWERS BEFORE TRYING IT.

[COLOR=Black]EDIT:
I'm much too slow, but others seem to think that the live CD may help as well.  You can use the live CD for the fsck with sudo e2fsck /dev/sdx# where sdx# is your ubuntu root partition.
[/COLOR][/COLOR]

---

### Post by geirha on 2011-01-21
All those ??? suggests the filesystem is corrupt, you'll need to do an fsck on it.  Boot with a liveCD to do that.  You may be able to get the permission of those files back to normal (by help of the liveCD), but it will be time consuming and hard.

I recommend you back up all your important files and reinstall.

Also, chmod 777 is never a solution.

---

### Post by KeyserSoze93 on 2011-01-21
> **bigspoon said:**
> Here's the info you wanted Queue29



gcorradini@twinkie:~/$ ls -1ha /usr/
.
..
bin
games
include
lib
lib32
lib64
local
sbin
share
src
gcorradini@twinkie:~/$ ls -1ha /usr/bin/sudo
ls: cannot access /usr/bin/sudo: Permission denied

It's "ls -lha /usr/", not "ls -1ha /usr/"

l, as in lowercase L, displays a long listing including the relevant permission information. 1, as in one, simply display the short information in one column.

---

### Post by HermanAB on 2011-01-21
Another way to fix it, is to install the same version of Linux on another machine (or VM) and then copy /usr over to the old machine.

---

### Post by bigspoon on 2011-01-21
Thanks for all the great responses. Most importantly, I'm learning new stuff about linux and that's the real payoff :)

Ok, I loaded the 10.10 disk and started the Ubuntu Trial (booting from CD). I mounted what seemed to be my partition by going to Places > and clicking on 438 GB Filesystem. It then mounts this on desktop with the following DIR location at /media/e934dff934939-349-aabld-349343 or something which from hereafter I will refer to as <mypartition>. There  were my files, so it seemed to be it. And I saw my screwed up /usr/bin permissions. Let's have at it! Grrrr goes the meerkat pup!

The difference between ls -l /usr from CD and ls -l <mypartition> is that all folders except
/usr/src and any link such as /usr/lib64 have 755 permissions or more explicitly drwxr-xr-x. /usr/src has drwxrwsr-x. And the links have 777 permissions.

I made the appropriate changes, unmounted my partition, sudo reboot, removed install disk, logged in, opened terminal screen and...and...and

$ sudo -u postgres -i -H 

IT FREAKIN WORKED!!! You guys are great. I will remember this trick forevs.

Although I still have that persnickety postgresql error :(

---

### Post by bigspoon on 2011-01-21
marked solved

---

### Post by ajgreeny on 2011-01-21
Congratulations!!

---

### Post by MiKOTRON on 2011-01-22
Awesome! =D>

---

