---
title: "Fresh install preserving configuration, apps and settings?"
date: 2009-11-17
forum: General Help
---

### Post by Bucky Ball on 2009-11-17
Hi all,

Is there anyway I can re-install whilst keeping my current configuration, settings and packages? Using 8.04 and not upgrading, just needing to reinstall the kernel I think. Long story concerning a kernel panic (so working from a liveCD), but I don't really want to do a full install and wipe it all and start again. This baby has been two years in the making! I know, I should have worked out how to back up the essentials already ... :(

I have done quite a bit of research on this but still not sold on any of the methods so far. The most promising seem to be:

[http://lglinux.blogspot.com/2007/11/backup-ubuntu-debian-package-selection.html](http://lglinux.blogspot.com/2007/11/backup-ubuntu-debian-package-selection.html)

[http://www.hanckmann.net/?q=node/27](http://www.hanckmann.net/?q=node/27)

[http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

The last link professes to do all I want. Saves packages by using 'package.selections' which is a twist on the others. No probs about preserving /home; think I have that figured.

Anyone successfully done what I am attempting to do and how did they go about it? All thoughts welcome. :)

---

### Post by Bonster on 2009-11-17
since all ur configurations is in the /home and u said u got that handle. ur set there if u back that up. as for the packages. back up ur sources.list.
theres a few way to install the packages again.

1) Synaptic markings (saves list of all ur installed packages, so u can load into synaptic again and it will install those packages)

2)AtpOnCD (backups all the deb files to cd)

---

### Post by Bucky Ball on 2009-11-17
Thanks for that. Never thought of AptonCD. Just wondering how I would install that and run it to collect the packages when booting from a LiveCD though.

'Synaptic Markings'? Do you mean in Synaptics 'Edit->Save Markings', and that will save a list of all installed packages then once the reinstall is done 'Edit->Read Markings' will install the list? I'll keep digging but that is sounding good. 

Well, time to boot the laptop and do some more digging around but I think I have a plan. I can't fix the kernel panic so re-install it is, painlessly as possible. I like to have a solid plan!

Thanks for your suggestions and keep 'em coming if you have any other ideas. ;-)

---

