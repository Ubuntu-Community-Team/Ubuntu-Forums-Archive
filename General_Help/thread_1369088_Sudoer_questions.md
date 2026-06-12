---
title: "Sudoer questions"
date: 2009-12-31
forum: General Help
---

### Post by kcorbin on 2009-12-31
Hey guys/gals

i want to restrict certain jr admins from running some commands or from having access to certian files on the servers.... so my initial thought was to edit the sudoers file with cmnd_lists but i'm not sure if this is the best way to accomplish this goal or not.... 

Or am i better off to create a group (jradmin) and then assign rights to the group?? 

the goal is to have two jr admins that have the ability to create new users/email accounts etc... so they would have to vi an aliases file and run postfix on mail server.  i don't want the jradmin group to be able to halt or reboot the servers or alter anything else outside of the few tasks they are given.....   

So any thought or help on the best solution to accomplish this task would be great..

Thanks 
KC

---

### Post by Brandon Williams on 2009-12-31
It sounds like you're already on the right track. The best thing for you to do is create a user alias to represent the list of jr admins, and then list the specific commands and files you want the jr admins to have access to. It sounds like this is already what you plan to do.

---

### Post by kcorbin on 2010-01-04
Thanks,

This is the track that i want to follow, I guess my next question is do i put the cmnd_list in the jradmins group list? or does it stay in the sudoers file?

---

### Post by Brandon Williams on 2010-01-04
The list of commands you want them to be able to run will go in the sudoers file.

---

