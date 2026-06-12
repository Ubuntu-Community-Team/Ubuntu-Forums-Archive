---
title: "what is .ecryptfs and why is is making my home folder twice as big?"
date: 2010-12-13
forum: General Help
---

### Post by zedadex on 2010-12-13
[COLOR="DimGray"]***Please Note: I am a new user. This is literally my first post.** Taking into account the "search before you post" rule, I searched ".ecryptfs delete" but did not find a suitable answer to my query.*[/COLOR] :confused:

So I created a very small partition (about 10GB) for running Ubuntu as an emergency/backup OS. While installing, I checked the "encrypt home directory" checkbox. 

Now, however, I have my home folder sized at 2.8GB when there's only 1.4GB of data in my user folder. The other 1.4GB are stored in ".ecryptfs" (which I assume is the encrypted form of my data) I assume that my user folder only shows up (decrypted) after I log in or something, which is why I see two 1.4GB folders in my home folder (my user folder and ecryptfs). However, I'd prefer my home folder to NOT be twice as big as my actual user data, just because of encryption...

**So I guess my question is,** what is ".ecryptfs"? What part does it play in encryption? Why does it double the size of my home directory? And most importantly, **can I safely disable it?**

[COLOR="DimGray"]Other related queries i have (have not searched for these yet, they just relate to this question):
[LIST]
[*] How can i move the home directory to a separate partition?
[*] Assuming the home directory is in a separate partition, how big should the linux partition be?
[/LIST][/COLOR]
Thanks for your time and help! :D

---

### Post by loonytune on 2011-06-21
having the same problem. any news?

---

### Post by dandnsmith on 2011-06-21
Have you tried [this helpful exposition](https://help.ubuntu.com/community/EncryptedPrivateDirectory)?
I haven't tried this beast myself (the encryption), but think it might hold all the clues.

HTH

---

