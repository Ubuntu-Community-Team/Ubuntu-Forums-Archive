---
title: "How can standard users change their own password?"
date: 2012-06-30
forum: General Help
---

### Post by AleveSicofante on 2012-06-30
It's been a while since I used Ubuntu regularly (pre Unity). Now I'm setting a laptop for my parents. I don't want them to be sudoers but I want to give them some privacy.

I vaguely remember there was something like an "About me" menu where the user could change its own picture, full name, password and other features that are their sole responsibility.

I can't find anything close to that "About me" thing in Unity. How can standard users do those things now?

---

### Post by nothingspecial on 2012-06-30
Prefix changed from lubuntu to ubuntu.

---

### Post by GreatDanton on 2012-06-30
What you are looking for it's under System Settings, User Accounts.

When you get there you can add or delete accounts. Under Account type you can choose between types of user (Administrator or in your case you want to set up Standard account).

Kind regards.

---

### Post by AleveSicofante on 2012-07-01
> **GreatDanton said:**
> What you are looking for it's under System Settings, User Accounts.

When you get there you can add or delete accounts. Under Account type you can choose between types of user (Administrator or in your case you want to set up Standard account).

Maybe I didn't make myself clear, so let me explain again:

My parents accounts have been already set. They are standard users, not administrators. They want to set up their own account's password, picture and real name. They can't do that using System Settings as any change there requires admin privileges, which they don't have and won't get.

The former "About me" menu entry allowed ANY standard user to make changes to these details on their own account. How is this solved now?

---

### Post by AleveSicofante on 2012-07-01
> **nothingspecial said:**
> Prefix changed from lubuntu to ubuntu.
Sorry. My mistake. Thanks for fixing it.

---

### Post by Cheesemill on 2012-07-01
Going to System Settings > User Accounts will let any user change their own information without prompting for a password, I've just tested it with a normal user on my system.

---

### Post by GreatDanton on 2012-07-02
> **Cheesemill said:**
> Going to System Settings > User Accounts will let any user change their own information without prompting for a password, I've just tested it with a normal user on my system.

That's right. 

@AleveSicofante: Did you upgrade or made a fresh install?

---

### Post by AleveSicofante on 2012-07-02
OK. I've seen there's a bug here.

The user was created with an empty password and that seems to be the problem, since I can't change it even if unlocking the System Settings with my admin password.

Will have to check it further and/or file a bug report.

Thanks for your help.

EDIT: I DO can change the password if I'm logged in with my own admin account. [SIZE=3]**Now that I changed the password to a non-empty one, the standard user can also change the password, so the bug is "Can't change en empty password as standard user".**[/SIZE]

---

### Post by AleveSicofante on 2012-07-02
> **GreatDanton said:**
> That's right. 

@AleveSicofante: Did you upgrade or made a fresh install?
Fresh install.

---

