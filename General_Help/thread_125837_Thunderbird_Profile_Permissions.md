---
title: "Thunderbird Profile Permissions"
date: 2006-02-05
forum: General Help
---

### Post by Mau on 2006-02-05
I'm trying to setup Thunderbird to work under Kubuntu.  I have copied my profile folder from my backup drive to my thunderbird "home" folder.  

However, when I launch Thunderbird, I first see all my email.  Then, an alert comes up saying something along the lines that it could not initialize the security component.  It tells me to check the permissions.

I click OK, and then Thunderbird tries to download new mail, it tells me to check the permissions again.  It then stops and sits idle without downloading any mail.

So, I went to my profile folder and I right clicked -> properties -> permissions.  Just to see if it was truely a permissions problem, I gave global write access to everything including all sub-folders.  I clicked okay, and Konqueror gave me an alert with text just containing some file.  It did not say anything about this file.  I assume this means that the permissions were not set.

So, how do I get around this?  It seems that there is some problem going from XP to Linux.

---

### Post by aysiu on 2006-02-05
Try this.
Close Thunderbird. 
Open a terminal ```
cp -r ~/.mozilla-thunderbird ~/.mozilla-thunderbird_backup
sudo chmod -R mau:mau ~/.mozilla-thunderbird
```

If you're using the Mozilla (not Ubuntu) version of Thunderbird, do this instead: ```
cp -r ~/.thunderbird ~/.thunderbird_backup
sudo chmod -R mau:mau ~/.thunderbird
```

---

### Post by Mau on 2006-02-05
Hmm, it's telling me this: ```
carl@carl:~$ sudo chmod -R carl:carl  ~/.thunderbird
chmod: invalid mode string: `carl:carl'
```

I installed Thunderbird oddly (or at least I think so - coming from Windows and OSX, I don't quite understand application installation yet).  I first installed Thunderbird 1.0.7 from Adept, and then downloaded 1.5 from Mozilla and installed that via the wiki instructions.  I'm migrating 1.5 Windows -> 1.5 Ubuntu.

EDIT: Doing this produced no error, but it still doesn't work: ```
carl@carl:~$ sudo chown  -R carl:carl  ~/.thunderbird

```

---

### Post by Mau on 2006-02-05
Okay - I think I fixed the problem.  I just went in and applied the permissions to each second level file and folder and -- it worked!

A little odd.  Perhaps a bug?

---

