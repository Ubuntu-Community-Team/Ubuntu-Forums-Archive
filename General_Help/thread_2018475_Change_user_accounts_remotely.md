---
title: "Change user accounts remotely"
date: 2012-07-06
forum: General Help
---

### Post by Cursed Lemon on 2012-07-06
Hi everyone. 

So, I've been trying to do some user modification on a computer off-site here. The computer is running 11.04. The issue is that there are five user accounts on the computer, but the people trying to log into it can only see three of them. Here is what I see using Freenx:

[IMG]http://i50.tinypic.com/121razb.png[/IMG]

Problem with Freenx is that I can't click a lot of the buttons I see, so I can't actually make changes. Is there any way to change these user settings via command line? I want to have "Amy" and "guests" be the only active accounts, but it seems that the people trying to log in can only see the grey-colored accounts.

---

### Post by btindie on 2012-07-06
It sounds as if the account for Amy and Guest are disabled, you're better of verifying this by the command line.
```
 sudo passwd -S <username>
```>        -S, --status
           Display account status information. The status information consists
           of 7 fields. The first field is the user's login name. The second
           field indicates if the user account has a locked password (L), has
           no password (NP), or has a usable password (P). The third field
           gives the date of the last password change. The next four fields
           are the minimum age, maximum age, warning period, and inactivity
           period for the password. These ages are expressed in days.If the 2nd field is an 'L' then the account is locked, you can unlock it by passing the --unlock option to passwd. Also check that there's actually a passwd set for the account.

---

### Post by Cursed Lemon on 2012-07-06
> **btindie said:**
> It sounds as if the account for Amy and Guest are disabled, you're better of verifying this by the command line.
```
 sudo passwd -S <username>
```If the 2nd field is an 'L' then the account is locked, you can unlock it by passing the --unlock option to passwd. Also check that there's actually a passwd set for the account.

The second field is "P", so that's a little strange.

---

