---
title: "Evolution Password?"
date: 2010-05-15
forum: General Help
---

### Post by WolfRage on 2010-05-15
I am trying to convert from Thunderbird to Evolution; because I want a better calendar application and I want more seamless integration with my desktop. But I found no way to convert Thunderbird email into Evolution; still I am going forward and starting fresh with the email accounts in Evolution. 
My current problem is that I try to "Send/Receive" but evolution has never asked me for my password and it still has not. That is why I believe that it is failing. How do I give it my password?

---

### Post by howefield on 2010-05-15
> **WolfRage said:**
> But I found no way to convert Thunderbird email into Evolution

Try this thread...

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_migrate_from_Thunderbird_to_Evolution](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_migrate_from_Thunderbird_to_Evolution)
 
> My current problem is that I try to "Send/Receive" but evolution has never asked me for my password and it still has not. 

You should be prompted for the password the first time Evolution tries to receive mail from the server, immediately after creating the account.

If this isn't the case, I'd close Evolution and restart, see if it prompts for a password, failing that, delete and recreate the account.

---

### Post by WolfRage on 2010-05-15
Turns out it was the way I was connecting. I was using TLS but that is only supported for SMTP not POP. Switched to SSL and problem solved. Thank you for your help and your link. Working that now.

---

### Post by dakkar9999 on 2010-05-17
I also have a problem with Evolution not remembering the passwords.  Usually, the gmail accounts are ok, but very often Evolution ask my regular e-mail account password.  It doesn't seem to be able to remember...

Any ideas?

---

### Post by WolfRage on 2010-05-18
From what I saw in other post and of what I understand of Evolution. The passwords are stored in your GNOME Key Ring. So you may have do delete your key ring. Only advisable if you only have GNOME storing passwords that you know. But according to other posts that Should reset it and should fix the problem of Evolution forgetting.

---

### Post by zer010 on 2010-12-06
I've been having this problem as well.  Evolution seems to forget my @live.com passwords every now and then, but it does fine with my @gmail.com accounts.  A bug perhaps?

---

