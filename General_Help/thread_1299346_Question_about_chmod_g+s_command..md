---
title: "Question about chmod g+s command."
date: 2009-10-23
forum: General Help
---

### Post by Roasted on 2009-10-23
I was browsing google trying to find some information about the chmod g+s command, which evidently is a command to make all files/folders created within a directory to automatically take on the group ownership of the parent folder.

I saw this:

```

Assuming your disk is mounted on /media/disk:
sudo chgrp users /media/disk
sudo chmod g+w /media/disk
sudo chmod g+s /media/disk
should do the trick. I tried it here and it worked a treat.
```

Okay, so I know what g+s is. What is g+w? Are there other variants of that command? I was surprised at how little info I found on it, including in the man chmod page.

---

### Post by diesch on 2009-10-23
chmod g+w gives the group writer permissions. See the [manpage for chmod](http://manpages.ubuntu.com/manpages/jaunty/en/man1/chmod.1.html) for more about that.

---

### Post by Matt__ on 2009-10-23
g+w just adds write ability to group.

/edit pah....away a few secs to answer phone and someone else posts lol

---

### Post by mikewhatever on 2009-10-23
g+w adds write permission to the specified group.
Check out this chmod tutorial [http://catcode.com/teachmod/](http://catcode.com/teachmod/).

---

### Post by phillw on 2009-10-23
> Okay, so I know what g+s is. What is g+w? Are there other variants of that command? I was surprised at how little info I found on it, including in the man chmod page.

Just in case you not aware, the g+w would also allow anyone in group to delete stuff !!!

This should help a little to understand..

[http://www.washington.edu/computing/unix/permissions.html](http://www.washington.edu/computing/unix/permissions.html)

Regards,

Phill.

---

### Post by sisco311 on 2009-10-23
> **diesch said:**
> chmod g+w gives the group writer permissions. See the [manpage for chmod](http://manpages.ubuntu.com/manpages/jaunty/en/man1/chmod.1.html) for more about that.

> **Matt__ said:**
> g+w just adds write ability to group.

/edit pah....away a few secs to answer phone and someone else posts lol

yep, but the files created in the directory will not inherit the permissions.

---

### Post by Matt__ on 2009-10-23
would chgrp -r and chmod -r 0777 work on directory and all subsequent action within it?

---

### Post by Roasted on 2009-10-23
I'm confused...

g+w simply gives write permission to the group without touching the other 2 octal permissions - owner and all others. Right?

While g+s simply means the group stays intact for all files/folders created within the parent directory.

So all in all, g+w and g+s each do very different things.

Or am I way off?

---

### Post by sisco311 on 2009-10-23
> **Roasted said:**
> I'm confused...

g+w simply gives write permission to the group without touching the other 2 octal permissions - owner and all others. Right?

While g+s simply means the group stays intact for all files/folders created within the parent directory.

So all in all, g+w and g+s each do very different things.

Or am I way off?

u = user
g = group
o = others
+ = add
w = write (permission)
s = set sticky bit

g+w = set write permission for group
g+s = setgid (set sticky bit for group)
u+w = set write permission for user
...
[uhelp]community/FilePermissions[/uhelp]
[http://en.wikipedia.org/wiki/Setuid]("http://en.wikipedia.org/wiki/Setuid")

---

### Post by Roasted on 2009-10-23
> **sisco311 said:**
> u = user
g = group
o = others
+ = add
w = write (permission)
s = set sticky bit

g+w = set write permission for group
g+s = setgid (set sticky bit for group)
u+w = set write permission for user
...
[uhelp]community/FilePermissions[/uhelp]
[http://en.wikipedia.org/wiki/Setuid]("http://en.wikipedia.org/wiki/Setuid")

Hm, good deal. That explains it. Thanks everyone!

Just to clarify - this g+s option is only done through terminal, right? There's no GUI option for it? (just for the sake of learning)

EDIT:

What's up with this? Copied directly from the community link above.

```

 Options
Definition
u	
owner

g	
group

o
other

x
execute

w
write

r
read

+
add permission

-
remove permission

=	
set permission 
```

= is set permission? Isn't that supposed to be S?

---

### Post by Roasted on 2009-10-24
Also - is there such thing like this for owner where you can set the owner of all files that get dropped in a directory?

---

### Post by uncle-c on 2009-10-24
Just in case you are wondering


**$ chmod u+s * directory ***

does absolutely nothing ! You can only SUID a file.

---

### Post by Roasted on 2009-10-24
> **uncle-c said:**
> Just in case you are wondering


**$ chmod u+s * directory ***

does absolutely nothing ! You can only SUID a file.

And U is what... owner?

So you can only set a group and not the owner?

---

### Post by sisco311 on 2009-10-24
> **Roasted said:**
> 
Just to clarify - this g+s option is only done through terminal, right? There's no GUI option for it? (just for the sake of learning)


You can enable show advanced permissions in nautilus:
[list=i]
[*]press Alt+F2
[*]type gconf-editor and <Enter>
[*]from the left pane in the pop-up window, choose app -> nautilus -> preferences
[*]go to the right pane, find out the show_advanced_permissions, check the box on its right
[*]close the window, done.

[/list]

> **Roasted said:**
> 
= is set permission? Isn't that supposed to be S?

+ adds a permission for the user/group/others 
= sets the permission to

```
drwxr-xr-x  4 sisco users  348160 2009-10-22 19:35 xtmp


[sisco@acme ~]$ chmod g+w ./xtmp   #add write permission for the group
[sisco@acme ~]$ ls -l xtmp
drwxr**w**xr-x  4 sisco users  348160 2009-10-22 19:35 xtmp


[sisco@acme ~]$ chmod g=w ./xtmp   #+set the permission for group to w
[sisco@acme ~]$ ls -l xtmp
drwx-**w**-r-x  4 sisco users  348160 2009-10-22 19:35 xtmp
```

---

### Post by sisco311 on 2009-10-24
> **Roasted said:**
> And U is what... owner?

So you can only set a group and not the owner?

[http://en.wikipedia.org/wiki/Setuid]("http://en.wikipedia.org/wiki/Setuid")
[quote=wiki]
When a binary executable file has been given the setuid (**u+s *or* 4755**) attribute, normal users on the system who have permission to execute this file gain the privileges of the user who owns the file (commonly root) within the created process. When root privileges have been gained within the process, the application can then perform tasks on the system that regular users normally would be restricted from doing.[/quote]

For example the passwd command is setuid. The passwords are stored in the /etc/shadow file (in encrypted format). The file is owned by root:root and has -rw------- permissions (only root can write to the file). But you still can change your password (without root privileges) because the passwd command runs as root.

---

### Post by Roasted on 2009-10-25
Hmm... real good info here. Thanks guys.

...but I'm still trying to understand the equals thing.

sudo chmod g+s folder

okay, I got that. I know what that does.

But what is an example command of equals? 

sudo chmod g=s folder (??)

---

### Post by Roasted on 2009-10-26
One thing I can't seem to iron out, what's different from g+w versus octal rights having write permission?

I mean, if you have rwx/rw-/r-- permissions, group would have rw permissions. How's that different from issuing g+w?

---

