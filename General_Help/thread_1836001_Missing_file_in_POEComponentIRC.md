---
title: "Missing file in POE::Component::IRC?"
date: 2011-08-30
forum: General Help
---

### Post by mitchell2.0 on 2011-08-30
I'm having problems with libpoe-component-irc-perl, i get this:

mitch@Mitch-Laptop-Linux:~/Downloads/grue$ ./grue.pl
Can't locate IRC/Utils.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/share/perl/5.10.1/POE/Component/IRC/Plugin/Whois.pm line 13.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.10.1/POE/Component/IRC/Plugin/Whois.pm line 13.
Compilation failed in require at /usr/local/share/perl/5.10.1/POE/Component/IRC.pm line 20.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.10.1/POE/Component/IRC.pm line 20.
Compilation failed in require at ./grue.pl line 24.
BEGIN failed--compilation aborted at ./grue.pl line 24.

I was told its installed right (all the other files are where they should be), but this ones missing. anyone else having this problem?

---

