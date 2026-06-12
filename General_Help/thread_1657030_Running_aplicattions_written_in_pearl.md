---
title: "Running aplicattions written in pearl"
date: 2010-12-31
forum: General Help
---

### Post by pedlazcar on 2010-12-31
Hello.

First of all, I'm convinced that "pearl" is not the main problem here. I'm a complete newbie in ubuntu (or linux) universe.

I'm trying to edit mobi files. To do so, I looked for a mobi2html program, which I found here: [https://dev.mobileread.com/trac/mobiperl/wiki](https://dev.mobileread.com/trac/mobiperl/wiki)

I followed all the instructions mentioned in the READ_ME file that comes with the zipped source. I strongly believe, as no error messages appeared during the installation, everything went according to plan.

My question is simple: **having completed all the installation procedures, what should I do next?** My general procedure is to look up for the new program name in the "applications" tab, but I know that won't always do the trick.


Here are the messages I've received during the installation:

===========================================================

perl Makefile.PL
```
Checking if your kit is complete...
Looks good
Writing Makefile for Palm
```make
```
cp lib/ZirePhoto.pm blib/lib/Palm/ZirePhoto.pm
cp lib/Datebook.pm blib/lib/Palm/Datebook.pm
cp lib/Raw.pm blib/lib/Palm/Raw.pm
cp lib/Address.pm blib/lib/Palm/Address.pm
cp lib/Memo.pm blib/lib/Palm/Memo.pm
cp lib/PDB.pm blib/lib/Palm/PDB.pm
cp lib/ToDo.pm blib/lib/Palm/ToDo.pm
cp lib/DateTime.pm blib/lib/Palm/DateTime.pm
cp lib/Mail.pm blib/lib/Palm/Mail.pm
cp lib/StdAppInfo.pm blib/lib/Palm/StdAppInfo.pm
cp lib/Palm.pm blib/lib/Palm.pm
cp examples/pdbdump blib/script/pdbdump
```make install
```

Installing /usr/local/share/perl/5.10.1/Palm.pm
Installing /usr/local/share/perl/5.10.1/Palm/Address.pm
Installing /usr/local/share/perl/5.10.1/Palm/ZirePhoto.pm
Installing /usr/local/share/perl/5.10.1/Palm/Datebook.pm
Installing /usr/local/share/perl/5.10.1/Palm/Mail.pm
Installing /usr/local/share/perl/5.10.1/Palm/StdAppInfo.pm
Installing /usr/local/share/perl/5.10.1/Palm/ToDo.pm
Installing /usr/local/share/perl/5.10.1/Palm/Memo.pm
Installing /usr/local/share/perl/5.10.1/Palm/PDB.pm
Installing /usr/local/share/perl/5.10.1/Palm/DateTime.pm
Installing /usr/local/share/perl/5.10.1/Palm/Raw.pm
Installing /usr/local/man/man1/pdbdump.1p
Installing /usr/local/man/man3/Mail.3pm
Installing /usr/local/man/man3/Raw.3pm
Installing /usr/local/man/man3/Memo.3pm
Installing /usr/local/man/man3/Palm.3pm
Installing /usr/local/man/man3/StdAppInfo.3pm
Installing /usr/local/man/man3/Datebook.3pm
Installing /usr/local/man/man3/ZirePhoto.3pm
Installing /usr/local/man/man3/Address.3pm
Installing /usr/local/man/man3/ToDo.3pm
Installing /usr/local/man/man3/PDB.3pm
Installing /usr/local/bin/pdbdump
```

Thanks!

---

### Post by noah++ on 2010-12-31
I don't think the program you compiled is sophisticated enough to insert itself in the Applications menu. But since this file is in a **bin **directory,
```
Installing /usr/local/bin/pdbdump
```you can be pretty sure that's the binary executable.

**/usr/local/bin** should be in your **$PATH**. Invoking **echo $PATH** from Terminal will verify that. If it is there, then invoking **pdbdump** from Terminal will work to start the program. 

Let us know if you have any questions about any of these terms or commands. You were right to suspect that Perl is not a suspect here.

---

### Post by melander on 2010-12-31
It appears that the script runs from the command line and has no GUI so it's not going to appear on any applications tab.

From the examples given [on this page]("https://dev.mobileread.com/dist/tompe/mobiperl/html/mobi2html.html") I believe you would:
[LIST]
[*]start a terminal
[*]change to the directory in which your mobi file is located
```
cd mobidirectory
```
[*]unpack the mobi file
```
mobi2html "mobifile"
```
[/LIST]

There are various options for what directory to unpack to, unpack format and so on shown in the examples on the page linked to above.

I've never used the program and don't even know what a mobi is, so this is mildly educated speculation on my part.

Regards,

---

