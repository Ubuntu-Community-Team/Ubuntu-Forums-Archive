---
title: "Profiles transfer for Firefox and Thunderbird"
date: 2012-09-01
forum: General Help
---

### Post by ravenkrane on 2012-09-01
Good evening all! :)

I've just installed Ubuntu on my new HP laptop, but my old computer was a MacBook. 
I'd like to know if anyone knows if I can transfer my Mac Firefox and Thunderbird profiles onto the Ubuntu ones? 

There is so much on them that I can't really afford to lose everything or retype all the saved logins and passwords... 

If there is a way I'd also like to know how or where I can find the applications files (for Firefox and Thunderbird, but for other applications that have them). 

Thank you very much for your help.

Cheers,
Raven.

---

### Post by Habitual on 2012-09-01
```
cp -pr ~/.mozilla /path/to/usb/or/other/media
cp -pr ~/.thunderbird /path/to/usb/or/other/media
```

copy them back to your ~ directory on new host.

---

### Post by ravenkrane on 2012-09-01
Thank you for your answer!

But when I type either of those in the Terminal, it tells me that there is no such file or directory...

---

### Post by oldfred on 2012-09-01
I do not know where the files  are on a Mac.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by ravenkrane on 2012-09-01
I know where they are on Mac, it's finding them on Ubuntu that is posing me a problem... ;)

---

### Post by oldfred on 2012-09-01
Start Firefox & Thunderbird once and it will create the default folders and profile.ini. Then you can copy your versions into those folders and update profile.ini with your XXXXX.default.

Locations should be as Habitual posted above.

Mine Not sure why I have crash Reports & it looks like my copied one from 2009 as I keep reusing the old one,  has slightly wrong permissions, but works. My actual XXX.default is else where in a data partition so I can share it with many installs.:
```
fred@fred-Precise:~/.thunderbird$ ls -l
total 16
drwx------ 3 fred fred 4096 Aug 31 15:19 Crash Reports
-rw-rw-r-- 1 fred fred   94 Apr 18 15:39 profiles1204.ini
-rw-r--r-- 1 fred fred  151 Nov 25  2009 profiles.ini
drwx------ 4 fred fred 4096 Apr 18 15:40 qbugvibk.default
```

---

### Post by ravenkrane on 2012-09-01
Thank you!
I will do that once I've resolved the wireless connection problem I have.

---

