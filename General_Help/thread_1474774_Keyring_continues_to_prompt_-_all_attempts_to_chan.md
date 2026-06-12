---
title: "Keyring continues to prompt - all attempts to change have failed - lucid netbook"
date: 2010-05-06
forum: General Help
---

### Post by dBuster on 2010-05-06
Okay folks, Here we go.  I have spent 4 days of searching and trying all tricks to get the keyring prompt when starting up the netbook to not prompt for a password to connect to the wireless network.  

This netbook is for my wife, recent convert from Windows as she was tired of the updates and how long it took to start up the machine.  

Any how, Has anyone been successful in getting the keyring to not prompt for password upon booting up?  I have the user set to auto login and would like the keyring to do so as well.

This was installed from a fresh install just downloaded this past Monday 5/3/2010 of the 10.04 Ubuntu Netbook Remix.

Oh and by the way, I have her login going into gnome so I can add to the panel the weather applet.  Can't make changes when solely in netbook mode.

---

### Post by dBuster on 2010-05-06
Any ideas here, done searching the web and no luck with the tips there.

---

### Post by mikewhatever on 2010-05-06
Usually, just leaving the password fields black the first time you are prompted, does the trick. If you did set the password, remove it, since there is no keyring autologin.
Applications->Accessories->Passwords and Encryption Keys.

---

### Post by dBuster on 2010-05-08
Okay it was so simple that I overlooked it.

I had to enable again, "available to all users" on the wireless configuration and it no longer prompts for password.

Cool beans!

---

### Post by dBuster on 2010-05-11
Okay well that was fine for the first reboot after setting available to all users...  It is back to prompting again for the keyring!  

I have tried to use unsafe and it didn't take my changes, I have tried all I can find but still getting prompted for that keyring!  

Any ideas?

---

### Post by doas777 on 2010-05-11
ok, the problem is that you are autologing in. I won't lecture about that, but if you are not even going to put in a desktop password at all, it makes a lot of sense to not unlock the keyring until after a password is provided.

that said, you can disable the keyring by going to Accessories -> "Passwords and encryption keys" and select "Default". then right click and select "change password". leave both boxes blank, and click ok. the system will ask you if you really want your passwords to remain unecrypted (use unsafe storage). say yes, and you should no longer get popups.

---

### Post by varanasi on 2010-05-11
I don't think the problem is his autologin.  I am logging in, with a password that matches the keyring password, and still getting prompted every time.  Formerly, if the login password matched the keyring, the prompts went away.

---

### Post by doas777 on 2010-05-11
> **varanasi said:**
> I don't think the problem is his autologin.  I am logging in, with a password that matches the keyring password, and still getting prompted every time.  Formerly, if the login password matched the keyring, the prompts went away.
my point was simply that you will never have problems with the keyring (at least not for this usecase) when autologin is disabled. I've also heard of people setting their login password as the "Default" password in "Passwords and Encryption keys" to address the issue.

---

### Post by varanasi on 2010-05-11
> **doas777 said:**
> my point was simply that you will never have problems with the keyring (at least not for this usecase) when autologin is disabled. I've also heard of people setting their login password as the "Default" password in "Passwords and Encryption keys" to address the issue.

I think what you are saying was once true, but may not be true in this version of remix, at least.  I am not using autologin, and I have done the default thing, and I am still being prompted for my password.  (With past versions, I have had the experience you describe.)

So far, I haven't been able to fix it.

---

### Post by doas777 on 2010-05-11
> **varanasi said:**
> I think what you are saying was once true, but may not be true in this version of remix, at least.  I am not using autologin, and I have done the default thing, and I am still being prompted for my password.  (With past versions, I have had the experience you describe.)

So far, I haven't been able to fix it.
oh. well it wouldn't be the first time I've become obsolete.
good luck

---

### Post by varanasi on 2010-05-12
Simple.  I'm a dope.  When the keyring dialog pops up, select the first option.

---

