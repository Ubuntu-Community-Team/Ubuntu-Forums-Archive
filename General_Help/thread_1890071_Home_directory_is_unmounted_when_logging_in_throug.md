---
title: "Home directory is unmounted when logging in through ssh with keys"
date: 2011-12-02
forum: General Help
---

### Post by Efficacy on 2011-12-02
Hey guys, I haven't been able to find anything by searching, so I thought I'd ask here.

Basically the situation is as follows: when I ssh into my machine at home either over LAN or through the internet, my home directory is unmounted to protect my data. This started when I updated my keys due to an unrelated incident. It worked fine the first couple of logins, and now whenever I use them, I can still login just fine... but my home directory is not accessible. Now, I can decrypt it just fine using ecryptfs-add-passphrase, and then putting in the string of values generated when I encrypted it in the first place, but that takes a rather long time and is inconvenient to say the least.

If I ssh in using my password (no key), everything works fine as it always has. I can see all the files in my home folder.

Have I just overlooked something simple or do you have any suggestions for fixing it?

note: My authorized keys file is NOT in my home directory, and as I said I can login to the machine just fine using keys, I just don't have access to my files. If I ssh with a password instead of a key, everything is great.

---

