---
title: "multi users issue on Ubuntu 12.04 64"
date: 2012-08-12
forum: General Help
---

### Post by hunterkasy on 2012-08-12
I am running Ubuntu 12.04 64 with all updates, I have 2 accounts 1 admin and 1 standard.  whenever I logg off one account and log into the other one the top panal won't display anything and the launcher won't do anything, the mouse moves and I can do ctr-alt-f2 and reboot from their.  It does not matter wich account I am in, once I log off and try to go back into the same account this same issue happens.

thanks in advance for your help

Tyler

---

### Post by irv on 2012-08-12
My question is why do you want to setup a admin account? You can do anything you want in user account by using su or sudo. You can run any app in su mode. To me this is a less dangerous way to do things.

---

### Post by hunterkasy on 2012-08-12
> **irv said:**
> My question is why do you want to setup a admin account? You can do anything you want in user account by using su or sudo. You can run any app in su mode. To me this is a less dangerous way to do things.

what I meant as admin is the first account that Ubuntu made for me the account type is called administrator, so I called it admin,

sorry for confustion

---

### Post by irv on 2012-08-12
In your home directory you have a hidden folder call .gnom2 (don't forget the “.”) and in there is a folder call nautilus-scripts. I have a few scripts files in there that let me do some root stuff from nautilus.
[ATTACH]222610[/ATTACH]
 If you right click on a file or folder you will see a script list on the pop out menu. 
[ATTACH]222611[/ATTACH]
You must set all scripts files to execute. You do this by putting a check mark in  allow execution in the property settings.
If you are interested in these script file I have them on my server so you can download them by right mouse clicking on them and save as. Here is the [LINK]("http://wabasha-server.net/Nautilus%20Scripts/").

---

### Post by irv on 2012-08-12
> **hunterkasy said:**
> what I meant as admin is the first account that Ubuntu made for me the account type is called administrator, so I called it admin,

sorry for confustion

A standard install only creates two accounts. your user account and a guest account. 
[ATTACH]222612[/ATTACH]

---

### Post by hunterkasy on 2012-08-12
> **irv said:**
> In your home directory you have a hidden folder call .gnom2 (don't forget the “.”) and in there is a folder call nautilus-scripts. I have a few scripts files in there that let me do some root stuff from nautilus.
[ATTACH]222610[/ATTACH]
 If you right click on a file or folder you will see a script list on the pop out menu. 
[ATTACH]222611[/ATTACH]
You must set all scripts files to execute. You do this by putting a check mark in  allow execution in the property settings.
If you are interested in these script file I have them on my server so you can download them by right mouse clicking on them and save as. Here is the [LINK]("http://wabasha-server.net/Nautilus%20Scripts/").

I have no files or folders in the folder nautilus-scripts

---

### Post by irv on 2012-08-12
> **hunterkasy said:**
> I have no files or folders in the folder nautilus-scripts

You won't that's why I gave you the link to my server to download the scrip files. After downloading them you need to copy them to this folder and make them so they can be execute.

---

### Post by hunterkasy on 2012-08-12
> **irv said:**
> You won't that's why I gave you the link to my server to download the scrip files. After downloading them you need to copy them to this folder and make them so they can be execute.

ok, I downloaded all of your scripts and pasted them in the right folder and made them so they can be execute

---

### Post by irv on 2012-08-12
> **hunterkasy said:**
> ok, I downloaded all of your scripts and pasted them in the right folder and made them so they can be execute

Now when you right click on a file or folder you should see an option "Scripts" with all your script files listed under it.

---

### Post by hunterkasy on 2012-08-12
> **irv said:**
> Now when you right click on a file or folder you should see an option "Scripts" with all your script files listed under it.

yes, I seen the scripts options with all of the scripts, 
now how can I use the scripts to fix my problem?

---

### Post by irv on 2012-08-12
> **hunterkasy said:**
> yes, I seen the scripts options with all of the scripts, 
now how can I use the scripts to fix my problem?

This is not going to fix your problem all this will do is allow you to do things with admin rights without logging in with admin. What I was trying to show you is all you need is one login. You don't need to switch users to do things. The more you use Linux the more you will learn how to do things with the command line prompt. It is much easier and faster and you will find this out as time goes on.
I was just trying to show you that you can do things with the GUI with admin rights as well.

---

### Post by hunterkasy on 2012-08-12
Does anyone have any idea what could be wrong and how to fix it?

---

### Post by hunterkasy on 2012-08-12
> **irv said:**
> This is not going to fix your problem all this will do is allow you to do things with admin rights without logging in with admin. What I was trying to show you is all you need is one login. You don't need to switch users to do things. The more you use Linux the more you will learn how to do things with the command line prompt. It is much easier and faster and you will find this out as time goes on.
I was just trying to show you that you can do things with the GUI with admin rights as well.

I have 2 logins because the 2nd one is for a kid, that one is the standard account.  the "main" account is the one Ubuntu made and if you go to system settings and user accounts it shows the "main" account as administrator

---

