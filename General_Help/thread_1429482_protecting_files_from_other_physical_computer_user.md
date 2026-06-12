---
title: "protecting files from other physical computer users"
date: 2010-03-14
forum: General Help
---

### Post by m4lte on 2010-03-14
Hi,

I occasionally have friends using my home computer. They just use my account.

There are some files that I want to hide/protect from people using my computer. It's not that I need highly secure encryption, it's more like I want to make sure people don't accidentally see my porn collection if they borrow my computer to check their email.

Is there a way to set up a folder such that it's required to enter a password (e.g. the admin password) to see it's content? Probably I could change the owner of the folder, so that I can't access it without password?

How do you protect/hide your secret or intimate files?

---

### Post by ajgreeny on 2010-03-14
> How do you protect/hide your secret or intimate files?     You don't let other people use your user account!

Why not make a new user with no password requirement?

Make  a new user in normal way with username "guest" and temporary password.  **Do not give that user admin permisssions.**
Go to /etc/shadow as root and edit the line:-
guest:some:long:line:of:characters::13720:1:99999:7::: 
to read
guest:U6aMy0wojraho:13720:1:99999:7::: 
U6aMy0wojraho is the encrypted version of nothing, ie no password.

Other users can now login as guest and simply hit return at the password prompt without entering anything, and will be logged in.

---

### Post by az on 2010-03-14
Encryption is truly the most effective way to ensure your privacy.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

And it's not that complicated.

---

### Post by mcduck on 2010-03-14
I agree with ajgreeny that you simply shouldn't let them use your own account. Either create a new user for your friends to use, or log them into the guest account (available in the user switcher applet in the top right corner of your desktop on any new Ubuntu version) when they need to use your computer.

Of course if you for some reason don't want to do that (not that I could imagine any good reason why) then encrypted directory is the way to go. The easiest & simplest way to do that is to install Cryptkeeper (_very_ simple Gnome tool for creating and managing encrypted diretories, using EncFS).

---

### Post by DawieS on 2010-03-14
> **m4lte said:**
> Is there a way to set up a folder such that it's required to enter a password (e.g. the admin password) to see it's content? Probably I could change the owner of the folder, so that I can't access it without password?

Create a new user "private" by selecting the **System - Administration - Users and Groups** tab.(Click on the keys to make changes and enter the sudo password). Click on the "Add" tab. Enter a new password for this user "private". A new home folder for user "private" will be created.

Now log out and log in as "private". Open a file browser. Click on the home folder of "private" to mount it. Right-click and select "Properties", then "Permissions". Select folder access as "None" to both **Group** and **Others**. Click on "Apply Permissions to Enclosed Files" and close the window.

Now copy your private files or folders over to this newly created home folder of user "private". Make sure they are all there, then log out and log in as yourself. Now delete your private files at their original location.

Notes:

- You, or any other user, will NOT be able to see the contents of the home folder of user "private". Although the files are there, the home folder will show as "empty" in the file browser. 

- Should you require to update or use your private files, you must again log in as "private" and repeat the copy/delete process.

- Should you later decide to make your private files readable to other users (including your own normal account), you must again log in as "private" and reset the permissions accordingly.:grin:

---

### Post by subedistra7 on 2010-03-14
make a new folder. dump all your porn/whatever into it, compress the folder with a password, and rename it with a . in front of it like [COLOR=Red].new folder[/COLOR]. that will hide it. double or triple compress with passwords if youre truly paranoid. as long as its legal porn, you have nothing to worry about.

---

### Post by nx2ho on 2010-03-14
Please read ( and understand ! ):

[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive) ,   "Permissive home directory access"

[https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734](https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734)

Adjust the file permissions:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

HTH

---

### Post by m4lte on 2010-03-14
> **az said:**
> Encryption is truly the most effective way to ensure your privacy.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

And it's not that complicated.



Thanks az, I set up an encrypted folder according to the instructions. That's pretty much what I was looking for.

Though, **what happens if I want to create a backup?** Do I need to mount the private directory and then it will be backed up as if it wasn't an encrypted file?

---

