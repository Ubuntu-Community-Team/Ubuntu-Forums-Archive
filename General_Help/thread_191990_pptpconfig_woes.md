---
title: "pptpconfig woes"
date: 2006-06-08
forum: General Help
---

### Post by Blackadder on 2006-06-08
So I'm running Dapper 32 bit, and I follow the instructions to install the pptpconfig program, and I get this error:

> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-gtk-pcntl (>= 1.0.0) but it is not going to be installed
E: Broken packages


Googling it, I find there doesn't seem to be anything about this around... can anyone point out why this is happening?

---

### Post by engleb on 2006-06-10
I ran into this same issue.  I was able to get it installed by enabling the Universe repos, running a sudo apt-get update, then doing the sudo apt-get install pptpconfig.  libglade0 is in there and it is what php-gtk-pcntl was looking for when I tried to install it seperately.

I haven't configured it and tried it out yet, but I'm assuming it'll work.

**Update:** after installing this, I am unable to connect using pptpconfig, it appears to hang and errors out.  I haven't had much time to troubleshoot, if anyone else figures this out, please let me know.

---

