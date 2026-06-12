---
title: "Broken packages"
date: 2006-02-12
forum: General Help
---

### Post by KevNice on 2006-02-12
Hi again all,

I have a broken package on my system. Ive gotten the following errors in Synaptic:

When I try to reload the package manager, I get this message:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


Then, I go into the package manager, filter for the broken package, and fix. In the bottom, the "broken packages" changes from 1 to 0, and then there is an update to install. The file name is "lilypond"(version 2.6.3-9~breezy1). I go to install it, and then get the following message: 

E: /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb: subprocess pre-installation script returned error exit status 1


When I do the sudo apt-get command in Terminal, it lists the lilypond thing, and tells me to -f install. I run f-install, and hit yes, and I get this: 

Preconfiguring packages ...
(Reading database ... 70008 files and directories currently installed.)
Unpacking lilypond (from .../lilypond_2.6.3-9~breezy1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 19: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Whats going on here? Is it a defective package, should I just remove it? and if so, whats the command?

Thanks!

---

### Post by dcstar on 2006-02-12
[QUOTE=KevNice]Hi again all,

I have a broken package on my system. Ive gotten the following errors in Synaptic:
.......
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Whats going on here? Is it a defective package, should I just remove it? and if so, whats the command?

Thanks![/QUOTE]
Delete the package in the cache (it could be corrupted) and use Synaptic to install it again.

---

### Post by KevNice on 2006-02-12
Ok, I deleted the lilypond file from the cache. and I clicked "fix broken depencies " in the archive manager. But it still wants to download it.. when I click on the updates, I uncheck the lilypond file and then hit reload, and I get this message:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Also it keeps coming back and saying there is a broken file, even though I clicked "Fix Broken Depencies" and it says at the bottom that there are no more broken files.

Am I missing something? Sorry if these are dumb questions, I just got Linux and I don't have any programming experience other than basic HTML.

Thanks,
Kevin

---

