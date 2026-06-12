---
title: "Ubuntu Server 10.10 need login locally after boot up, or I cannot login remotely."
date: 2010-11-21
forum: General Help
---

### Post by koalainb on 2010-11-21
**[COLOR="Red"][resolved][/COLOR]**
Everytime I restart the computer, I need plug a keyborad and input the username(any valid username) and password. How to resolve this problem? It's painful!

---

### Post by papibe on 2010-11-21
Some old hardware doesn't boot well without a keyboard connected.

Nevertheless, there's a few tricks you can try. Go into the BIOS and look for an option like "server operation", or "keyboardless option", etc (my P4 IBM has that last option). Also, disable all network booting protocols like PXE or RIPL. Sometime the lack of keyboard or monitor triggers PXE.

Last option: you can buy a super extra cheap keyboard at your local brick-and-mortar store for a few bucks, and let it connected.

If your server boots well, it should be NOT necessary to log in to use ssh.

Regards.

---

### Post by asmoore82 on 2010-11-22
Check the "Perfect Headless Server" link in my signature.

---

### Post by koalainb on 2010-11-22
> **papibe said:**
> Some old hardware don't boot well without a keyboard connected.

Nevertheless, there's a few tricks you can try. Go into the BIOS and look for an option like "server operation", or "keyboardless option", etc (my P4 IBM has that last option). Also, disable all network booting protocols like PXE or RIPL. Sometime the lack of keyboard or monitor triggers PXE.

Last option: you can buy a super extra cheap keyboard at your local brick-and-mortar store for a few bucks, and let it connected.

If your server boots well, it should be NOT necessary to log in to use ssh.

Regards.

Yes, If I plug a keyboard before start the computer, ubuntu would 
run and all startup services would start, and I can connect to ubuntu remotely. Though a login: is displayed if a moniter is connected(In fact, it would appear no matter whether there is a moniter), but there is not need to login before you use ubuntu. 

So, the only inconvenience is that I need an extra keyborad.
My Computer is DELL Inspiron 560S, It seems there is no "keyboardless option". I would find a way to disable keyboard detect when startup for my DELL Inspiron 560S.

---

### Post by koalainb on 2010-11-22
I found how to disable keyboard error report in DELL Inspiron:
Press F2, and then ...
Boot Device Configuration
 -> Boot Settings Configuration
   -> Keyboard Errors  => [Do Not Report]

---

### Post by dcstar on 2010-11-22
> **koalainb said:**
> I found how to disable keyboard error report in DELL Inspiron:
Press F2, and then ...
Boot Device Configuration
 -> Boot Settings Configuration
   -> Keyboard Errors  => [Do Not Report]

So it is **Solved** then?

---

### Post by koalainb on 2010-11-24
> **dcstar said:**
> So it is **Solved** then?

Yes, solved.

---

### Post by dcstar on 2010-11-24
> **koalainb said:**
> Yes, solved.

Then MARK THE THREAD!

---

