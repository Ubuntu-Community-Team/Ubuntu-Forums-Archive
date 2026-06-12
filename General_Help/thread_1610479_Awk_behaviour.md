---
title: "Awk behaviour"
date: 2010-10-31
forum: General Help
---

### Post by velocite on 2010-10-31
I understand that Ubuntu 10.04 changed the default awk from mawk to gawk, however I don't understand why
echo | gawk '{printf("%.3s\n","Hello")}'
produces 'Hello', rather than 'Hel'
I thought GNU awk supported string precision modifiers.

I'm testing on a virgin installation of Ubuntu 10.10

Can anyone shed any light?

---

### Post by Brandon Williams on 2010-10-31
mawk and gawk work exactly the same way for me (tested on 08.04 and 10.04). Maybe you accidently left out the '.' in "%.3s\n" when you tested it on 10.04.

---

### Post by velocite on 2010-11-01
Hmm. Perhaps this is an issue with 10.10 but not 10.04?

I've replicated this behaviour on two Ubuntu 10.10 machines:
1) a virgin install of Ubuntu 10.10
2) a machine that's been upgraded from 8.10->9.04->9.10->10.04->10.10

On both I get:

$ type gawk
gawk is /usr/bin/gawk

$ ls -l /usr/bin/gawk
-rwxr-xr-x 1 root root 326236 2010-05-09 15:09 /usr/bin/gawk

$ gawk -W version
GNU Awk 3.1.7

$ echo | gawk '{printf("%.3s\n","Hello")}'
Hello

$ echo | mawk '{printf("%.3s\n","Hello")}'
Hel

Can anyone else reproduce this on Ubuntu 10.10?
i.e. is the gawk shipped with Ubuntu 10.10 "broken" as far as string precision modifiers are concerned?

---

### Post by Brandon Williams on 2010-11-02
Yes, you're right ... this is broken on the version of gawk in 10.10 but not broken on the version that came with earlier ubuntu versions.

That said, I see that ubuntu-minimal depends upon mawk. For me, gawk is installed because one of the printer packages depends upon it, but since mawk is also installed, I just switched the default to mawk using update-alternatives.

---

### Post by velocite on 2010-11-03
I've downloaded the source code for gawk 3.1.8 from [http://ftp.gnu.org/gnu/gawk/](http://ftp.gnu.org/gnu/gawk/) and compiled it up. Problem solved.

(mawk won't work for me as it segment faults in some of my scripts)

Hopefully gawk 3.1.8 will find its way into the Ubuntu 10.10 automatic updates.

---

