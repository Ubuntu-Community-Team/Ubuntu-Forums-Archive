---
title: "MSCore Fonts Installer Issue"
date: 2009-08-24
forum: General Help
---

### Post by gb2k01 on 2009-08-24
I've been having this error message pop up after every installation I do, and when I do installations, it always hangs up at the "ttf-mscorefonts-installer" for a few minutes, while it tries to find the missing font.

E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1
E: msttcorefonts: dependency problems - leaving unconfigured

I've tried re-installing the 'restricted extras' package (this error happened during that installation) as well as the 'Microsoft Core Fonts' package, but the problem persisted during both of those.

Any help would be really appreciated, it is a minor problem but it's rather annoying (unless it somehow majorly affects my installations, then I'm a bit worried!). Thanks in advance!

---

### Post by oldos2er on 2009-08-24
Make sure you have the multiverse repository enabled (System, Administration, Software Sources). Then run ```
 sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by gb2k01 on 2009-08-25
Hello!

Thank you for your quick reply, unfortunately, it didn't work so well.. looking into the terminal window, it may be a server-side issue, but just for one font:

```
--2009-08-26 01:20:51--  http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2009-08-26 01:20:51--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-08-26 01:20:52--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

```

And then this error appeared at the end again:

```
arial32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on ttf-mscorefonts-installer; however:
  Package ttf-mscorefonts-installer is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 ttf-mscorefonts-installer
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How weird. I guess best bet may be to try and find it someplace else available online?

Thanks again for your earlier help, though, I appreciate it!!!:)

---

### Post by oldos2er on 2009-08-25
You could try changing servers, via menus System, Administration, Software Sources, Download from, Other, Select Best Server.

---

### Post by mcduck on 2009-08-25
> **oldos2er said:**
> You could try changing servers, via menus System, Administration, Software Sources, Download from, Other, Select Best Server.

That won't help, since the problem is not with downloading the package itself from repositories.

Instead the connection times out when that package tries to get the fonts from sourceforge.net. (the fonts are not included in the package, it's just an installer script that downloads the fonts for you).

Anyway, I just tried to download the font that caused the error and it's there and works fine. So most likely there was some problem with the server/file that's already been fixed and thus installing that package should work now.

---

### Post by oldos2er on 2009-08-25
Thanks for the correction.

---

### Post by gb2k01 on 2009-08-26
That did the trick, now the error isn't showing up anymore! :)

Thanks a lot for both of your help, hope you both have a nice day!

---

