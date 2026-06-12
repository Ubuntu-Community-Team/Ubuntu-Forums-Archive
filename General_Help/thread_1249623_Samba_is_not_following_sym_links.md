---
title: "Samba is not following sym links"
date: 2009-08-25
forum: General Help
---

### Post by alpha_lt on 2009-08-25
Hi all,

I've set these lines in [general] section of smb.conf

```

follow symlinks = yes
wide links = yes
unix extensions = no

```

Symlinks isn't working with samba. Do I miss something here ? I can see file name of symlink, but I can't even read it. I've searched forums and these three lines should be enough, but...
The strangest thing is that when I copy those line to share section and restart samba several times it seems try to work as I want. Then I'll change those three lines to "no" again to disable symlinks and I'm unable to enable it again. It just don't work. Strange behaviour. Maybe some one of you have dealt with it.
Samba version is 3.3.2 and linux is ubuntu 9.04

alpha

---

