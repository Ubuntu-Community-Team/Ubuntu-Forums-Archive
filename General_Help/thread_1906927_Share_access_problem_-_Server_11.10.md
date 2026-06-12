---
title: "Share access problem - Server 11.10"
date: 2012-01-10
forum: General Help
---

### Post by mcreef on 2012-01-10
I am having an issue I am not quite sure how to correct, maybe you folks can help me find where I am going wrong...

I have Samba configured so that she works just as I want her now. File ownerships and permissions seem to be functioning as I intend, with one exception. A user on the network running a WinXP machine wanted to back up some files to the new server. I added a new user to the system, created a new group and made him a part of it, then created a directory that his group would have RWX access to. This works fine and dandy, the problem is he also has access to all of the other directories as well, and I'm not sure why. If I go to the "Network" page on the XP machine, I can map to, access, read, write, and execute in any folder that I have made browsable regardless of the fact that this user is neither the owner nor is he a part of the group who is assigned to the directories. Permission to the directories/files in question are set to 0770, so guests should have no access whatsoever.

My current thinking is that the problem lies in the "force user" command. I am using "force user" to force any new files or directories or files created anywhere within any of my shares to be owned by one user. This "forced" user will then have overall control of all files/folders through ownership, and everyone else' permissions will be decided through the use of the "group" and "other" permissions.

What I am wondering is this, does "force user = x" simply assign ownership of any new file/directories to "x" regardless of who created them (say user "y" in this example", or does it go further, actually transferring the permissions of user "x" to user "y", essentially giving them access to anything user "x" has ownership of?

I hope I am being somewhat clear in what I am asking here, if not, let me know.

---

