---
title: "running makefile.pl"
date: 2006-06-15
forum: General Help
---

### Post by jeisma on 2006-06-15
hello!

what packages do i need to avoid this message?

```

Checking for Gtk.. failed
-------------------------------------------------------
Can't locate Gtk/Types.pm in @INC (@INC contains: /usr/lib/perl5/site_perl/5.8.0 /usr/lib/perl5/site_perl/5.6.0 /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 4) line 3.

Gtk is needed, it implements the perl bindings to Gtk+.
The module is called Gtk-Perl on CPAN or module gnome-perl in the Gnome CVS
We need at least version 0.7000
-------------------------------------------------------
Checking for Gnome.. failed
-------------------------------------------------------
Can't locate Gnome/Types.pm in @INC (@INC contains: /usr/lib/perl5/site_perl/5.8.0 /usr/lib/perl5/site_perl/5.6.0 /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 5) line 3.

Gnome is needed, it implements the perl bindings to Gnome.
It is a submodule of the Gtk-Perl package and needs to be built separately.
Read the Gtk-Perl INSTALL file for details of how to do this.
Glade-Perl will still work but you will not be able to
use any Gnome widgets in your Glade projects
We need at least version 1.2.0
-------------------------------------------------------
Checking for Glade-Perl.. failed
-------------------------------------------------------
Can't locate Glade/PerlRun.pm in @INC (@INC contains: /usr/lib/perl5/site_perl/5.8.0 /usr/lib/perl5/site_perl/5.6.0 /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 6) line 3.

Glade-Perl is needed, it runs glade generated programs.
It is a module of the Glade-Perl package
We need at least version 0.60
-------------------------------------------------------
-------------------------------------------------------
The missing modules can be obtained from CPAN. Visit
<URL:http://www.perl.com/CPAN/> to find a CPAN site near you.
-------------------------------------------------------

Setting RELEASE = 2 at Makefile.PL line 134.
Writing Makefile for Pxesconfig

```

thank you!

---

### Post by th3james on 2006-06-15
Are you running kubuntu? it looks like you don't have any gnome libaries installed

---

### Post by jeisma on 2006-06-15
hello!

im running, ubuntu. which libraries do i need?

thanks!

---

### Post by th3james on 2006-06-15
hmm.. it looks like your missing gtk-perl, do a search in synaptic, have you got libgtk2-perl installed?

---

### Post by ifokkema on 2006-06-15
[QUOTE=jeisma]hello!

im running, ubuntu. which libraries do i need?

thanks![/QUOTE]
The three errors above are from missing these three packages:
libgtk-perl
libgnome-perl
libglade-perl

Install those and you're done (or at least a little further).

---

