---
title: "Managing Users"
date: 2010-06-23
forum: General Help
---

### Post by Jonny87 on 2010-06-23
I'm trying to set up Ubuntu 10:04 for a family I know.
The plan is to set up a separate user for the mother and each of the kids.
I want to have the mother as the first user so she can do some basic admin stuff. And the Kids as very limited users, preferably  not even having internet access type thing. I even thought about having another desktop user profile for the internet that the mother would keep a password for, that way they can't access the net with out the mothers permission.

Is there a simple way that I can block the kids profiles from accessing the internet or at least have it prompt for the mothers password?

Also is there a way that I can block the kids access to the "edit menus" so that I can remove certain things that they don' need access to, with out them being able to add it again?

I've looked under System -> Administrator -> Users & Groups -> Advanced Settings -> User Privileges (tab), but there doesn't appear to be enough control/options. Is the another way that offers more advanced options and flexibility?

---

### Post by Jonny87 on 2010-06-24
Does no one know of a more advanced way to manage users with exactly what they can and can't do?

There must be a way, if not then Ubuntu is lacking on this side of things.

---

### Post by Jonny87 on 2010-06-24
Thanks, have been looking online but haven't found much more than what I already know about. That's why I was hoping someone would be able to point me in the right direction.
And I'm quite happy using the command line if I know what commands to use as I'm still learning them as I go. I don't have the advantage of having used Linux for years.

---

### Post by ba_saish on 2010-06-25
I assume you are using system->adminstration->user and groups to add the users. 
In the same screen you will see  privileges tab, you can use that to set some restrictions. 

Then to restrict the access of individual files and folder please check out one of the basic command "chmod". 

Hope this helps.

---

### Post by Jonny87 on 2010-06-27
> **ba_saish said:**
> I assume you are using system->adminstration->user and groups to add the users. 
Yes, as stated in my original post I have tried that, but I'm looking for something more advanced.

> Then to restrict the access of individual files and folder please check out one of the basic command "chmod". 

Hope this helps.
It's not so much the individual files (I have that sorted) but to prevent them from running particular applications etc.

---

### Post by WorMzy on 2010-06-27
I'm not sure if this will cause problems, but you could chown the applications that you don't want the kids to use so that the group is a group that your wife is a member of, but not your kids; then chmod the applications so that only the owner and group can execute them.

For example, the default permissions on /usr/bin/chromium (the file that launches the chromium web browser) are:

```
-rwxr-xr-x 1 root root
```

You'd make it so that it was thus:

```
-rwxr-x--- 1 root wifesgroup
```

Which would mean that root and anyone in wife's group could see and execute it, but everyone else wouldn't be able to.

That can be accomplished by running
```
sudo chown :wifesgroup /etc/bin/chromium
```
```
sudo chmod o-rx /etc/bin/chromium
```

---

### Post by Jonny87 on 2010-06-27
>  	 		**Re: Managing Users**
 I'm not sure if this will cause problems, but you could chown the applications that you don't want the kids to use so that the group is a group that your wife is a member of, but not your kids; then chmod the applications so that only the owner and group can execute them.

For example, the default permissions on /usr/bin/chromium (the file that launches the chromium web browser) are:

 	Code:
 	-rwxr-xr-x 1 root root 
You'd make it so that it was thus:

 	Code:
 	-rwxr-x--- 1 root wifesgroup 
Which would mean that root and anyone in wife's group could see and execute it, but everyone else wouldn't be able to.

That can be accomplished by running
 	Code:
 	sudo chown :wifesgroup /etc/bin/chromium 
 	Code:
 	sudo chmod o-rx /etc/bin/chromium 

Thanks, that may work.

Just out of curiosity though is it possible to apply permission to more than one group?

For example, if I want a sudo user (first Ubuntu user) to have permission to chromium as well as one non sudo user (any other Ubuntu use except the first), but wanted to keep the their individual groups. While blocking all other users.

---

### Post by WorMzy on 2010-06-27
No, only one group can own a file, but you can just create a new group with the users you want to be able to access it. They won't leave their original groups.

---

### Post by Jonny87 on 2010-06-27
True, I didn't think of that. I'll keep that in mind. Thanks for your help.

---

### Post by gadolinio on 2010-06-28
> **WorMzy said:**
> No, only one group can own a file, but you can just create a new group with the users you want to be able to access it. They won't leave their original groups.
That would be a good idea. Create a group like "appusers", and add users allowed to use it to that group.
Now I wonder whether root and/or somebody else should be in the group as well, for the application to work correctly...

---

