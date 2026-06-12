---
title: "Gimp 2.7 and broken updates"
date: 2011-10-12
forum: General Help
---

### Post by An Sanct on 2011-10-12
Greetings!

Well, I wanted to install Gimp 2.7.x, so I added the according PPA and updated, then wanted to install the new version of Gimp.

OS: Maverick 64bit

Now, update manager says:
> ... Terminal: apt-get install -fI tried that and it sayed
> 1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4,015kB of archives.
After this operation, 2,294kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 331404 files and directories currently installed.)
Preparing to replace gimp 2.6.10-1ubuntu3.4 (using .../gimp_2.7.3-2010072701~mm_amd64.deb) ...
Unpacking replacement gimp ...
dpkg: error processing /var/cache/apt/archives/gimp_2.7.3-2010072701~mm_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/gimp/2.0/plug-ins/file-xmc', which is also in package gimp-plugin-registry 3.2-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.7.3-2010072701~mm_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Software center continuously hits me with "Items cannot be installed or removed (...) Do you wan to repair it now?". After clicking Repair it fails.

I know it is a beginner problem I am having :), but could someone shed some light for me on this? What should I do?

---

### Post by An Sanct on 2011-10-13
(old)Anybody?(old)

Yes :) solved it ...

Basically, I deleted some update files from 

> /var/lib/dpkg/info/

updated, updated, upgraded

and then it worked ...

the procedure for similar situations can be found [here]("http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/").

---

