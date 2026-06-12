---
title: "Users &amp; Groups: Unlock not working + banned from accessing"
date: 2009-12-16
forum: General Help
---

### Post by astrobob.tk on 2009-12-16
Hey guys,

I have been using Ubuntu for some time now. Yesterday I was checking the Users & Groups & did some editing. I added a root user (which I don't quite understand why it was missing since during installation i remember i assigned one). I also added a new regular user & put each user to his own group (i.e.; "astrobob" to "astrobob group" & "root" to "root group"). Besides i edited some permission to the regular users & unchecked the giving access to change system what otherwise it is called.

After doing that, when trying to unlock the users & groups to do further editing, I wasn't promoted to enter a root pasword. The application seems to take quite some time (~ 2 or 3 minutes) after which it gave an error stating that it couldn't unlock.

Today when trying to access the application i was given the following error:

"You are not allowed to access the system configuration."

Could you please help me in this ? or directing me to the appropriate thread ?

One other thing. How does the root user log in ? I tried this when promoted to login but it said root users login from another place.

Thank you in advance

Sincerely Yours,
BOB

---

### Post by doas777 on 2009-12-16
1) it was not a great idea to add a root user. the user is already there, but disabled.
2) is astrobob the user you are trying to use to unlock, and are they members of the adm and admin groups?

---

### Post by earthpigg on 2009-12-16
hi,

give this a shot, maybe?

```
sudo su
users-admin
```

(watch out when using sudo su. it opens a root terminal, meaning a single typo could fry your machine and whatnot.)

to login as root:
```
sudo login root
```

again, logging in as root is normally not how the ubuntu security model does things. use at own risk.

---

### Post by astrobob.tk on 2009-12-16
> **doas777 said:**
> 1) it was not a great idea to add a root user. the user is already there, but disabled.
2) is astrobob the user you are trying to use to unlock, and are they members of the adm and admin groups?

well yeh, my main user is astrobob. I used to administer the system from this user. 
if the root already existed why wasn't it in the users and groups list ? there was only astrobob.

i just tried the following by logging in as root (su -) with no success. The situation is still the same.

```
sudo adduser astrobob admin
```

what should I do to get back to where i was before doing this stupid action ?

---

### Post by doas777 on 2009-12-16
your best bet is probably recovery mode. reboot and when you get to grub, select a recovery mode option. it  will automatically log you in as the real root, and your command shoudl succede without sudo. make sure to add your self to adm as well.

no worries about playin around.  I prolly shouldn't have said anything. experimentation is key to learning.

---

### Post by astrobob.tk on 2009-12-16
well thx. that worked :D

so basically what did make it work ? was it the command i used?

one last thing. could you please direct me to an appropriate thread about users & groups, especially groups & how they affect users? 

thank you

---

### Post by doas777 on 2009-12-16
first off, there are some things about your original situation that i kinda don't understand, so bear with me. for instance, when i open the usergroup tool, I see the root account greyed out, and it becomes accessible when i hit unlock. I have no idea why you had no root user listed. in ubuntu there is a root account (most of the system runs under it, and you did as well, when you were in recovery mode), but it;s login is disabled by default. 

an administrative user in ubuntu runs as a normal user most of the time, but has the ability to use tools like sudo gksu and su to switch the users privileges to that of the root user. It is my understanding that to use sudo, you either need to be a member of the admin and adm groups, or of the sudoers group (not entirely certian what the sudo group is for, since my users are not in it, but can sudo). the command you ran added your user to the admin group.

here is some info on managing users and groups. 
[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)
[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)
[http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)

---

### Post by astrobob.tk on 2009-12-17
> first off, there are some things about your original situation that i kinda don't understand, so bear with me. for instance, when i open the usergroup tool, I see the root account greyed out, and it becomes accessible when i hit unlock. I have no idea why you had no root user listed. in ubuntu there is a root account (most of the system runs under it, and you did as well, when you were in recovery mode), but it;s login is disabled by default.well before adding this new user & the root user, there was only 1 user which wasn't locked. this was the astrobob user (if i am not mistaken the home directory was set as it is now: /home/astrobob). for this reason i added the root user (which is now set as /root & is greyed as u describe). But still when i need to unlock the users & groups, i am asked for the astrobob pass & not the root pass. Is that how it should be? 
Well when i installed Ubuntu i was asked for a root password but never been accepted. I was using the astrobob user pass instead which was working. Now I am still using the astrobob pass to administer the system but there are things that require the root pass like in some cases in the terminal. so i think this fixed it. I am as well not sure how this happened.

by the way here is how the users are grouped:

1. root group: root
2. users group: BOB (which stands for astrobob i suppose) & the other account
3. fuse: all 3 users
4. lpadmin: root
5. netdev: all 3 users
6. admin: BOB & root
7. astrobob: BOB
8. sambashare: root
9. other account group: other account user

as for other groups the users are all unchecked in them. Should the "root" user be in the "users" group ?

& thx for the links :D

---

### Post by doas777 on 2009-12-17
ahh, I think I understand the quandry.

when a user with adm/admin group membership runs gksu, it prompts for Their password, not roots. the point is primarily to get you to declare explicitly that you want the command run, and that you understand that it will run with admin privs. it is also helpful if you don't lock your terminal or use the remote desktop server (vino), as it does not authenticate by default.

the root password is set to a random string, and login for that account is disabled. as such root effectively has no password by default. you just can't log in whatever you try. in fact it is against the forum rules to post info on how to enable the root account. ubuntu really really doesn't want you to use it.

no, root should not go in users, typically. it prolly won't hurt anything if it does though. I add users to the users group primarilly for fileshare access. 

this may help answer some of your questions about the elevation process and root emulation:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

