---
title: "No way to specify a user number?"
date: 2010-05-12
forum: General Help
---

### Post by OlympicSoftworks on 2010-05-12
** How does someone set up a new user with a specific user number?

I have a fairly large family, and all of us use Ubuntu GNU/Linux.  When I needed to set up a NAS for the family to backup to and such things, I set it up with each user having their own user number in their folders on the NAS.  With previous versions of Ubu I was able to set up their user number so the NAS saw them as the owner of the folders, but I can't update them to 10.4 because I can't set their user numbers in the provided graphical tool.

I could probably use useradd, in a console to get the job done but I can't believe there is no provided way to do this.  What am I missing?

---

### Post by blueridgedog on 2010-05-12
I suggest you test this in a virtual install (sun VirtualBox comes to mind).  

I have in the past changed user ID's by hand editing /etc/passwd.  You can see the user id's pretty plainly and you can assign them if you want to alter the default setting.  This will orphan files owned by that user, but you can correct that by reassigning ownership after you make the change.  You should NOT change the base user, as that user will need to have a home directory that they own, so they can log in and clean up the mess that is created with you change the other user id's.

So, assuming you have at least two users on a test system, with the first user account being an administrative one (authorized for sudo when the system was installed) you could edit the user ids with the following:

```
sudo gedit /etc/passwd
```

Edit the ID and group ID of the user you want to change (they are identical with a clean install).

The line looks like:

```
jane:x:1001:1001:Jane Doe,,,:/home/jane:/bin/bash
```

To Change the ID to 1500, you would edit the line to read:

```
jane:x:1500:1500:Jane Doe,,,:/home/jane:/bin/bash
```

Do not use 1000 as that will be your base admin user account and do not use a number below 1000 as those IDs are for system accounts.

Then edit the group file to also alter the group ID:

```
sudo gedit /etc/group
```

Use the same number used in passwd

The place to make the change should be intuitive at this point.

Then resyncronize the passwd and group shadow files:

```
sudo /usr/sbin/pwconv
sudo /usr/sbin/grpconv
```

Then change the home directory of the user you edited so the new ID owns the files:

```
sudo chown jane:jane /home/jane -R
```

Change jane to be the user name being changed in this instance.

This is from memory and from the days when I had to restore Linux systems with re-mounted /home files systems in which we needed to match user IDs to existing file ownership IDs.  It is some deep tinkering and I again suggest you test the process to verify that you are comfortable with it before trying it on a live system.

---

### Post by OlympicSoftworks on 2010-05-26
I know about those files, and if that's what is needed then I'll have to do it until I get schooled up on how to do LDAP authentication.  I am seriously surprised that the community took out the ability to specify the user number from the user admin tool though.

I will re-post my success...or lack of it.

Peace.

---

### Post by KeyserSoze93 on 2010-05-26
> **OlympicSoftworks said:**
> I know about those files, and if that's what is needed then I'll have to do it until I get schooled up on how to do LDAP authentication.  I am seriously surprised that the community took out the ability to specify the user number from the user admin tool though.

I will re-post my success...or lack of it.

Peace.

Instead of using LDAP, you could try the venerable NIS. NIS allows all user/group data to be read from one box, and works great when combined with NFS.

I work on a system which uses NIS/NFS to provide user ids and networked file storage to hundreds of users and it works a treat.

There are plenty of guides to setting up NIS servers and clients if you Google "Setup NIS ubuntu".

I am actually in the process of setting up another small office for some friends, which will also use NIS for all passwd entries instead of local users per-PC.

If the NIS server is also the file server, you only need one /etc/passwd file for the entire network.

---

### Post by gmargo on 2010-05-26
The best way to modify a userid number is through the usermod( 8 ) command-line tool.

As far as editing the /etc/passwd and /etc/group files, do not edit these directly; if you must edit them use the vipw( 8 ) and vigr( 8 ) commands.

---

