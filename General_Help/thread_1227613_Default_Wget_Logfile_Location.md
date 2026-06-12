---
title: "Default Wget Logfile Location?"
date: 2009-07-30
forum: General Help
---

### Post by BJ_Covert_Action on 2009-07-30
Howdy Everyone,

I popped open Firestarter after closing Firefox and noticed that wget was making various connects and disconnects to IP addresses that didn't reveal any particular pattern when I whois'ed them. Anyways, I was curious to see what wget was up to without telling me and I went in search of a logfile.

However, all I could find in the manpages was a discussion about how to pipe a manual wget command's output to a logfile. I didn't see any discussion regarding any default logifles. Googling didn't reveal a whole lot either.

Thus, my question is this. Is there a default location for some kind of logfile relating to wget? If not, is there a way to configure wget to output to a default logfile all the time? Call me paranoid, but I just want to see what is being downloaded onto my box.

I am running ubuntu 8.04 on this particular computer.

Thanks for the help in advance,
Brady

---

### Post by BJ_Covert_Action on 2009-08-02
Anyone? I still can't find a straight forward answer on google...

---

### Post by credobyte on 2009-08-02
wget without any parameters ( only url ) will not create a logfile.

```
wget http://www.domain.com/file.tar.gz -o wget.log
```

---

### Post by BJ_Covert_Action on 2009-08-03
Oh, well that explains why I can't find it. So far as I understand, the -o switch will force a logfile for one operation, is there a way to force it to print to a logfile every time?

---

### Post by andrew.46 on 2009-08-03
Hi BJ,

> **BJ_Covert_Action said:**
> Oh, well that explains why I can't find it. So far as I understand, the -o switch will force a logfile for one operation, is there a way to force it to print to a logfile every time?

wget has 2 configuration files: *$HOME/.wgetrc* and */etc/wgetrc*. For your needs I suspect it would be better to alter the *$HOME/.wgetrc* file rather than the system file and I suspect you will also need to create this file. Available commands can be seen here:

6.3 Wgetrc Commands
[http://www.gnu.org/software/wget/manual/html_node/Wgetrc-Commands.html](http://www.gnu.org/software/wget/manual/html_node/Wgetrc-Commands.html)

The one you are after is this one:

```
logfile = file
Set logfile to file, the same as ‘-o file’.
``` 

The only trouble may be that wget might very well *overwrite* this file each time rather than *append* to it, I have not tested this.

All the best,

Andrew

---

### Post by BJ_Covert_Action on 2009-08-04
That is precisely what I needed. I futzed about in the .wgetrc file a bit but I didn't notice anything relating to logfiles so I didn't implement anything. I would bet that I could force it to append rather than overwrite via the appropriate switch, or option or something....if all else fails I might be able to hack up a perl script to force an append rather than overwrite. Thanks for the pointers.

Out of curiosity, I noticed vim is also controlled via a .***rc file. Anyone have any idea what rc stands for? Real configurations? Readily Configurable? Rolling Cloisters? :P

Thanks guys,
Brady

---

### Post by andrew.46 on 2009-08-04
Hi BJ,

> **BJ_Covert_Action said:**
> Out of curiosity, I noticed vim is also controlled via a .***rc file. Anyone have any idea what rc stands for? Real configurations? Readily Configurable? Rolling Cloisters? :P

I believe the *rc* is derived from *runcom* files used in an ancient OS called CTSS. Just in case you think I am clever I only just found this out :-). Details here:

[http://en.wikipedia.org/wiki/Configuration_file](http://en.wikipedia.org/wiki/Configuration_file)

Andrew

---

