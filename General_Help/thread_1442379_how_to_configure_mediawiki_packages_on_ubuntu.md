---
title: "how to configure mediawiki packages on ubuntu"
date: 2010-03-29
forum: General Help
---

### Post by pythonscript on 2010-03-29
I just installed the mediawiki and mediawiki-extensions packages from the repository, and now I'm trying to get it configured so I can run mediawiki locally (in a virtual computer). I found instructions that said to browse out to [http://localhost/](http://localhost/)*install-directory-with-index.php-file* but this doesn't seem to work for me. Where would mediawiki install to? I ran "updatedb" followed by "locate index.php" and here's what I found:

```

usr/share/mediawiki/index.php
/usr/share/mediawiki/includes/specials/SpecialPrefixindex.php
/usr/share/mediawiki/maintenance/rebuildtextindex.php
/var/lib/mediawiki/index.php

```

but [http://localhost/usr/share/mediawiki/index.php](http://localhost/usr/share/mediawiki/index.php), or any other of these, just returns a 404 error. It's supposed to bring me to the control panel, or installation instructions, or something. Can anyone help me here? I'd really love to have my own local (for now) wiki running. Thanks!

---

### Post by pythonscript on 2010-03-30
Can anyone offer any insight into this? I simply have no idea how to continue, and my searches are fruitless thus far.

---

### Post by radard on 2010-05-18
Hi,

I have the same need...
And this page: [https://help.ubuntu.com/community/MediaWiki](https://help.ubuntu.com/community/MediaWiki)
which I used before Lucid, does not help much now. For some reason it won't work as smoothly as it use to. :confused:
The first command gives me this message:
```
tasksel: aptitude program error (100)
```

I do have the confirmation that my local server works ([http://localhost/](http://localhost/)), though.

---

