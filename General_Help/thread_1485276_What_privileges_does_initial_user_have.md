---
title: "What privileges does initial user have?"
date: 2010-05-16
forum: General Help
---

### Post by masterridley on 2010-05-16
Guys, I've got the simplest question...

I accidentally promoted my **initial account** to admin and now I want to revert it but I don't remember the specific **initial user privileges**.

So there are 2 questions:

1) First, is it safe to "downgrade" the account, logging in with another one? In general what's the best way to do it?

and

2) Could someone enter Administration->Users and Groups->[select initial account]->
Advanced Settings->User Privileges and list the privileges that are on by default?

I repeat I want the privileges of the initial account, which I suspect are above those of basic users (that are added later) and below admin...

---

### Post by rattskjelke on 2010-05-26
I did the same thing. I wonder why this isn't documented anyplace.
If I decide to reinstall 10.04 I will look up the default user privileges and groups and post it here.

---

### Post by WorMzy on 2010-05-26
What do you mean you promoted it to admin? You mean you added it to the root group? Can't you just remove it from the root group?

Or do you mean you changed the permissions of everything using chmod?

---

### Post by rattskjelke on 2010-05-28
This is what I did:
System/Administration/Users and Groups/Account type

You can choose between Administrator, Desktop User, and Custom.
The default initial user that you create when you install Ubuntu is set to Custom (not Administrator)

We are trying to find out what the default settings are for the default user.
I searched for it but I don't know what it is called and I don't know where it is documented at.
I have no idea what bash commands equate to the System/Administration/Users and Groups/Account type menu.

---

### Post by WorMzy on 2010-05-28
Ah, I see. Here's what my "Advanced Settings" look like:
[[img]http://www.ubuntu-pics.de/thumb/72549/change_advanced_user_settings_035_W93Fyi.png[/img]](http://www.ubuntu-pics.de/bild/72549/change_advanced_user_settings_035_W93Fyi.png)
[[img]http://www.ubuntu-pics.de/thumb/72550/change_advanced_user_settings_037_fDNwx6.png[/img]](http://www.ubuntu-pics.de/bild/72550/change_advanced_user_settings_037_fDNwx6.png)

Hopefully you can use this information to restore your account to it's default state.

I'm also a member of wormzy, adm, dialout, cdrom, plugdev, lpadmin, admin, and sambashare.
Run 'groups' in a terminal to find out which groups you've been added to, in case changing your account type changed them.

Obviously, replace "wormzy" with whatever your account's name is.

---

### Post by jerenept on 2010-05-28
You need to have at least one account with 'Administer the system' checked. I think.

---

### Post by rattskjelke on 2010-05-29
Thank you wormzy.
Jerenept that is correct. I tried to uncheck it and it complained.

---

