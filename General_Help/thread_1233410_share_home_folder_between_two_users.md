---
title: "share home folder between two users"
date: 2009-08-06
forum: General Help
---

### Post by ZeldaFan on 2009-08-06
Is there a way for a user on my system to use the same home folder as another user? In other words can two users use the same home folder?

---

### Post by michy99 on 2009-08-06
What would be the point? If you want them to be able to share data like pictures, music, documents, etc, you should set up a folder for those files and link to it from each users home folder.

---

### Post by whiteychs on 2009-08-06
You can specify the location of the home folder for the user upon creation.  Maybe you could set user bill's home folder to /home/bob?

Possibly a symlink if that doesn't work?

---

### Post by ZeldaFan on 2009-08-06
Yes I want to do that, so I'll try setting up the shortcuts. I also want to share thunderbird, firefox, and pidgin profiles such that I can change a setting on either user and experience the change with both users. Additionally, is it possible to share a virtualbox guest OS between two users?

---

### Post by ZeldaFan on 2009-08-06
Whitey, I tried that but some error occurred not allowing me to log in to the new user. So I had to revert back.

---

### Post by whiteychs on 2009-08-06
Put both users into the same group and chmod the home directory to give access to everyone in that group.


edit:
[http://www.cyberciti.biz/faq/linux-setup-shared-directory/](http://www.cyberciti.biz/faq/linux-setup-shared-directory/)
May have your solution.

---

### Post by michy99 on 2009-08-06
Will both users ever be logged on at the same time? If not, how about just having them share one user account.

---

### Post by Doctorzongo on 2009-08-06
Instead of sharing everything, why aren't you just creating one account?

"bobjill" instead of "bob" and "jill."

It would seem to be a lot less troublesome. But, if you insist, then delete your config files for Thunderbird, Pidgin, etc, for the second user and create a symlink to the first user's config files.

---

### Post by ppirilla on 2009-08-06
you pretty much cannot have two users share the same home folder.    Default security measures check to make sure that a user owns his own home folder before allowing logon, and two users cannot both own a file.  It is possible to disable this security measure, but I **very strongly** advise against trying.

If you want that much similarity between the two accounts, though, why do they need to be two separate accounts?

---

### Post by martinbaselier on 2009-08-06
This sounds like a bad idea. If two users use the same home folder, their settings will be identical for the most part. personalization: impossible. (you will both have the same desktop, same icons, same color scheme. So basically they will be the same user. 
You only create an extra problem with permissions. 

If you only want to share certain stuff like e-mail (this means you will both use the same e-mail account), you could just create symbolic links for one of the users. 

For example I have a pc with 5 different users and I want them all to share the same wine account. The main user is called 'opa'. 

So for each user I created a symlink:

ln -s /home/opa/.wine ~/.wine

You could theoretically do the same thing with the users home folder itself. After creating the user, delete the home folder and create a symbolic link to the other users folder. Then make the new user owner of the symlink. 

To change the owner of the symlink use chown -h 
example:

sudo ln -s /home/opa /home/test
sudo chown -h test:test test
I have a user called test in the group test. 

This will make both users almost identical. For each file that does not have read or write permissions for other users, either in the same group when you decide to put them both in the same group or for others outside the group, you will not be able to read or write the file, when you login as the second user. And things can become more complicated when you use the system for a longer time. 

So it is possible, but it will bring more troubles than benefits. What is the reason you want it anyway? There is probably a better solution. If you just want to share some settings, just use the first part of this message.

---

### Post by ZeldaFan on 2009-08-06
I tried creating a symlink, and it worked fine. But if I set up a symlink directed at my original user's thunderbird profile, thunderbird doesn't load for the other user (it doesn't load the profile). How do I deal with that?

---

### Post by michy99 on 2009-08-06
I think the ownership issue is going to be a real problem. You can point the other user at your profile, but the files are owned by you, not by him/her.

---

### Post by lisati on 2009-08-06
My background using mainframes which hold confidential data is making me mildly nervous about two users sharing the one account..... However, on our own machine, we are free to look into doing things the way we want and to make our own choices.

With the email, some email clients support multiple identities, which might go some way to keeping email separate if you do decide to go the route of using one user account for two people. The down side that the users would have to switch identity.

---

