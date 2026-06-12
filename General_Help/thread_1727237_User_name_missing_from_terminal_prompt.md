---
title: "User name missing from terminal prompt"
date: 2011-04-12
forum: General Help
---

### Post by mjc7373 on 2011-04-12
Hi all. I have a file server on an office network running Ubuntu Server (Jaunty). I have Samba running to share directories on the LAN between about 7 users. 

One user has been complaining that he often runs into permission errors when accessing network shares. I have looked at the directory permissions and saw nothing amiss there, then checked Samba's user list (which is correctly set in the smb.conf file) which does have an entry for this user.

The only clue I have so far is when I log onto the server via Putty and SSH as this user, the user name and location is missing from the prompt. So when I'm logged with any other user, I see the normal prompt:

> user@server:~$

When I log in as this user I get this prompt:

> $

Another weird thing is while I'm logged in this way, the tab key doesn't work to auto fill text as it should. 

I'm baffled after scouring Google to no avail. Please help!

---

### Post by Azdour on 2011-04-12
Hi,

I do not think the empty prompt has anything to do with your permission problem.

When I create new users from the command line I have to remember to run:

```

sudo chsh --shell /bin/bash <username>

```

Then they get the correct shell with prompt and can use the tab key.

---

### Post by mjc7373 on 2011-04-12
Thanks Azdour! I used your code and now have a normal prompt for the user. 

Going back to my permissions problem, I did this:
> mjc@chlserver:/var/log/samba$ tail log.brian-hp
[2011/04/12 10:00:40,  1] smbd/service.c:make_connection_snum(1130)
  brian-hp (10.2.3.12) connect to service CHL Docs initially as user brian (uid=1006, gid=1008) (pid 13728)
[2011/04/12 10:01:03,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.

I Googled the error, and found info suggesting this was a permissions error that affects Mac OS X, which got my attention because we have one Mac user who also had permissions issues. However, the user associated with this Samba error message isn't the mac user, it's the user with the PC and permission problems. Could both these permission issues be related?

---

### Post by mjc7373 on 2011-04-12
UPDATE: As a possible fix for the Mac OS X permissions issue, I added this line of code to each samba share:

> unix extensions = no

Then I restared Samba. I'm hoping this fixes both permissions issues, but I'm not sure how to test it since I've not been able to replicate the problem. If anyone can shed some light on any of this I'd be very grateful!

---

