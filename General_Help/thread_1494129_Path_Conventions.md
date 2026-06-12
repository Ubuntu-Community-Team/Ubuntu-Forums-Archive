---
title: "Path Conventions"
date: 2010-05-26
forum: General Help
---

### Post by Cool Javelin on 2010-05-26
Is there a convention for which executables go into which directories?

Hello ubuntoriens:

Could someone please help me understand the logic behind some of these names. I know from the computers point of view it doesn't matter, but this is for my own obsessive compulsive sanity. :rolleyes:

My $PATH looks like /usr/local/sbin:/usr/local/bin:/usr/sbin:usr/bin:/sbin:/bin:/usr/games

I assume the sbins are for text script executables, and the bins are for binary compiled programs.

What's up with the /usr vs. /usr/local versions? Does one point to a different place depending on the currently logged on user?

Are the just plain /sbin and /bin for the global Linux stuff like ls, chmod, and whereis?.

If I add a program like heyu, and I want everybody to be able to use it, would it be better to place it in /usr/bin, or usr/local/bin?

If I add a program that only I want access to, like CheckPrinting, do I have to make my own directory in my own folder under /home/mark/bin to keep it private. or can I place it in one of the global paths and use chmod to remove read, write, and execute privileges to all but the owner. If the latter, will others be able to see it but not run it?

Phew, I guess I hold it all in till I just explode.

Thanks for your help,
Mark.

---

