---
title: "Undoing what has been done?"
date: 2006-02-21
forum: General Help
---

### Post by tntc1978 on 2006-02-21
How do I undo/uinstall these steps?
```
sudo perl -MCPAN -e 'install Bundle::LWP' 
sudo perl -MCPAN -e 'install Crypt::Simple' 
sudo perl -MCPAN -e 'install XML::Simple' 
sudo perl -MCPAN -e 'install Crypt::SSLeay'
```

---

### Post by akiro.yamamoto on 2006-02-21
CPAN has no un-install script.
You will have to Find file Bundle/LWP/.packlist in Perl directories. This file contains
a list of Bundle::LWP files. Just remove them all. 
Follow the same process for the others. There is an external script around, but I can't remember the name of it right now.
Hope this helps.

---

### Post by Sendervictorius on 2006-02-21
Maybe there is a way with another CPAN option, but I would just go to the perl installation directory (e.g. /usr/share/perl5/Bundle/) and remove the LWP.pm package - and rmdir the directory if there aren't any other packages installed.

Not sure why you want to remove these though? Are they doing harm?

---

### Post by tntc1978 on 2006-02-21
> Not sure why you want to remove these though? Are they doing harm?I don't know, but I was trying to install the gmail checker like this: [http://ubuntuforums.org/showthread.php?t=74539](http://ubuntuforums.org/showthread.php?t=74539) but couldn't get it to work. Then I found an easier way around here: [http://ubuntuforums.org/showpost.php?p=372215&postcount=106](http://ubuntuforums.org/showpost.php?p=372215&postcount=106)
And then I thought that I didn't need these Perly things anymore...

---

### Post by tntc1978 on 2006-02-21
And then again, I get these errors every time I use Synaptics:
> E: libxml-sax-perl: underproces post-installation script returned terminationstatus 255
E: libxml-libxml-perl: dependency problems - leaving it unconfigured
E: libxml-simple-perl: dependency problems - leaving it unconfigured

What to do what to do? :-?

---

### Post by Sendervictorius on 2006-02-22
Not sure what the problem is [libxml-sax-perl], but I suspect you have a mixture of different versions of perl dependencies. In synaptic, work through the version dependencies: (Right-click/dependencies tab) and check what versions of packages you have installed (find installed package in synaptic).

---

### Post by tntc1978 on 2006-02-22
Man that will take a while, but since my Breezy installation is quite new (from yesterday) I might as well do a fresh install, and don't put any code into the terminal that I don't understand.

Thanks a bunch for the replies.

---

