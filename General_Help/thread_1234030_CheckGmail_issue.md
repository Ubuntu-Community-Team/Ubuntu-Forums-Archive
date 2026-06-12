---
title: "CheckGmail issue?"
date: 2009-08-07
forum: General Help
---

### Post by archeryguru2000 on 2009-08-07
Hello all, I've recently discovered CheckGmail. I decided to give it a try and I kinda like it. However, upon returning to my workstation the next day (upon reboot)... I cannot activate CheckGmail. I've tried executing from CLI with the following error message:
```

$: checkgmail
Warning: Gtk2::Sexy not found ...

CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN (http://search.cpan.org) if you want to use this feature ...


not well-formed (invalid token) at line 16, column 15, byte 515 at /usr/lib/perl5/XML/Parser.pm line 187
Perl exited with active threads:
   1 running and unjoined
   0 finished and unjoined
   0 running and detached

```
The return states 1 running and unjoined, does that mean that CheckGmail is running? If so, why doesn't it display in my notification menu, why doesn't it display an icon when I receive a new mail? And what on Earth does 'Sexy not found...' mean? I mean hello, I'm right here! ;) Sorry, had to do that.

Anyway, if anybody could give a heads up on what this message may mean I'd greatly appreciate it.

Thanks,
~~archery~~

---

### Post by archeryguru2000 on 2009-08-12
Just to give anybody a heads up, my problem is know (apparently) solved.  I simply deleted (renamed) my '~/.checkgmail/prefs.xml' file and restarted checkgmail.  I'm not sure what the problem was before... but all is well now.

~~archery~~

---

