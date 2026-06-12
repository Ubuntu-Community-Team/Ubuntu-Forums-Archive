---
title: "Setting up a share folder in home directory"
date: 2011-02-24
forum: General Help
---

### Post by Rytron on 2011-02-24
Hi.

I've created a folder in /home called share. I am the owner. It has no group access. Others have full access. Is this setup safe?


My current setup:
```
/home$ ls
eve  share  lost+found  roy
```

I want eve and any future users to have full access to the folder 'share'. I am user 'Roy'.

---

### Post by wt8008 on 2011-02-26
If you give `other' permission to delete or add files any other user on that system will be able to do so. If you want to test what they can do you can add some test users to play around with it.

Assuming this is not a server system, you should be fine.

---

### Post by tredegar on 2011-02-26
You might like to **chmod 700 /home/roy** so other users do not have access to your home directory, unless you subsequently grant it.

The ubuntu default seems to be to allow other users read access, but not write, to your home files.

To check your current permissions do **ls -l /home** and check the permissions for roy

---

### Post by Rytron on 2011-02-27
> **tredegar said:**
> You might like to **chmod 700 /home/roy** so other users do not have access to your home directory, unless you subsequently grant it.

The ubuntu default seems to be to allow other users read access, but not write, to your home files.

To check your current permissions do **ls -l /home** and check the permissions for roy


Here is my output from [COLOR="Indigo"]ls -l /home[/COLOR]
```
drwxr-x--- 240 roy roy 12288 2011-02-27 15:04 roy
```

---

### Post by Rytron on 2011-02-27
> **wt8008 said:**
> Assuming this is not a server system, you should be fine.

It is just a desktop PC

---

### Post by Morbius1 on 2011-02-27
What is the intended purpose of /home/share?

Are you trying to create a common shared directory for all local login users to access?

Or are you trying to create a shared directory for everyone on your local network to access?

Two different things and the permissions would be totally different depending on how you set up your Samba share.

---

### Post by tredegar on 2011-02-27
Rytron (the OP) didn't say anything about Samba, I _assumed_ he just needs a shared dir for the users of his linux PC.
> Here is my output from ls -l /home
Code:

drwxr-x--- 240 roy roy 12288 2011-02-27 15:04 roy

The permissions for **/home/roy** are fine. Nobody but **roy**, or members of the group **roy** have access to the files.

If you **chmod 666 /home/share** then everyone will have read / write access to /home/share

Hope this helps.

---

### Post by Morbius1 on 2011-02-27
Sometimes I get hung up on the details of the exact requirements of the user.

> **tredegar said:**
> If you **chmod 666 /home/share** then everyone will have read / write access to /home/share
I think you have a typo there. I think it should be "chmod 777". If it's 666 no one will be able to add anything to the folder not even the owner.

But let's take that an an example. Let's say we do a chmod 777 /home/shared.

It's true that all local users will be able to add or delete a file to that folder but they will not be able to edit any files in that folder other than their own. If that's what the user wants then that will work.

If however the requirement is that any user should be able to edit any file in that folder then something else is required. Something like this:
```
sudo chown :plugdev /home/share
sudo chmod 2775 /home/share
```And the default umask in /etc/profile will have to change to 002 so that every subfolder / file saves with permissions of 775 / 664.

Then every file saved to /home/share will have owner= user-name, group = plugdev, and permissions of 664. Every member of the plugdev group will be able to write to every file in that folder.

Things can get complicated depending on what exactly he wants.

---

### Post by tredegar on 2011-02-27
> I think you have a typo there. I think it should be "chmod 777"
You are quite right.

Meanwhile, we need the OP to define what he wants / is looking for, better.

Best wishes.

---

### Post by Rytron on 2011-02-28
> **Morbius1 said:**
> What is the intended purpose of /home/share?

Are you trying to create a common shared directory for all local login users to access?

Or are you trying to create a shared directory for everyone on your local network to access?

Two different things and the permissions would be totally different depending on how you set up your Samba share.

I am trying to create a common shared directory for all local login users to access. I am not on a network.

---

### Post by Morbius1 on 2011-02-28
> **Rytron said:**
> I am trying to create a common shared directory for all local login users to access. I am not on a network.

**(1) Access defined as all users can add to and delete from the folder and can read but not write to each others files:**
```
sudo chmod 0777 /home/share
```**(2)** **Access defined as all users can add and delete from the folder and can read and write to every file:**
```
 sudo chown :plugdev /home/share
``````
 sudo chmod 2775 /home/share
```Edit /etc/profile as root:
```
gksu gedit /etc/profile
```Find the line at the bottom that references umask and change it to:
```
umask 002
```Logout and log back in again since profile is  read only once at login.

---

### Post by Rytron on 2011-02-28
> **tredegar said:**
> Meanwhile, we need the OP to define what he wants / is looking for, better.Best wishes.

Hi. I just want to be able to put files & folders into the share directory so that other user on PC can copy it to their home folder and edit on their side (it is not necessary for other users to edit in share folder).

---

### Post by Rytron on 2011-02-28
Thanks for that comprehensive post Morbius1.

---

### Post by Rytron on 2011-03-01
What exactly are the numbers in purple bold. I only saw them as three numbers before such as **750** and **777**.

sudo chmod **[COLOR="Indigo"]0777[/COLOR]** /home/share
sudo chmod **[COLOR="Indigo"]2775[/COLOR]** /home/share

---

### Post by Morbius1 on 2011-03-01
In the first example ( chmod 0777 ) it's really unnecessary since if it's missing it's assumed to be zero.  Habit I guess.

In the second example ( chmod 2775 ) the "2" represents the setting of the "setgid" ( set group id ) bit. This is what allows all the adds to the that folder set that way to "inherit" the group of that folder for all the members of that group. I guess technically what it does is replace the default group of the user with the group of the parent folder.

If I save a file to a random folder it will save as:
owner = morbius
group = morbius

If I save it to a folder that has a group = othergroup and has permissions of 2775 then my new file will save as:
owner = morbius
group = othergroup

---

### Post by Rytron on 2011-03-04
Thank you Morbius1. You have been most helpful.

---

