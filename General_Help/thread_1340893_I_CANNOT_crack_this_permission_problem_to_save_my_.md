---
title: "I CANNOT crack this permission problem to save my life."
date: 2009-11-29
forum: General Help
---

### Post by Roasted on 2009-11-29
I have a Kubuntu file server using Samba. It's worked great for a long time, no issues. I have a "system" with my shares - everything is owned by Jason, and "Samba" is the effective group assigned to each share. All permissions are 775, so only Jason or Samba members can write to the shares.

Members of the group Samba:

Jason
Pam
Curt
Tyler

Users not a member of the group Samba:

test1
user


Permissions of test share in question:

drwxrwxr-x  6 jason samba  4096 2009-11-29 04:37 test

The moral of the story is this. The only people who can write are Jason and Samba users. "User" is NOT a member of Samba. "User" is NOT the owner of the share. Yet User can write to the share.

I don't get it. I'm so far beyond lost it's not even comprehensible. How can a user with "others" rights of r-x actually WRITE folders and files to the share from an XP system? 

What am I doing wrong??

EDIT - The weirdest part is, if I remove write permission from the group, THEN "user" gets denied when trying to write to the share.

Keep in mind - "Others" do not have write permission, and "User" is NOT a member of "Samba." (the group assigned to the share)


EDIT AGAIN - This is even weirder. So I finally thought, ya know, maybe there's just something wrong with the group "Samba". So I deleted Samba and re-added it and re-added the members to it.

Then, I assigned the share the group Samba. I was able to write to it with my user known as "User."
Then, I assigned the share to the group Sambashare. I was NOT able to write to it with "User." 
Okay, great. This is looking good! User CAN write with Samba, User CANNOT write with Sambashare.

Problem is, I looked at the group settings for "Samba" - "User" is NOT a member of "Samba." Yet he was able to write with "Samba" being the group.

What the hell...

---

