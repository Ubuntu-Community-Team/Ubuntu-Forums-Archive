---
title: "Broken packages after installation with USB in Notebook"
date: 2009-12-29
forum: General Help
---

### Post by rogergs on 2009-12-29
Hello,

I have installed a fresh Ubuntu Karmic 9.10 on my HP Mini notebook, using a bootable USB stick, created using Ubuntu's "USB startup disk creator" of my desktop computer.

No error occurs during the installation and I can restart normally after finish. During the process and after the notebook is connected to internet using ethernet. Next start the problems when I try to configure the proprietary drivers and run update manager also. In both cases errors are prompt.


[LIST]
[*][COLOR=Red]SystemError: E:Unable to correct problems, you have held broken packages[/COLOR] --> This error occurs when I try to activate the Broadcom STA wireless driver-
[*]Running Update Manager, different warnings are prompted and the process is cancelled:
[LIST]
[*][COLOR=Red]Some of the packages could not be retrieved from the server(s).[/COLOR]
[COLOR=Red]Do you want to continue, ignoring these packages? [/COLOR]--> I push Yes and next:
[*][COLOR=Red]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.6+nobinonly-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.6+nobinonly-0ubuntu0.9.10.1_i386.deb)
  Hash Sum mismatch [COLOR=Black]--> This is only one warning of dozens[/COLOR][/COLOR]
[*][COLOR=Red][COLOR=Black]If I try to download and refresh the package information from repositories, I receive the next error: [COLOR=Red]Could not download all repository indexes. Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://es.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)[/COLOR]
[/COLOR][/COLOR]
[/LIST]
[/LIST]
Please, could somebody, help me to solve this issues?

Thanks in advanced.

Roger

---

