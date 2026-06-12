---
title: "Changing UID"
date: 2010-12-21
forum: General Help
---

### Post by NertSkull on 2010-12-21
If I change the UID and Group ID of the main user account (the one set up during install, which is the same password as root) will it mess things up?

My biggest concern is file permissions on the home directory.  

My reason is I have a NFS server set up.  But the user id's and group id's are not the same between the computers.  Its just a home computer setup with 2 desktops and a laptop.  So I don't really want to try to install NIS or other options.  It seems it would be easy to change the UID and GID to match on the three users and then everything would work smoothly (at least from what I've read).

But, I don't want to change these and have everything get broken.  So is this a bad idea?

---

### Post by tredegar on 2010-12-21
_Do not do this_ whilst logged in as yourself.
_Do not do this_ by **sudo**-ing to root from your own account.  

Well, it might be OK, but I didn't try it when I changed the UID of my "Administrator account, (so if you are feeling lucky, go ahead, just don't blame me for any mess.)

Boot to a root shell in "Rescue Mode".

Now you have a root login, and your username is not logged in, you can make the change to your UID like this
```
usermod -u 1234 NertSkull
```
See **man usermod** for what this does.
Reboot normally.

Test your account is still working as it should.

---

### Post by NertSkull on 2010-12-21
Thanks, I'm going to try that when I get home.

I wouldn't have thought about logging in like that instead of sudo.  But it actually makes sense and seems like a safer idea.

I'll try it later and see how it works.  I figure as long as I can change it back to the original UID and GID I should be ok to test.

thanks

---

### Post by NertSkull on 2010-12-22
So that worked pretty well.

I logged into recovery mode.

Then I changed the GID

```
groupmod -g XXX groupname
```

Then I changed the UID (and assigned the new UID)

```
usermod -u XXX -g XXX username
```

That updated the UID in the home directory.  But I still needed to change the group ID and the UID and GID on the rest of the drive.  So I ran the following two lines

```
find / -uid (OLD UID) -exec chown (NEW UID) {} \;
find / -gid (OLD GID) -exec chgrp (NEW GID) {} \;
```

And now everything seems to be in great shape.

The only thing I could think being a real issue is if some program expects a certain username to have a certain UID.  But since I was only changing regular user accounts (above 1000) not system users (below 1000) I highly highly doubt that will ever be an issue.

---

