---
title: "Wireless vs KeyRing"
date: 2011-06-29
forum: General Help
---

### Post by OldManRiver on 2011-06-29
All,

I have this U box that can only connect wireless and constantly I battle with key-ring on this box.  Last night, in the middle of it uploading, the key ring corrupted the wireless connect, so I have to remove all my wireless connect sessions and rebuild the one that connect, but now when the machine boots, I not only get the annoying "keyRing Login" but now also get prompted to:

Deny,
Allow Once,
Always allow.

If I select anything but Allow Once, I'm toast on the internet.

I want to fix this %$#$@#%%$# Key ring thing once and for all.  To me it is an intrusive, unneeded, bothersome piece of crap.  If it has a useful purpose, which I can not even find a def of what it does; would someone explain any nessity to me?

I've tried 4 times now to remove it to no avail, so how is that done?

If it needs to remain, it needs to work right, so how is that done?

Thanks!

OMR

---

### Post by gandaran on 2011-06-29
use a blank password to set the keyring password but you will have to remove the existing keyring in passwords and encryption keys before you can do that then it wont bother you again.

---

### Post by OldManRiver on 2011-07-15
> **gandaran said:**
> use a blank password to set the keyring password but you will have to remove the existing keyring in passwords and encryption keys before you can do that then it wont bother you again.

Since I never installed this piece of %$#@#$@$%# keyring crap, have no idea what you are talking about.  It somehow installed itself, without my consent, so details are really needed and have no idea even what the %#$#$@#@##$%%$# it does.

Unless there is a prevailing reason, like security, do not want it and do not need it, but it will not remove, as I have tried.

Thanks!

OMR

---

### Post by MDguy on 2011-07-15
Keyrings come with Ubuntu by default; they encrypt passwords you want to store. If you remove the keyring password, then your computer will store the passwords in plain text, which may be unsecure.
 
However, if you still want to remove it, follow these steps:
 
1. Open "Passwords and Encryption Keys". If you are using 11.04/Unity, you can search for it in the dash.
2. Find the keyring named "default", and delete it.
3. Log out and back in again. 
4. You will be prompted for your WiFi Password. Enter it.
5. You will be prompted for a new keyring password. **Leave this password blank.**
6. When asked if you are sure you want to use unsafe storage, click "Use unsafe storage".
7. Log out and back in, and your computer should connect to wifi automatically.

---

### Post by OldManRiver on 2011-08-23
> **MDguy said:**
> Keyrings come with Ubuntu by default; they encrypt passwords you want to store. If you remove the keyring password, then your computer will store the passwords in plain text, which may be unsecure.
 
However, if you still want to remove it, follow these steps:
 
1. Open "Passwords and Encryption Keys". If you are using 11.04/Unity, you can search for it in the dash.
2. Find the keyring named "default", and delete it.
3. Log out and back in again. 
4. You will be prompted for your WiFi Password. Enter it.
5. You will be prompted for a new keyring password. **Leave this password blank.**
6. When asked if you are sure you want to use unsafe storage, click "Use unsafe storage".
7. Log out and back in, and your computer should connect to wifi automatically.

Great, got rid of it but now Network Manager prompts me 50 times (exaggerating) to get anything on the network done.  What a crock of crap!

Put it back in to take this #$%^$$#@ prompts to a min.  Why doesn't the @##$$%^%$$ crap program read the dang passwords file for my user and leave me the crap alone.

Thanks!

OMR

---

### Post by bkratz on 2011-08-23
Just read this interesting thread about the keyring

[http://ubuntuforums.org/showpost.php?p=10770999&postcount=7](http://ubuntuforums.org/showpost.php?p=10770999&postcount=7)

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #25 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

