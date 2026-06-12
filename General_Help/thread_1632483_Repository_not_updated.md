---
title: "Repository not updated"
date: 2010-11-28
forum: General Help
---

### Post by Brian R. on 2010-11-28
I am getting the following error message:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Plus i tried to install google earth which did not work and i am now left with a message that in dpkg that googleearth is listed but has no files, how do i fix this.
Thank you

---

### Post by tajiknomi on 2010-11-28
[SIZE=2]Follow the same threads , which are solved.....

[/SIZE][         1) http://ubuntuforums.org/showthread.php?t=1550877]("http://ubuntuforums.org/showthread.php?t=1550877")

       2)   > [http://ubuntuforums.org/showthread.php?t=924034](http://ubuntuforums.org/showthread.php?t=924034)

---

### Post by karthick87 on 2010-11-28
```
sudo apt-get update
```

---

### Post by sikander3786 on 2010-11-28
Add the missing GPG key by

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

And then,

```
sudo apt-get update
```

Good Luck!

---

### Post by karthick87 on 2010-11-28
Can you explain the first command?

---

### Post by sikander3786 on 2010-11-28
> **karthick87 said:**
> Can you explain the first command?
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

---

### Post by karthick87 on 2010-11-28
Thank you :)

---

### Post by Brian R. on 2010-11-28
Thank you sikander3786 that solved the problem.

---

### Post by sikander3786 on 2010-11-28
Both of you are Welcome :-)

The OP can now mark the thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

---

