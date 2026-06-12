---
title: "Air"
date: 2011-12-06
forum: General Help
---

### Post by Ve6jhc on 2011-12-06
I am trying to run AIR (Automated Image and Restore). This a gui for creating images of digital media. I am getting an error when I run the tool as noted below (can't find Tk.pm) ...

Install of Perl/Tk is complete.

Unpacking and installing air-counter...
Install of air-counter is complete.

Unpacking and installing tailer...
Install of tailer is complete.

Unpacking and installing icons...
Install of icons is complete.

/usr/local/bin/split already installed - not installing split.
Installing AIR 2.0.0...
Install of AIR v2.0.0 complete.

Cleaning up...

All Done. Type 'air' on the command-line to begin.

jeff@ubuntu:~/Desktop/AIR$ sudo air
Can't locate Tk.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/local/bin/air line 21.
BEGIN failed--compilation aborted at /usr/local/bin/air line 21.
jeff@ubuntu:~/Desktop/AIR$ 


Reading the documentation they talk about a bug in Perl/Tk (804.028) as well as a fix but no joy. Any ideas?

---

### Post by phidia on 2011-12-06
If you google the line that begins with > Can't locate TK pm... you get some hits but unfortunately nothing seemed related to AIR. Why did you use sudo to start air though?

---

### Post by Ve6jhc on 2011-12-06
The release notes for AIR say to Type 'sudo air' on the command-line to start.

---

