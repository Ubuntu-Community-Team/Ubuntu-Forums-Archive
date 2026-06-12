---
title: "deleted the main username, urgent help needed."
date: 2009-08-11
forum: General Help
---

### Post by breephd on 2009-08-11
hi. i am an idiot.  i had to go and screw around.  now all my hard work is going down the tubes.
 
i went in to users and groups. and i deleted the main user.  now, i can log in with another username, but it won't allow me to select "users and groups".  
 
i can get to terminal from the other username.
 
can someone please help me?  or should i just do a completely new reinstall of 9.04?

---

### Post by ZizzerZuz on 2009-08-11
Can you login as root?

What do you mean by "main usrname"?

---

### Post by zkriesse on 2009-08-11
i don't see why you can't get into the username list....

---

### Post by jerrrys on 2009-08-11
when you delete a user account it not really deleted, it is disabled and can be restored with files intact.  I myself have not done this and find it amazing that the main user can be disabled.  since you can get to terminal, try this:

sudo usermod -a -G admin <username>
username being the current user that your in.  in theory this will allow you to give this user sudo access and then be able to reinstate yourself (main user).

and i say again, this is untried by me, just looks like it may work.

---

### Post by jocko on 2009-08-11
You mean you deleted the only user with the right to use sudo?
Boot up into recovery mode and add the user again.
1. Reboot. Hit Esc to see the grub menu if it's hidden. Select the second option (ends with "recovery mode" or "single user mode")
2. When it's fully booted, you'll get a simple blue menu where you can choose what to do next. One of the options (don't remember the exact text) will give you a command line logged in as root.
3. Add the user to your system, give the user a password and add the user to the admin group (to be able to use sudo), and some other groups that the user should be a member of:
```
adduser [COLOR=Blue]username[/COLOR]
passwd [COLOR=Blue]username[/COLOR]
addgroup [COLOR=Blue]username[/COLOR] admin
addgroup [COLOR=Blue]username[/COLOR] adm
addgroup [COLOR=Blue]username[/COLOR] dialout
addgroup [COLOR=Blue]username[/COLOR] cdrom
addgroup [COLOR=Blue]username[/COLOR] video
addgroup [COLOR=Blue]username[/COLOR] plugdev
addgroup [COLOR=Blue]username[/COLOR] lpadmin
addgroup [COLOR=Blue]username[/COLOR] netdev
addgroup [COLOR=Blue]username[/COLOR] sambashare
addgroup [COLOR=Blue]username[/COLOR] audio
addgroup [COLOR=Blue]username[/COLOR] pulse
addgroup [COLOR=Blue]username[/COLOR] pulse-access
```Of course you should change [COLOR=Blue]username[/COLOR] to the real username. You'll probably get a message that the user is already part of some of those groups, but run all commands just to be sure.

---

### Post by jocko on 2009-08-11
> **jerrrys said:**
> when you delete a user account it not really deleted, it is disabled and can be restored with files intact.  I myself have not done this and find it amazing that the main user can be disabled.  since you can get to terminal, try this:

sudo usermod -a -G admin <username>
username being the current user that your in.  in theory this will allow you to give this user sudo access and then be able to reinstate yourself (main user).

and i say again, this is untried by me, just looks like it may work.
That won't work. If he has deleted the only user that has the right to use sudo, there is no way he can use sudo to restore his account. Recovery mode is the only option.

---

### Post by jerrrys on 2009-08-11
glad you came alone jocko, was thinking his password still may work.  still amazed that main user can be wiped...

---

### Post by Barafu Albino Cheetah on 2009-08-11
He is not the main user. The main user is root. In ubuntu, the root user gets random password, and your user gets right to use sudo.   
You my change root password to be able to log in in case of such emergencies.

---

### Post by jerrrys on 2009-08-11
and they say that old dogs can't learn new tricks  :)

---

### Post by breephd on 2009-08-11
thanks i will try what you suggest.  at start up, ubuntu asks me if i wish to use "root" as the log in. and if i say "yes" then the screen goes blank.
 
the toruble is this.  at first i went in to the user name on teh first user, and i changed the file structure instead of saying "jane" which was the name of the ssytem, i said to put that person in the admin group.  instead of the jane group.  then, once it was there, i deleted it.  
 
so i messed up on two fronts.  i changed it, then deleted it.  ubuntu clearly doesn't liek what i did, b/c i see a bunch of code b4 ubunut loads on reboot.  
 
i hope these methods will work.

---

### Post by breephd on 2009-08-11
okay. i am sorry for the confusion.  i am not sure what to do.  
 
i can log in under other names.  when i want to do something that requires admin authorization, ubuntu still allows me to select the user i deleted and use that password.
 
so, it seems that that user is somehow there, but ubuntu will not allow me to log in using that username and password from when the ubuntu loads.
 
so, i am able to log in.  and if i need admin authorization, i can type in my previous main user password.  it is very odd.  and something seems wrong.  but i am able to follow this somewhat silly process to use my computer.
 
does anyoen know how can i see all of the user names?  i think i can get to terminal, but not sure if i can use sudo.

---

### Post by breephd on 2009-08-11
how do i change the password of root?
 
i think i really screwed up.  if no one has nay ideas, i may just have to install from the beginning.

---

### Post by Barafu Albino Cheetah on 2009-08-11
reload
in grub, chooose recovery mode. 
you will be presented a menu. 
in it, choose to get access to console as root
there type 
```
adduser --home /home/jedi  jedi
gpasswd -a jedi admin
```
and you will be a jedi!
Be sure to add yourself to other groups you need.

---

### Post by breephd on 2009-08-11
trying now. the screen looked a little different, but wow i am hoping this works!
 
thank you. i got back in!  now i will retype the part i altered before.  i won't mess with it.  i don't mind if it is still there.  at this point i just want it to work...

---

