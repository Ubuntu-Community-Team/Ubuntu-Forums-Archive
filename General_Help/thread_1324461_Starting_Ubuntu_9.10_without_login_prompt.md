---
title: "Starting Ubuntu 9.10 without login prompt?"
date: 2009-11-12
forum: General Help
---

### Post by Andy H. on 2009-11-12
I have my machine in a secure location and would like to know how to set it to boot without the login screen and allow to change users without login prompt. I don't really mind being prompted for changing configuration or adding software but would prefer not to be bothered with this also.
 
How can I set Ubuntu 9.10 to start without login prompt?
 
Thanks,
 
  -AH

---

### Post by dserver on 2009-11-12
There is an option for auto login under System > Administration > Login (Login Window?). I'm not sure what its called exactly but it's definitely under Administration.

---

### Post by Andy H. on 2009-11-12
Thanks - That was the first place I tried looking.  Under the option "Login Screen" there is only an option for asking who will log in (multiple user login screen) or for the machine to boot to my login, but nothing that appears to allow me to disable the login prompt. 

When I authenticate and access "Login Screen Settings" the option "Allow [dropdown menu <me>] to log in automatically" is checked but it doesn't seem to mean what Ithink it should mean as I'm prompted to log in whenever the machine starts up.

I also tried the "System>Administration>Authorizations" option and got the following error message:

> [SIZE=3]**Could Not Launch Authorizations**[/SIZE]
Failed to execute child process "polkit-gnome-authorization" (No such file or directory)I don't think this is the correct place to set that option though I may be wrong.

Any other suggestions?

Thanks,

   -AH

---

### Post by Andy H. on 2009-11-12
Bump

---

### Post by BrokaToe on 2009-11-12
Go to System>Administration>Users and Groups
Here you can select your username and click on properties.
Then there is a box to check that says > Don't ask for password on login

---

### Post by wojox on 2009-11-12
> **BrokaToe said:**
> Go to System>Administration>Users and Groups
Here you can select your username and click on properties.
Then there is a box to check that says > Don't ask for password on login

I've never noticed that before, pretty cool.

---

### Post by Andy H. on 2009-11-12
Thanks for the tip.  I went into Users and Groups as you suggested, selected my account and then went into the Properties. The box for "Don't ask for password on login" was grayed out.  

Any suggestions on how to activate this?

Thanks again,

 -AH

---

### Post by wojox on 2009-11-12
When you first load User Settings Press the keys Click to make changes.

---

### Post by SteveHillier on 2009-11-12
> **wojox said:**
> I've never noticed that before, pretty cool.

I have only seen it in this release.  I assumed it is a new feature.

However I am not sure why we would want to use this.  It isn't a great fag to type in a username and password to gain the benefit of some security.

---

### Post by Andy H. on 2009-11-12
> **wojox said:**
> When you first load User Settings Press the keys Click to make changes.

Wojox,
Thanks but that still doesn't do it.  I opened it up, clicked the keys to make changes, and t was still grayed out.

Steve, 
I'm not using the machine for anything sensitive, and have it an a secure location where the nly one using it is me or my wife.

Any other suggestions on how to activate the checkbox are welcome.

Thanks,

  -AH

---

### Post by jamie.nicholson on 2009-11-15
Hi,

This worked for me,

System > Administration > Login Screen
Click Unlock
Type your password
Click Authenticate
Then select Log in as 'your user'
Then click Ok

The reason the stuff is grey'd out is because you need to unlock and type in your password, in the user groups there are a set of keys (click on them) on the main page to help you unlock that window. However I didn't see any options in the user window to allow me to login.

Maybe you will......

---

### Post by Andy H. on 2009-11-15
Jamie,

 Thanks for the attempt.  I've done what you suggested with the login screen and the users and groups menus and even after clicking the keys to allow changes to be made, authenticating that I have the permissons, etc., the "user settings> properties>account" option "Don't ask for password on login" is still grayed out.

So far, the only thing I can think of is that this is just a bug in the Ubuntu system.  I've spent way more time trying to get the"dummy" option to work than I would've saved eing able to just get on the system w/o logging in each time over the next few years...

If anyone's got other suggestions, I'd appreciate hearing them.

Thanks,

  -AH

---

### Post by Andy H. on 2009-11-17
Bump.

How do I activate the "user settings> properties>account>Don't ask for password on login" option?

Thanks,

  -AH

---

