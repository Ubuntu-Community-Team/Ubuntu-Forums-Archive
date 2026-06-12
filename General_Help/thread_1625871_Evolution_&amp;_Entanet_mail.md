---
title: "Evolution &amp; Entanet mail"
date: 2010-11-19
forum: General Help
---

### Post by ibod on 2010-11-19
I  am trying to resolve a problem for a friend, setting up evolution on ubuntu 10.4
(also same problem on my ubuntu 9.10)

I have set up evolution and it wont connect to the server 

I have looked in google and searched the forum for anything to do with enta mail and evolution and can't find any thing that helps 

I spoke to the ISP and they tell me that their server dose not require authentication when connected via their service. Both my friend and I  are connected by their service.

I have clicked on the "Check for supported types" under Authentication Type on the POP page  and it strikes through all but 'password' so I have to set that because there is no 'NONE' option

I have not ticked the 'server requires authentication' under SMTP so that should be ok if i can get the POP to work.

The error is 

```

Unable to connect to POP server pop.enta.net.
Error sending password: - ERR Login failed.

```Any suggestion welcome.

---

### Post by dcstar on 2010-11-19
> **ibod said:**
> I  am trying to resolve a problem for a friend, setting up evolution on ubuntu 10.4
(also same problem on my ubuntu 9.10)

I have set up evolution and it wont connect to the server 

I have looked in google and searched the forum for anything to do with enta mail and evolution and can't find any thing that helps 

I spoke to the ISP and they tell me that **their server doee not require authentication when connected via their service**.
........

No, you **should** require a POP password for your account.

Your POP user name should be set in the Account, and the "Remember Password" box should be set.

When connecting you should be prompted for the POP password, and when you enter it correctly it should not prompt you again.

You can manually test the POP login with the following (change the obvious stuff marked by the < >):
```
telnet <pop-mailserver-name.com> 110
user <your-POP-user-name>
pass <your-POP-password>
list
quit
```

---

### Post by ibod on 2011-02-18
After a lot of random problems with this email set-up including the above and even the ADSL disconnecting when sending mail.

I found the real problem.

There was a fault in the router that only showed up when using the default mail port.

Router now binned and a replacement installed and all the mail problems have gone away

---

