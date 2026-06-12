---
title: "Problem with kgpg and Enigmail in Thunderbird"
date: 2006-02-10
forum: General Help
---

### Post by Jeff Eklund on 2006-02-10
Hi!
I'm using KDE 3.5.1 and just recently my GPG-key expired, so I thought of creating a new one. And so I did. Using Kgpg. Now it just happens I used non ascii-characters in my passphrase (å, ä, ö) to get more security. Now when I try to sign email using enigmail and my new key, enigmail complains: ```
Send operation aborted:
Error - bad passphrase
gpg command line and output:
/usr/bin/gpg --charset utf8 --batch --no-tty --status-fd 2 --clearsign --digest-algo sha1 -u <my@email.address.org>
gpg: skipped "<my@email.address.org>": bad passphrase
gpg: [stdin]: clearsign failed: bad passphrase
```

Now I know that the passphrase is correct, so I am wondering, could it be something with the encodings? I think that Kubuntu 5.10 is utf8, and enigmail reports using that as an argument for gpg, but thats the only problem I can think of... Anyone?

Thanks in advance,
Jeff

---

