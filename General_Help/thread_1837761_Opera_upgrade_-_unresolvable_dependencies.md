---
title: "Opera upgrade - unresolvable dependencies"
date: 2011-09-02
forum: General Help
---

### Post by heyup on 2011-09-02
I have Opera 11.50 installed. When I mark it for upgrade using Synaptic Package Manager, I get an error message:

> The following packages have unresolved dependencies. Make sure all required repositories are added and enabled in preferences.

opera: 
  Depends: libfontconfig1 (>=2.8.0) but 2.5.0-2ubuntu3 is to be installed 
  Depends: libglib2.0-0 (>=2.24.0) but 2.16.6-0ubuntu1.2 is to be installed

   

I cannot work out how to solve this. Opera is enabled in Software Sources.

---

### Post by Frogs Hair on 2011-09-02
Strange , mine updated automatically to 11.51 via the  update manager yesterday . I have always received  automatic updates for Opera stable versions without a PPA .

---

### Post by Duncan Williams on 2011-09-02
re-install from manufacturers site:
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

this should add the right ppa.

---

### Post by heyup on 2011-09-02
> **Duncan Williams said:**
> re-install from manufacturers site:
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

this should add the right ppa.

I removed Opera 11.50 and tried to re-install Opera 11.51 from both Synaptic Package Manager and the Opera website, but I'm unable to do so because the installer gives error message about unresolved dependency libfontconfig1.

I have been able to install Opera 11.10 (which I'm now using), but cannot install Opera 11.51 due to unresolvable dependencies.

If I completely remove Opera 11.51 (including config files) will that solve the dependency problem?

I'm on Hardy Heron.

---

### Post by Duncan Williams on 2011-09-03
You might need to do a clean install.
Opera will read info from previous installs.
If something is missing, then you may have an issue.

Some info here:
[http://www.wilderssecurity.com/archive/index.php/t-271821.html](http://www.wilderssecurity.com/archive/index.php/t-271821.html)

---

### Post by ruario on 2011-09-13
Hi I am an Opera employee. ;)

We don't actually support Hardy anymore because Canonical dropped support for it when run as a desktop on 2011-05-12 (yes I know it is still supported as a server).

Nonetheless we will look at this issue as it also affects Debian Lenny, which is still supported by The Debian Project.

I have made test repacks of Opera 11.51 that will now install on Lenny. You may wish to also try these on your own system. More details here:

[http://my.opera.com/ruario/blog/2011/09/13/problems-installing-opera-11-51-on-debian-5-0-lenny-or-mepis-8](http://my.opera.com/ruario/blog/2011/09/13/problems-installing-opera-11-51-on-debian-5-0-lenny-or-mepis-8)

---

### Post by ruario on 2011-09-13
On second thoughts, I can see that the libfontconfig1 version I set in my repack is still too high for you. I never considered Hardy only Lenny.

In that case I you may want uninstall Opera via apt or dpkg and then install one of the Opera tar packages, which do not dependency checking.

Details of how to install from one of our tar packages are provided here:
[http://my.opera.com/ruario/blog/selecting-a-linux-or-freebsd-package-and-installing-it](http://my.opera.com/ruario/blog/selecting-a-linux-or-freebsd-package-and-installing-it)
(Don't worry we include an uninstall script should you need to remove Opera later)

Alternatively, you could repackage Opera yourself and knock down the libfontconfig1 version even lower or you force install via 'dpkg --install --force-depends operapackagename'

---

### Post by ruario on 2011-09-13
> **ruario said:**
> Alternatively, you could repackage Opera yourself and knock down the libfontconfig1 version even lower or you force install via 'dpkg --install --force-depends operapackagename'

Ah, what the hell. I have repacked them again for you so that they should install on Hardy ;)

[32bit Opera](http://people.opera.com/ruario/repack/opera_11.51.1087-1_i386.deb)
[64bit Opera](http://people.opera.com/ruario/repack/opera_11.51.1087-1_amd64.deb)

---

### Post by heyup on 2011-09-13
ruario

Thanks for your input.

I thought the unresolvable dependency problem might be a Hardy issue.

---

### Post by ruario on 2011-09-20
We have now updated the Opera 11.51 package stored in our repository with corrected dependencies.

---

### Post by Duncan Williams on 2011-09-21
good stuff, ruario

---

### Post by heyup on 2011-09-22
Excellent. Thank you.

---

