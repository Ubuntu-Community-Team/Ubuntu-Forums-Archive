---
title: "Grsync"
date: 2011-10-06
forum: General Help
---

### Post by Guitar John on 2011-10-06
I'm sure the solution to this is simple, but it escapes me nonetheless.

I am trying to sync my Music folder on my computer with a Music folder on a remote HDD, telling it to only add new files.  I am using the default, which has the following boxes checked.

In the Basics tab:
Source and Destination

/home/mycomputer/Music
/media/remoteHDD/Music

Preserve Time
Verbose
Ignore existing
Skip newer
Show transfer process


In the Advanced tab:
Protect remote args

What I want is the existing files on the remote drive left alone, and the newer one from the computer added.  What I wind up with is a folder called "Music" within the folder Music on my remote HDD that is a copy of my Music folder from the computer.

Any ideas?
Thanks in advance.

---

### Post by jazzon on 2011-10-06
> **Guitar John said:**
> I'm sure the solution to this is simple, but it escapes me nonetheless.

I am trying to sync my Music folder on my computer with a Music folder on a remote HDD, telling it to only add new files.  I am using the default, which has the following boxes checked.

In the Basics tab:
Source and Destination

/home/mycomputer/Music
/media/remoteHDD/Music

Preserve Time
Verbose
Ignore existing
Skip newer
Show transfer process


In the Advanced tab:
Protect remote args

What I want is the existing files on the remote drive left alone, and the newer one from the computer added.  What I wind up with is a folder called "Music" within the folder Music on my remote HDD that is a copy of my Music folder from the computer.

Any ideas?
Thanks in advance.


1.) back up your music device before you try this.
2.) Change destination to
```
/media/remoteHDD/
```
3.) give it a go (try it with and without the trailing / character on destination.

---

### Post by ajgreeny on 2011-10-06
Also note that with rsync and grsync the source and destination folders need the trailing /, so should be 
```
/home/mycomputer/Music/
/media/remoteHDD/Music/
```

---

### Post by Guitar John on 2011-10-07
It was indeed the missing trailing/ that was causing the problem.  Thanks to both for your replies.

Marked SOLVED.

---

