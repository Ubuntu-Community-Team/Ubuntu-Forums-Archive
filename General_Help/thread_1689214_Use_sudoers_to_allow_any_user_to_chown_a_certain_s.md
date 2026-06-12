---
title: "Use sudoers to allow any user to chown a certain set of files"
date: 2011-02-16
forum: General Help
---

### Post by stillnotelf on 2011-02-16
Hi,

I have a fairly complicated request.  The short version is, I want to set up a system so that any user can change the ownership of a certain set of files at any time without root access.  I think it's possible to set up sudoers to do that, but so far I have failed miserably.

I have tried setting up a wrapper script around chown, then putting that script into sudoers, but it didn't work.  Here's the script and sudoers (paths changed to genericize them):

```
#!/bin/bash

#this script moves a copy of the code
mpth=/path/to/directory/

echo "usage: claim_copy.bash (db)copy_#"

#change this copy of mini to belong to the invoker of this script
chown --recursive $USER $mpth/$1
``````

#sudoers is ubuntu default up to this point
ALL computer_name = (ALL) /path/to/directory/claim_copy.bash
```Ideally, I want it so that any user on the system can chown any files in one certain directory (/path/to/directory) - that should be the only extra permission they get by this script.  Currently, the setup spits "chown: changing ownership of `(a file name): Operation not permitted" for every single file, recursively.


The long version:
I want to set up a system so that a large software installation can be cloned off as needed to facilitate its development.  Many of our tests (formal and otherwise) depend on comparing the behavior of unmodified code to modified code.  I'm trying to set up a system so that there will be several unmodified copies of the code laying around, precompiled, with the testing data precomputed.  (So far, so good, all this is handed by cron jobs).  These copies can then be taken to either make changes to for new code branches, or use as references.  

This is where I hit the problem.  The copies "belong" to a certain user - me.  But, I want them to be available for others to take as needed.  Here are some of the obvious solutions, and why we don't want to do it that way:

A) cp operations to generate new directories, rather than mv operations moving them out of the cron-maintained set.  This is bad because the copy operation is very slow, whereas move is instantaneous.  The point of this system is making it super-fast to get clean copies, which is one of the chokepoints now for actually using our testing suites.

B) chmod the files to be world-editable.  Then anyone can move them without difficulty.  This is a problem because it a) leaves them "owned" by me, not their new owner, and b) leaves you with bizarre file permissions instead of default ones (-rw-r--r-- would be best...)

C) set the system up for each user individually - this is too expensive in terms of disk space to hold their spare copies, and computing time to keep recompiling them regularly to keep them fresh.

I am open to solutions other than the move script I've described, but our needs are fairly specific.  Thanks for any advice...

---

### Post by Monotoko on 2011-02-16
Hi Stillnotelf,

Can you not put the users in the same group? Then you can allow all the files to be modified by every user of that group. (775)

---

### Post by stillnotelf on 2011-02-16
I've never used groups so I'm not really familiar with how it works.  I was hoping for a solution that won't require manually configuring /etc/group every time a new user is added (invariably we'll forget to add someone, then 3 years from now someone will spend an afternoon debugging why they, and only they, can't use this system all of a sudden).

If we're all in one group, then is there some way to restrict the permissions to these files?  Do we have to remember to not change the middle three group permissions w/chmod for all other files on the system, since we're using group to handle this set?

If I set the group bits as you suggest, can they be chowned afterwards?  (chown to self, then chmod to normal 644?)  That has promise.  I'll try it out shortly...

---

### Post by gzarkadas on 2011-02-19
The simple solution is to enable the set-gid bit in directories permissions and allow the group write permissions. Using the set-gid bit has as result that any new file or directory created inside will belong to group and thus be editable by all members of the group.

In short, do:

```
chmod -R 2775 <your-project-base-folder>

addgroup --system --gid 900 devels
chown -R <you>:devels <your-project-base-folder>

# for every user execute this to add him/her in devels group
adduser <user> devels 
```Then, modify your /etc/adduser.conf to assign automatically the devels group in new users (assuming you want all new users to be devels), using these steps:

1. Open /etc/adduser.conf (as root) with your favorite editor
2. Find the line EXTRA_GROUPS=
3. If it is commented out, uncomment it
3. Add devels to the end of the groups list (be careful to be inside the double quotes)
4. Find the line ADD_EXTRA_GROUPS=
5. Ensure it is either =1 or commented out (the default is 1)

As your users keep editing files the user that owns the file will change to their uid. This is not bad since it allows to keep track who was the last to change a file. But if you prefer one user to own the files, add a cronjob to periodically execute a `chown -R <select-user>:devels <your-project-base-folder>'.

---

### Post by stillnotelf on 2011-02-21
Thanks to both of you.

I'd gotten the sticky-bit stuff figured out just by mucking around and Google.  The hint to change adduser.conf was really helpful, though; the dangling thread was how to make people remember to add themselves to the group at user creation time!

---

