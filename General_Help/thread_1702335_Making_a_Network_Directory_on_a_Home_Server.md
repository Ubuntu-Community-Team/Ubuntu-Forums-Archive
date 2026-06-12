---
title: "Making a Network Directory on a Home Server"
date: 2011-03-07
forum: General Help
---

### Post by ncwalker2010 on 2011-03-07
I really have two questions, 1st - Is what I am trying to do the most effective way to do this?

2nd - Why won't it work?

------------------------------

I have Ubuntu running as my home computer and it is acting as a server.  So myself (as admin) and the rest of the family each have a logon onto this home server.  Several of us have Windows boxes that I want to be able to access they home server box.

I want a directory that only I can write to on the Linux box (for family pictures and stuff, so the kids don't inadvertently save the mustaches they draw on me :-) ).  I want a directory that anyone on the Linux box can read/write too, but ONLY on that box.  (For helping with homework, family common projects, etc.)  And I want a directory that anyone on my wireless network can write to, so if someone wants to place files onto the Linux box from a Windows laptop they can.

Here is what I have done.  
1) I made a group called "kitchenusers" (the computer is in the kitchen) that has as members all the logons onto the Linux box and everyone is a member of that group.
2) I want out into /home and made a directory called /homeserver at the same directory level as all the user accounts
3) In /homeserver I made 3 directories

/homeserver/LocalRO = the one only I can write in, but everyone (even the wireless logons) can read

/homeserver/Local = everyone reads, only people logged on to the Linux box can write to

/homeserver/NetFree = free access by everyone.

I used chown to set me as the owner and kitchenusers on all three directories.

I used chmod to set the permissions in this format:

chmod -R xxx dirname

LocalRO was 755
Local was 775
NetFree was 777

And when I do the "ls -l" I get what I expect.

Then I went into Samba and shared them.  I shared "/homeserver" as read-only via samba and I shared "/homeserver/NetFree" as writable by anyone.

All good.  All works as I expected.  People can read from anywhere, but only write as how I have outlined this.

So... Question 1:  Was that an effective way to do this?  I mean, best use of Linux?

Question 2:  It is not inheriting privileges.  Meaning if someone creates a file in the "/homeserver/Local" directory, the intent is that someone else can modify it.  I am finding that is not happening.  If my son creates a file in there and I look at it with ls -l it shows up with his name as user and group, so the other son (or myself or whoever for that matter) can read it, but nobody can edit it or delete it.

So when son1 puts a file out there, he has to change the group in nautilus.  I also have an administrator script that just forces compliance using chmod with the -R modifier.

What I don't understand is if I set up the directory with this scheme, why are the files being created in there NOT following the ownership scheme?

---

### Post by mikewhatever on 2011-03-07
...

---

### Post by mikewhatever on 2011-03-07
Creating a local shared folder is somewhat more complex then simply chmod`ing and chow`ing the existing directories. (check the link).
[http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html](http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html)

Also, file creation is not governed by the permissions of the parent folder, but rather by creation mask. The default is 022, which translates to 755 newly created file permissions.

---

### Post by ncwalker2010 on 2011-03-07
Many thanks, Mike.  The link was very helpful and very well written. So I am understanding what is going on now.

I am a little skittish about enabling ACL - and I doubt I have a good reason for it, other than my lack of understanding.

In any case, there remains one issue with the solution.... and that is if users have created the file in another directory, then drag and drop into this one, or copy it from the terminal,  it retains the permissions if the directory (ACL) setup.

I am thinking a script in the root of my netuser.  Then the kids can just run that when they need (knowing that it will only change the files they own).  That's OK.

---

