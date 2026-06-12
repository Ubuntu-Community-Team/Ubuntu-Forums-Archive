---
title: "CHMOD help"
date: 2011-09-09
forum: General Help
---

### Post by Colo2 on 2011-09-09
Hey all

I'm creating multiple users for my SSH server, and I need to make each home directory ONLY accessible to each user,

So user "john" can ONLY access /home/john/ and not /home/bob/

Any ideas how i'd chmod the folders, or add permissions or something?

Thanks

Tom

---

### Post by searchfgold6789 on 2011-09-09
Yeah. Classically, you would do this by right-clicking the folder, going to Properties, and clicking the Permissions tab. Then, you have two drop down menus, one for $USER, and one for others. You can select the correct combination yourself, and then click OK or whatever.

---

### Post by Colo2 on 2011-09-09
Hey

Thanks for the reply :)

Yeah, that's how I'd usually do it, problem is, this time I'm working without a GUI.

Tom

---

### Post by haqking on 2011-09-09
> **Colo2 said:**
> Hey all

I'm creating multiple users for my SSH server, and I need to make each home directory ONLY accessible to each user,

So user "john" can ONLY access /home/john/ and not /home/bob/

Any ideas how i'd chmod the folders, or add permissions or something?

Thanks

Tom


see here [https://help.ubuntu.com/11.04/serverguide/C/user-management.html](https://help.ubuntu.com/11.04/serverguide/C/user-management.html)

and scroll down to the user profile security section.

rather than me type commands out and not be exactly what you need.

you coudl also encrypt the home folders also

---

### Post by Colo2 on 2011-09-09
Thank you :) ill take a look at that.

---

