---
title: "Working with firefox 3.6 from the terminal"
date: 2011-05-25
forum: General Help
---

### Post by Azdour on 2011-05-25
Hi,

I have written a CyberCafe style application that runs on an Ubuntu Server (Ubuntu 10.04). It can create and delete user accounts.

I've done some googling but I've not found any straight answers to the following questions:

[LIST=1]
[*] I want a standard set of bookmarks in Firefox for new users. Is there any commands I can use at the terminal so that I can write a script to do this?
[*] I know you need a Firefox profile to add bookmarks. If I understand correctly they are stored in the places.sqllite file. So in order to add bookmarks I need to first generate a profile. How can I generate a new profile when creating a new user account?
[/LIST]

Any tips would be appreciated or possibly you may have ideas about other ways to go about doing what I want to do? At the end of the day I want a script that can be run to do this without the use of any UI, thanks.

Update: Another idea I have been thinking about is to create a new user, launch firefox, add the bookmarks, tar the profile. Then untar the profile when a new user is created making sure to create a profile.ini to point to the new profile. I'm not sure if this approach will have any issues though.

---

### Post by lovinglinux on 2011-05-25
You can create a new profile by command. However, it doesn't create the files you want, which are only created when you start Firefox with the new account.

I think the simplest way would be to create a base Ubuntu account, start Firefox, add the bookmarks and configure Firefox. Then make a script to copy the ~/.mozilla folder from the base account to the new user account.

---

### Post by Azdour on 2011-05-26
Hi,

Ok, thanks for info. I will try and make a default .mozilla and see how that works.

---

### Post by mcduck on 2011-05-26
You can just create the "base" account, then copy the relevant config files & directories from that account into /etc/skel/. Anything in that directory will automatically get copied to new user's home directories.

---

### Post by Azdour on 2011-05-26
Hi,

I think there maybe instances where the user account it creates does not need these bookmarks, but thanks for the suggestion regarding etc/skel - I had forgotten about that.

---

### Post by Azdour on 2011-05-26
Hi all,

The copying a basic mozilla profile with the bookmarks in works well, thanks.

---

### Post by lovinglinux on 2011-05-26
> **Azdour said:**
> Hi all,

The copying a basic mozilla profile with the bookmarks in works well, thanks.

You are welcome.

---

