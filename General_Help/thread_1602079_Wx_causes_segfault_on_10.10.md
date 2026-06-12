---
title: "Wx causes segfault on 10.10"
date: 2010-10-21
forum: General Help
---

### Post by cesera on 2010-10-21
I just upgraded my netbook to Maverick (with Unity interface) and now I have a problem with a home brew perl script giving me the following error:

```
Signal SEGV at /usr/lib/perl5/Wx/Mini.pm line 57
    Wx::wx_boot('Wx::FS', 0.01) called at /usr/lib/perl5/Wx/FS.pm line 23
    require Wx/FS.pm called at (eval 18)[/usr/lib/perl5/Wx.pm:66] line 1
    Wx::BEGIN() called at /usr/lib/perl5/Wx/FS.pm line 0
    eval {...} called at /usr/lib/perl5/Wx/FS.pm line 0
    eval 'use Wx::DND;use Wx::DocView;use Wx::FS;use Wx::Grid;use Wx::Help;use Wx::Html;use Wx::MDI;use Wx::Print;use Wx::Socket;use Wx::Calendar;use Wx::DateTime;use Wx::Media;use Wx::RichText;use Wx::AUI;' called at /usr/lib/perl5/Wx.pm line 66
    Wx::import('Wx', ':allclasses') called at ./myscript.pl line 3
    main::BEGIN() called at /usr/lib/perl5/Wx/FS.pm line 0
    eval {...} called at /usr/lib/perl5/Wx/FS.pm line 0
Aborted
```To me this is a bit of a showstopper, so I was wondering if anyone help me with this. I probably just need to install another package, but can't work out which one.

---

### Post by cesera on 2010-11-03
BUMP

I can't be the only one still experiencing this problem.

---

### Post by cesera on 2010-12-17
OK, I finally found the problem. The code was generated with wxGlade and then modified, and for some reason wxGlade put the Wx use statement in as:
```
use Wx 0.15 qw[:allclasses];
```
When I changed took the 0.15 out the problem disappeared. I just checked and wxGlade stills puts that '0.15' in there, but I now know how to get around this problem.

---

