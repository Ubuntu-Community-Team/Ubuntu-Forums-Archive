---
title: "Changed privliges on the whole filesystem"
date: 2006-03-23
forum: General Help
---

### Post by fionntan on 2006-03-23
First off I realise the stupidty of this, but my Linux knowledge isn't huge.

Yesterday I was trying to change the ownership on all files in the current folder from only root reading and writing, to all users reading and writing. So I typed the command

sudo chmod 660 /*

I know now I glanced at the wrong number on a webpage and didn't include the "." before /*, which is what I meant to do even though it's probably not the right syntax. Thus changing permission on EVERY file on my Linux OS.

now I'm completely locked out of Linux. 
So I tried that 60 second command line log in but bash couldn't run, giving

permission denied on /bin/bash

So what exactly should do I do?
Any help greatly appreciated.

---

### Post by Gustav on 2006-03-23
Use a live-CD and mount the harddiscs and change permissions (It will take some work figuring out the apropriate permissions :()

---

### Post by Prospero2006 on 2006-03-23
I did that once on a Slackware box. Except, I did it intentionally. 
I figured it was a single user system, so why not just chmod -R 777 /
or something like that. Big mistake. 

My suggestion is completely reinstall the O/S and learn from the mistake. 
Use a live c.d. to back up anything important.

Pros

---

### Post by fionntan on 2006-03-23
I was really hoping I wouldn't have to re-install.

Fortunately I've got Windows installed on a different partition and can access all my Linux files from it.

Pretty annoying the way one number can mess up your entire system.

---

### Post by Prospero2006 on 2006-03-23
Never let a reinstall scare you. It only takes like 3-4 hours to completely set everything up correctly. If things get too bad for whatever reason, sometimes the simplest solution is to lay the whole thing down from scratch. 

My home network is designed with this in mind really. 
 -I use rsync to backup all of my important data every night to an independent 160 gig hard drive. All of my configuration files and what not are in a special folder, like xorg.conf, /etc/apt/kdmrc, firefox plugins, etc.
-I also make a point of documenting what I did to make complicated or confusing configurations work. (Firefox 1.5 with full support stands out as one of those endeavors.) 
 
-That way, in the event I do feel a reinstall is the best way to either test for a problem or outright fix it, it's a no brainer. I've got everything in place.
I'll format that sucker right now. 

-Something to think about I guess.
    Pros

---

### Post by engla on 2006-03-23
No seriously, it would be nice to have a script that would restore permissions, so that if you mess anything up (**small** and large), then it's fixable.

---

### Post by mooseman089 on 2006-04-03
I'm sorry to bring this semi old bad thread alive buts its the same problem as me so I didn't see a need to make a new thread. I did the same thing only I did chmod -R 777 / and now im borked and the worse thing is the computer is a backup server (1tb) so all my important files are on there and there isn't room on any of the other drives to move files if I were to jump on a live cd though I could use one to manually fix permissions so I was wondering if there is a script out there anywhere that I could use to restore permissions because going through each file would be a total pain and a total reinstall is almost out of the question because I can't lose those files. Any help would be super great appreciated

---

### Post by incubus on 2006-04-04
It's hard to imagine a script that would fix permissions, because different files have not only different permissions, but also different owners/groups. The script would be gigantic and specific to a distribution.

Since the permissions are set when you install packages, the following comes to mind. What about booting a Live CD, getting internet working, and:

$ sudo chroot <target partition>
# apt-get install --reinstall <list of all packages>
(note that after chroot, you're root)

This is really a blind guess. If that doesn't work, I would think of deboostraping a new system, while of course being careful to protect the data. Considering we're talking about a server, I would first try this in a virtual machine. If you can't, tell me and I'll try it here.

incubus

---

### Post by Barrakketh on 2006-04-04
I'm trying to figure out how come he couldn't access any of his files, as 777 grants Read/Write/Execute for all users (read is four bits, write is two, execute is one = 7).
Using apt to re-install all of your packages...it should go something like this once you've chrooted:

```
dpkg -l '*' | grep '^ii' | awk '{print $2}' | xargs apt-get -y --reinstall install 
```
Don't forget to run apt-get update first ;)

---

### Post by Al3xanR0 on 2006-04-04
[QUOTE=Prospero2006]My suggestion is completely reinstall the O/S and learn from the mistake. 
[/QUOTE] 

It is probably fair to say that it is unlikely that this mistake will be made again (*,)

---

### Post by mooseman089 on 2006-04-04
barrakketh: I think there is a problem because when I set everything to 777 anything that had weird permissons like sticky, setuid, setgid got screwdup.  But is there any ideas on why the internet doesnt work because if i can back on my lan with samba I can attempt to backup some files of higher pritority in the remote case that I lose stuff which I'm giong to try not to.

---

### Post by mooseman089 on 2006-04-07
I was wondering if anybody could do some ls -l dumps so I can see the normal permissions of a file like I did 4755 on su and now in the gui i can be su but i still need networking

---

### Post by mooseman089 on 2006-04-08
bump I would like to solve this sometime this weekend. Does anybody know any particular files that have special permissons like setuid, setgid, and/or sticky

---

