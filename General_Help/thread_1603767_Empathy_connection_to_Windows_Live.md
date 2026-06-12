---
title: "Empathy connection to Windows Live"
date: 2010-10-23
forum: General Help
---

### Post by Oxwivi on 2010-10-23
I'm not connecting to Windows Live server through Empathy since the last couple of days, but I can easily sign in web-based IM messengers like Trillian. Any ideas?

---

### Post by howefield on 2010-10-23
Try the instructions in this post..

[http://ubuntuforums.org/showpost.php?p=10003289&postcount=17](http://ubuntuforums.org/showpost.php?p=10003289&postcount=17)

---

### Post by yetiman64 on 2010-10-23
The package telepathy-butterfly is the culprit though I don't know why.

Had the same problem here and fixed it with (1st remove your account in Empathy) then in terminal,

```
sudo apt-get remove telepathy-butterfly
``` telepathy butterfly is described as "MSN connection manager for telepathy" in synaptic (search for it there if you need to check it out - highlight it and check the properies info).

Once removed log out and then back in, start Empathy and reset up your account, it should then work.

Note I got this info from another thread in here, but can't find it at the moment (<removed request for link>, I didn't post there and forget how it was named.)

[B]Edit: Try howiefields post 1st that sounds like more up to date information !

Edit2: [/B]Just reinstalled telepathy-butterfly and ran the fix in the link howiefield posted. I could not find the faulty line. But noted the new one is in there. It appears the official fix is already in place.

---

### Post by Oxwivi on 2010-10-23
The post howefield referred to worked, perfectly, thanks! Which reminds me I did not search, I'm ashamed...

---

### Post by Oxwivi on 2010-10-24
The problem is recurring! I checked that file again, and the solution is still in place yet I'm having problems signing in again!

---

### Post by Oxwivi on 2010-10-24
It worked itself out after rebooting...

---

### Post by pjalegria on 2010-10-24
Install msn-pecan...:guitar:

---

### Post by Oxwivi on 2010-10-24
The less programs, the better - it's a 10 GB HDD I'm using. Besides, I use more than MSN, don't want multiple icons in the notification area, it'll be a pain...

---

### Post by crooks_dwayne on 2010-12-05
Thanks alot. I was having this problem and the fix worked for me on Ubuntu 9.10 (Karmic Koala).

---

### Post by Ruja on 2011-12-07
> **yetiman64 said:**
> The package telepathy-butterfly is the culprit though I don't know why.

I'm posting here because I reached this post when I searched for a solution.

I'm using Ubuntu 11.10. Empathy would not log in to Windows Live Messenger. So I did more or less as yetiman said:

1. Removed my Live account.
2. Typed the following code into Terminal (upgrade instead of remove):
```
sudo apt-get upgrade telepathy-butterfly
```3. Added my Live account and it worked.

---

