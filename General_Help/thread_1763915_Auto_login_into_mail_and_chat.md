---
title: "Auto login into mail and chat"
date: 2011-05-21
forum: General Help
---

### Post by kirill578 on 2011-05-21
Is it possible to make Ubuntu login into my mail account and chat accounts on the startup?

---

### Post by sj1410 on 2011-05-21
what are you using for email and chat

you can save the account password and put that application to autostartup

---

### Post by kirill578 on 2011-05-21
> **sj1410 said:**
> what are you using for email and chat

you can save the account password and put that application to autostartup

I am using the defualt chat for ubuntu 11.04 
And my mail client is Evolution but I'd like to swith it to Thunderbird

---

### Post by prshah on 2011-05-21
> **kirill578 said:**
> Is it possible to make Ubuntu login into my mail account and chat accounts on the startup?

Yes; look for the little "envelope" icon next to the clock. You can click that, and setup your email, chat and broadcast (Eg twitter) accounts.

Subsequently, you will be automatically connected every logon after you unlock your keyring.

---

### Post by kirill578 on 2011-05-21
> **prshah said:**
> Yes; look for the little "envelope" icon next to the clock. You can click that, and setup your email, chat and broadcast (Eg twitter) accounts.

Subsequently, you will be automatically connected every logon after you unlock your keyring.


yes, I know but the chat account doesn't login automatically on startup

---

### Post by prshah on 2011-05-21
> **kirill578 said:**
> yes, I know but the chat account doesn't login automatically on startup

In the IM client window (Empathy), please check if Edit-Preferences-Automatically connect on startup is checked.

---

### Post by rayne127 on 2011-05-25
> **prshah said:**
> In the IM client window (Empathy), please check if Edit-Preferences-Automatically connect on startup is checked.

I have this check in my Empathy and it does not automatically sign in when I start up my computer and unlock my keyring...

---

### Post by prshah on 2011-05-25
> **rayne127 said:**
> I have this check in my Empathy and it does not automatically sign in when I start up my computer and unlock my keyring...

Then just add empathy in your startup programs. System, Preferences, Startup Applications.

---

### Post by Bigfootr on 2011-06-30
I have this same exact problem, and the help in this thread didn't work.

---

### Post by muxical on 2011-09-01
$ crontab -e

@reboot /usr/bin/nohup /usr/bin/nice /usr/bin/empathy -h &
(then save and quit)

---

