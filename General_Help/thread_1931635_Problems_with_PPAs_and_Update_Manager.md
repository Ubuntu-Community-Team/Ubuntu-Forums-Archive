---
title: "Problems with PPAs and Update Manager"
date: 2012-02-25
forum: General Help
---

### Post by A4orce84 on 2012-02-25
Hey Guys,

So I recently started receiving some errors when I go into update manager. It seems I have some failed PPAs, specifically:
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I know especially the last one (naturalscrolling) was an application that did not work correctly (only worked on Ubuntu 11.04 / 11.10, and I'm rocking 10.10) and I tried removing the PPA with the following command:

```
aahmad@aahmad-lt:~$ sudo add-apt-repository -r ppa:zedtux/naturalscrolling 
Error: 'deb http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu maverick main' doesn't exist in a sourcelist file
```

But it still shows up in the update-manager list as you can see above. I tried a few other things to clear it out, but I'm still getting the error message when I update.

Am I doing something incorrectly? Also how do I clean up other "official Ubuntu" PPAs?

Thanks in advance!

--Asif

---

### Post by UltimateCat on 2012-02-25
I once had to pick apart every PPA in the repositories to figure out which one was the problem.  Not sure if that might be your case but it could be a start.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Also; you could uninstall Update Manager and reinstall and see if that helps.

I uninstalled and reinstalled because I had a broken dependency.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

---

### Post by A4orce84 on 2012-02-25
I believe it started after I installed the naturalscrolling PPA. Is there any other easier method?

---

