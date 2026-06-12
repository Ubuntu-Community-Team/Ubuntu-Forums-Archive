---
title: "Can't delete files from samba share"
date: 2009-09-19
forum: General Help
---

### Post by alexlaban on 2009-09-19
I'm having a problem, I can't delete files from my samba share from my other computers but I can delete it using nautilus with the same account and I have permissions to do it but the error I get on the other computers says "You require permission from Unix User\rt to make changes to this file".  However I can delete files I've added/created to the server via samba just fine. 

smb.conf:
[http://pastebin.com/d3e3134e6](http://pastebin.com/d3e3134e6)

---

### Post by Roasted on 2009-09-19
Chances are you don't have the proper permissions enabled on your Samba machine. I just tested this with my Samba setup to confirm it using an XP machine to do the deleting of files and it worked in accordance to your problem.

What are the permissions of the samba network folder? My samba network folder has the permissions of 775, meaning owner can do anything, group can do anything, and all other users cannot write/delete. All samba users I added to a group called "sambashare", so my samba folder is owned by jason (me), group assigned is sambashare, and permissions are 775.

7 - Jason - Can Do Anything - Owner
7 - Sambashare - Samba users in group - Group
5 - All others - Cannot write/delete - All Others

Make sure the user trying to access the samba share has proper permissions. Your situation may be very different than mine that I gave an example of above, but if the user doesn't have permissions, it would explain the issue at hand.

---

### Post by alexlaban on 2009-09-19
> **Roasted said:**
> Chances are you don't have the proper permissions enabled on your Samba machine. I just tested this with my Samba setup to confirm it using an XP machine to do the deleting of files and it worked in accordance to your problem.

What are the permissions of the samba network folder? My samba network folder has the permissions of 775, meaning owner can do anything, group can do anything, and all other users cannot write/delete. All samba users I added to a group called "sambashare", so my samba folder is owned by jason (me), group assigned is sambashare, and permissions are 775.

7 - Jason - Can Do Anything - Owner
7 - Sambashare - Samba users in group - Group
5 - All others - Cannot write/delete - All Others

Make sure the user trying to access the samba share has proper permissions. Your situation may be very different than mine that I gave an example of above, but if the user doesn't have permissions, it would explain the issue at hand.
If I run ls -l it outputs the samba permissions as drwxrwxrwx and winshare as owner, nifelheim as group, the weird thing is that I can delete stuff I've added to the folder over samba just fine but I can only delete the other stuff from the computer running the samba server, both running nautilus from the winshare account and with the rm command.

---

### Post by Roasted on 2009-09-20
What if you add a user in samba, and log in as that user from Windows?

Samba plays nicer if you use Samba users, which is what I would recommend.

---

### Post by alexlaban on 2009-09-20
> **Roasted said:**
> What if you add a user in samba, and log in as that user from Windows?

Samba plays nicer if you use Samba users, which is what I would recommend.

Sorry if I sound noobish but how would I do that?

---

### Post by Roasted on 2009-09-20
sudo smbpasswd -a jason

jason being whatever user you want to add.

Whatever Samba users you must add, they must also exist on your system. If you're setting up a Samba file server just for you to use from other computers, then just use your own user name. If you are setting it up for other people to use as well, like I did, you'll have to add them as users to your Ubuntu system first, THEN add them to Samba as well. The Samba users you wish to add must also exist as users on the actual Ubuntu system too.

That way whenever you hit your file server, you have to log in. It's an extra layer of security that's a smart idea to have. On top of that, if you own (or are a part of the group that has full access to) the samba share, and have permissions like 775 instead of 777, then you're taking away everybody else's ability to mess with your files - which I'd recommend.

My setup:

I'm jason, and there's 3 other users in my system. All 4 of us are users on the Ubuntu system. All 4 of us are also Samba users that I added. I also added a group called "sambashare" and made us 4 members of it.

My samba share is owned by me, with the group sambashare being assigned to it too. Along with that, the permissions on the samba share are 775, owned by jason:sambashare.

That means Jason + sambashare has full reign over the files on the samba share. The users in sambashare are the other 3 members, in essence granting us 4 full reign, while everybody else has "5" permissions and cannot delete files off the share, which is ideal. Each user also has their own password, so when they log in, they're logging in as themselves, which thanks to Samba's functionality, I can from the Samba smb.conf file (or the Samba gui from add/remove) restrict/allow users to connect to certain shares. That way Bob can get into Bob's stuff, as expected, but Bob can't get into Fred's stuff, etc.

Your permissions on the Ubuntu machine itself play a key role in what users can and can't do. That's why I suggest you look at using Samba with users so you can customize things a little better.

---

