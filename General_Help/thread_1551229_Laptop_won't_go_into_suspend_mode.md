---
title: "Laptop won't go into suspend mode"
date: 2010-08-12
forum: General Help
---

### Post by inameiname on 2010-08-12
First off, I just want to let you know I'm using the 'ppa:kernel-ppa/ppa', which has worked just fine until now. 

Anyway, I just updated my kernel to 2.6.35-15-generic, having previously had 2.6.35-14-generic installed (which worked just fine), and all of a sudden when I close and open my laptop lid it refuses to go to suspend mode. It has always been set in suspend mode, so it was never something I changed upon installation of the latest kernel. Now, it merely turns the screen off, just as it would if it was set on "blank screen", and not "suspend". 

Why would it change with the latest kernel? As I said, 2.6.35-14-generic would go into suspend mode without issues. It's 2.6-35-15-generic that is obviously the culprit. 

Anybody know of how to either fix it, or perhaps find out just what might be the issue? I've ran across this issue with kernel updates before, (not me but I've seen threads about it), official and unofficial ones, so hopefully somebody can help me. I would like my laptop to actually go to sleep, not just go blank screen.

UPDATE:

I've tried changing what the computer does when closing the lid and all options (suspend, hibernate, & shutdown), all do nothing and instead it's set on 'blank screen'. Doh!

---

### Post by MrStill on 2010-08-12
I had this issue last time I updated the kernel on my Gentoo box. For me it was acpi, which would tell your laptop to sleep when you close the lid. Anyway, acpi requires kernel modules be present to work. This might not be the issue for you, since you are using a generic kernel. 

Try:
```

sudo /etc/acpi/sleep.sh

```
This is the script acpi uses to put your laptop to sleep.

---

### Post by inameiname on 2010-08-12
Thanks for the suggestion. This is what I get when putting that line in the terminal:

sudo /etc/acpi/sleep.sh
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory

So I do have the 'sleep.sh' script, it's just not picking up those few things for some reason. Perhaps then, I can assume that if I can figure out this error, and find a solution, my suspend issue should be fixed...do you think? However, if that was the case, it doesn't explain the inability to use the other options as well, such as 'shutdown' and 'hibernate' through closing the lid, which don't also don't work.

Oh, and I checked out the '/var/lib/acpi-support' folder and there is nothing in it, hidden or otherwise. Seems like there should be something in it.

---

### Post by inameiname on 2010-08-12
Ok, so this is very weird. 

Now, all of a sudden, my suspend, hibernate, and shutdown commands with closing the laptop lid work. 

I changed absolutely nothing. The only thing I did was a restart of the computer. And this was of course after the restart I did when I first installed the latest kernel, 2.6.35-15-generic, so it'll be the one used instead of the previous version.

Very weird. But hey, I'm not going to complain. I'll mark this as solved, just because, but it does intrigue me and make me wonder what might have happen and/or was the issue.

UPDATE:

There was one update that was installed from after I installed the latest kernel to now: 

libldap-2.4-2 2.4.21-0ubuntu5.2 was upgraded to 2.4.21-0ubuntu5.3

Does anybody know what this update is, and if it might explain the sudden fix?

Here is my apt-history readout:

```

2010-08-12 03:28:03 startup archives unpack
2010-08-12 03:28:05 upgrade libldap-2.4-2 2.4.21-0ubuntu5.2 2.4.21-0ubuntu5.3
2010-08-12 03:28:05 status half-configured libldap-2.4-2 2.4.21-0ubuntu5.2
2010-08-12 03:28:05 status unpacked libldap-2.4-2 2.4.21-0ubuntu5.2
2010-08-12 03:28:05 status half-installed libldap-2.4-2 2.4.21-0ubuntu5.2
2010-08-12 03:28:05 status triggers-pending man-db 2.5.7-2
2010-08-12 03:28:05 status half-installed libldap-2.4-2 2.4.21-0ubuntu5.2
2010-08-12 03:28:06 status half-installed libldap-2.4-2 2.4.21-0ubuntu5.2
2010-08-12 03:28:06 status unpacked libldap-2.4-2 2.4.21-0ubuntu5.3
2010-08-12 03:28:06 status unpacked libldap-2.4-2 2.4.21-0ubuntu5.3
2010-08-12 03:28:06 trigproc man-db 2.5.7-2 2.5.7-2
2010-08-12 03:28:06 status half-configured man-db 2.5.7-2
2010-08-12 03:28:08 status installed man-db 2.5.7-2
2010-08-12 03:28:09 startup packages configure
2010-08-12 03:28:09 configure libldap-2.4-2 2.4.21-0ubuntu5.3 2.4.21-0ubuntu5.3
2010-08-12 03:28:09 status unpacked libldap-2.4-2 2.4.21-0ubuntu5.3
2010-08-12 03:28:09 status unpacked libldap-2.4-2 2.4.21-0ubuntu5.3
2010-08-12 03:28:09 status half-configured libldap-2.4-2 2.4.21-0ubuntu5.3
2010-08-12 03:28:09 status installed libldap-2.4-2 2.4.21-0ubuntu5.3
2010-08-12 03:28:09 status triggers-pending libc-bin 2.11.1-0ubuntu7.2
2010-08-12 03:28:09 trigproc libc-bin 2.11.1-0ubuntu7.2 2.11.1-0ubuntu7.2
2010-08-12 03:28:09 status half-configured libc-bin 2.11.1-0ubuntu7.2
2010-08-12 03:28:09 status installed libc-bin 2.11.1-0ubuntu7.2

```

And here is my aptcache search readout, showing what description it gives it:

libldap-2.4-2 - OpenLDAP libraries
libldap-2.4-2-dbg - Debugging information for OpenLDAP libraries

---

