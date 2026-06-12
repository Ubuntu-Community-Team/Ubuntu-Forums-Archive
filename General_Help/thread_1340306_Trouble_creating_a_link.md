---
title: "Trouble creating a link"
date: 2009-11-28
forum: General Help
---

### Post by ian2112 on 2009-11-28
Hello,

I'd like to create a link (symbolic?) to a directory in one user's account (/home/user1/Pictures) and have it accessible as a link on the desktop of another user (/home/user2)

I've tried using both Nautilus (opened as root - gksudo nautilus), and I've tried the command line.

In both cases the link icon that gets created on User2's desktop is broken - the error message says the link doesn't exist.

I've set both users to belong to the same group (users) and made the 'Pictures' directory belong to the same group, and given the group rwx access to the folder.

Still... I suspect I've got some sort of permissions problem.

Any thoughts on things I can try?

Any help is appreciated.

Ian.

---

### Post by east2idaho on 2009-11-28
from the command line, you would do this as:

cd /home/user2/Desktop
ln -s /home/user1/Pictures user1Pictures

If you have the permissions correct, the things that you could be doing wrong are reversing the arguments for the ln command or misspelling something in the path to your target directory (tab completion is your friend here).

---

### Post by ian2112 on 2009-11-28
> **east2idaho said:**
> from the command line, you would do this as:

cd /home/user2/Desktop
ln -s /home/user1/Pictures user1Pictures



I tried the command as quoted (I needed to use sudo).  It created the link on the user2's desktop... but same result.  Double-clicking the link icon returns a message saying the link is broken (and the icon has an 'x' on the corner).

What permissions should I have applied to the Pictures folder (and assuming all the files and subdirectories in the folder)?  Any thoughts?

I appreciate the help!

Ian.

---

### Post by SuperSonic4 on 2009-11-28
It could be that user2 cannot read user1's files. I would suggest a chown

```
sudo chown -R :optical /home/user1/Pictures
```

(the group doesn't matter so long as both members are in it)


-----------------------------------------------------------

Another solution would be to make use of a data partition which both users could read and write to.

---

### Post by fluffman86 on 2009-11-28
It sounds like you've done everything right, but is the other accound encrypted?  It won't work if you selected encryption during the install process for the first user.

---

### Post by ian2112 on 2009-11-28
> **fluffman86 said:**
> It sounds like you've done everything right, but is the other accound encrypted?  It won't work if you selected encryption during the install process for the first user.

Interesting possibility - I don't recall if I selected encryption.  Is there a way to confirm?

Also - I tried the chown command (thanks!) and still have the same issue.  Weird.

I'm pretty convinced I'm making a newbie mistake... but frustrating.  Just to rule out permissions I did a chmod -R 777 on /Pictures directory.  I confirmed that everything is read, write, execute for owner, group and other. It's got me baffled.

Per the earlier suggestion.  How can I create a common partition that both users can access?  Is this relatively easy and harmless (i.e., newbie-proofish).

Thanks!!!
Ian.

---

