---
title: "Open Office Spell check not working"
date: 2010-03-04
forum: General Help
---

### Post by Kaneda187 on 2010-03-04
The title says it all im running open office 3.0 and in ubuntu 8.10 32bit

cant get spell chect to work at all....

any ideas?

---

### Post by prshah on 2010-03-04
> **Kaneda187 said:**
> open office 3.0 and in ubuntu 8.10 32bit
cant get spell chect to work

You may not have a default language selected. Choose Tools-Language-For all text-English (USA) (Or as suitable to you). Spell check should activate immediately (no need to restart, etc)

---

### Post by dE_logics on 2010-03-04
Try and upgrade to openoffice 3.2, if it still does not work download the en-us extension and install.

[http://extensions.services.openoffice.org/en/dictionary](http://extensions.services.openoffice.org/en/dictionary)

To install the new openoffice, download - 

[http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz](http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz) (x86)

or 

[http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxX86-64_install_en-US_deb.tar.gz(AMD64](http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxX86-64_install_en-US_deb.tar.gz(AMD64))


Extract the files; there should be a folder named 'debs' with lots of deb packages in it, open that location in terminal then execute ```
dpkg -i *.deb
```

Do the above only if the new openoffice is not in the repositories.

---

### Post by Hagar Delest on 2010-03-06
Check that one also: [[Troubleshooting] Spell check in OOo 3.x](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512).

---

