---
title: "Problems Adding User"
date: 2006-03-17
forum: General Help
---

### Post by Sharka on 2006-03-17
I am having problems adding additional users to Ubuntu. I have used the :

System -> Administration -> Users & Groups -> Add Users and filled out the required fields.

However, when I try to log in with the new user name and password, I get a message stating: User not found in Home Directory. Do you wish to log in using failsafe mode ? I am then booted out and have to log in using the username & password which I picked when I installed Ubuntu Breezy Badger.

After logging in as my root, I then go to the home directory and can't find a folder for the new user. I only see the folder for the root user.

Is this a bug ? Or am I doing something wrong ?
 
As a new newbie, I appreciate all of your help. My experience in Ubuntu has been wonderful: spyware/virus free and no crashes like in XP. I can allow my household members  to surf the net without having to worry about them picking up any nasty virus/spyware.

---

### Post by dcstar on 2006-03-17
[QUOTE=Sharka]I am having problems adding additional users to Ubuntu. I have used the :

System -> Administration -> Users & Groups -> Add Users and filled out the required fields.

However, when I try to log in with the new user name and password, I get a message stating: User not found in Home Directory. Do you wish to log in using failsafe mode ? I am then booted out and have to log in using the username & password which I picked when I installed Ubuntu Breezy Badger.

After logging in as my root, I then go to the home directory and can't find a folder for the new user. I only see the folder for the root user.

Is this a bug ? Or am I doing something wrong ?
......[/QUOTE]
In the "Advanced" area of the add user stuff, what does it say for the Home Directory box?

Mine has: /home/$user

---

### Post by Sharka on 2006-03-17
Thanks for the response:

In the Advance area it says /home/$user.

The message which I get when booted out is:

"Your home directory is listed as:
'/home/gabar' but it does not appear to exist. Do you want to log in with the 
/(root) directory as your home directory ? It is unlikely anything will work unless you use failsafe session.

---

### Post by dcstar on 2006-03-17
[QUOTE=Sharka]Thanks for the response:

In the Advance area it says /home/$user.

The message which I get when booted out is:

"Your home directory is listed as:
'/home/gabar' but it does not appear to exist. Do you want to log in with the 
/(root) directory as your home directory ? It is unlikely anything will work unless you use failsafe session.[/QUOTE]
For some reason the User Home directories do not seem to be created when you add a user.

As soon as I add a new user on my system, the Home directory is created ok, is your "Home" directory on your root filesystem or a seperate one?

---

### Post by Sharka on 2006-03-17
When I log in as my root, the file path is:

/home/(my login name)

But when I create a new user, the file path reads in the users and groups advanced window reads:

/home/(new user name)

But under the home directory, I don't see a folder for the new user but see a folder for the root.

I hope that I answered your question, "is your "Home" directory on your root filesystem or a seperate one?"

Thanks very much

---

### Post by Sharka on 2006-03-17
I managed to rearrange the home directory path under the Advanced tab of the Users and Groups by typing in :

/home/(new user name) 

This fixed the problem but I noticed upon logging in that the new user can add other users so I am not quite sure if the new user has Administration priviledges.

Am I correct in assuming that this person has Administration priviledges ?

---

