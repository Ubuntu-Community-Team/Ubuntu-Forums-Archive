---
title: "Cannot Read from Samba Share"
date: 2012-05-12
forum: General Help
---

### Post by slmpika on 2012-05-12
I created a samba share using the Samba Server Configuration tool. I have tried connecting to this share through both Windows 7 and my Wii. However, it is not working as it should.

- If I change the access to only allow access to a specific user, Windows 7 will prompt for a password; however, even after entering the password, access is denied.

- If I change the access to allow access to everyone, I can browse the share using Windows. However, I receive an error if I try to open any file. The same thing happens on my Wii.

The samba share I had previously on 11.04 was working fine, but I did a complete reinstall when I upgraded to 12.04, and I cannot get it to work now.

---

### Post by slmpika on 2012-05-13
I looked into the Samba logs and found that there is a single error causing this issue, even if I allow access to everyone:

passdb\lookup_sid.c:1667(get_primary_group_sid)
 Failed to find a Unix acount for wiicheck_sam_security:make_server_info_sam() failed with 'NT_STATUS_NO_SUCH_USER'

There is Samba User that I created named "wii", but not a User Account named "wii". I thought that Samba didn't require a user account to be created in order to create a "Windows User" for Windows to have access. What is the problem here?

EDIT: I solved a part of the problem by opening "Users and Groups" and adding my User Account to the group "wii". Now, I can restrict access to "wii" and log in through Windows using the Samba Username and Password. However, I still receive an error whenever I try to open or read any file in the share.

EDIT2: Solved (mostly). I was able to get this to work by Right-Clicking on the folder I want to share, going to Properties, and the Permissions tab. I changed "Other" to Read and Write, and now it works.

The reason I say that it is mostly solved is because I have no idea why it did not work before. "Read" was already a permission, so I don't know why this change allowed the files to be read when they couldn't be read before.

---

### Post by Morbius1 on 2012-05-13
> There is Samba User that I created named "wii", but not a User Account named "wii".How does one create a "samba user"?

You can only add a user that you created on the server to the samba password database. If there is no Linux user there is no samba user. For example if you run the following command ( and I'm betting you don't have a user named morbius ):
```
sudo smbpasswd -a morbius
```It will go through the motions of setting up a password but eventually end with the following error message:
> Failed to add entry for user morbius

---

### Post by slmpika on 2012-05-13
No, you are right, I didn't realize that the user existed because there was no home folder for that user. I'm not really sure what happened since somehow the user was recreated in "Users and Groups" after I added my user profile to the group "wii."

---

