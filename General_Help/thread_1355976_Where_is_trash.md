---
title: "Where is trash:///"
date: 2009-12-15
forum: General Help
---

### Post by bradcan on 2009-12-15
Before answering this question please read the title carefully.

The question has been asked and answered WRONGLY many times before.

Now I have some root owned files and directories in my trash. It's easy enough to get them in but how to get them out?

sudo updatedb; locate trash; locate .trash; locate .Trash etc produce nothing!

Doing a sudo natulius produces an error that .Trash does not exist for root!

So simple question where is location trash:/// which nautilus displays when I open my trash?

I know how to gain a traditional root login but that does not solve the problem either, obviously.

If somebody really knows how to get at thrashed files from the command line I would be really grateful learn and so would a lot of others.

TIA

---

### Post by philinux on 2009-12-15
/username/.local/share/Trash

and 

/root/.local/share/Trash

---

### Post by ajgreeny on 2009-12-15
As for the locate command, it's worth using the -i option (ignore case), and not using the . before the searched string, ie ```
locate -i trash
``` See what that gives you.

For root owned files and folders you will need to remove them as root, so use ```
gksudo nautilus
```and navigate to /root/.local/share/Trash or do it in command line.

---

### Post by bradcan on 2009-12-16
Thanks philinux you get the kudos because you are correct. well nearly!

Logged in as me:
cd .local/share/Trash
sudo chown -R me::me *
[sudo] password for me:

My trash is now unlocked :)

So actually /home/me/.local/share/Trash

---

### Post by bradcan on 2009-12-16
> **ajgreeny said:**
> As for the locate command, it's worth using the -i option (ignore case), and not using the . before the searched string, ie ```
locate -i trash
``` See what that gives you.

That is correct, but only if sudo updatedb has been executed.

> 
For root owned files and folders you will need to remove them as root, so use ```
gksudo nautilus
```and navigate to /root/.local/share/Trash or do it in command line.

Not if root owned files are in my trash, only if the trash was created logged in as root where ~ is a synonym for /root

When logged in as 'me' this: sudo ls ~ displays /home/me NOT /root

So trash created logged in as 'me' using for example:
sudo touch locked.file then dragged locked.file to trash by 'me'.

locked.file is not visible to gksudo nautilus because that's the same as logging in as root I think?

---

### Post by ajgreeny on 2009-12-16
> **bradcan said:**
> That is correct, but only if sudo updatedb has been executed.



Not if root owned files are in my trash, only if the trash was created logged in as root where ~ is a synonym for /root

When logged in as 'me' this: sudo ls ~ displays /home/me NOT /root

So trash created logged in as 'me' using for example:
sudo touch locked.file then dragged locked.file to trash by 'me'.

locked.file is not visible to gksudo nautilus because that's the same as logging in as root I think?
I'm sure you are right, but you have lost me there.  I am pretty sure that any files which are present in a folder can be seen when using gksudo nautilus.  If no files are seen, then none are present.

Perhaps that's what you were trying to say, but as I said, I got a bit lost with your argument.  In any case, I don't think you can put root owned files into a user's trash, but once again, perhaps I've misunderstood your meaning.

---

