---
title: "cal command - no option to change start day"
date: 2011-12-19
forum: General Help
---

### Post by Trevor Burton on 2011-12-19
I have a desktop on 10.04 and a laptop on 11.10 and the terminal cal command is different on each of them.

Specifically, calendars begin with a Monday on 10.04 cal and with a Sunday on 11.10 cal.

I'm surprised by this, as I would have thought changing the behaviour of cal would damage pre-existing scripts dependent on it.

Any cal users out there know how to get cal (10.04) to begin with Sunday as its start day for calendars?  man pages give no clue.

Thanks, Trevor

---

### Post by d2btoo on 2011-12-19
Hi,
On my 10.04.3 it's certainly starts with Sunday...

[IMG]http://img600.imageshack.us/img600/8971/selection001o.png[/IMG]

Are you sure your locale settings are alright in that machine? ... I asked this because I've read/heard somewhere that locale settings affect start of the week etc.

---

### Post by Trevor Burton on 2011-12-22
> **d2btoo said:**
> Hi,
On my 10.04.3 it's certainly starts with Sunday...

[IMG]http://img600.imageshack.us/img600/8971/selection001o.png[/IMG]

Are you sure your locale settings are alright in that machine? ... I asked this because I've read/heard somewhere that locale settings affect start of the week etc.

Hi, 

Well, thanks for the suggestion.

I checked my locale settings and got the following...
```

user@computer:~$ locale
LANG=en_GB.utf8
LC_CTYPE="en_GB.utf8"
LC_NUMERIC="en_GB.utf8"
LC_TIME="en_GB.utf8"
LC_COLLATE="en_GB.utf8"
LC_MONETARY="en_GB.utf8"
LC_MESSAGES="en_GB.utf8"
LC_PAPER="en_GB.utf8"
LC_NAME="en_GB.utf8"
LC_ADDRESS="en_GB.utf8"
LC_TELEPHONE="en_GB.utf8"
LC_MEASUREMENT="en_GB.utf8"
LC_IDENTIFICATION="en_GB.utf8"
LC_ALL=

```

That seems right doesn't it?

but cal *does* start with a Monday :confused:

[IMG]https://lh5.googleusercontent.com/-0YXVtZrPxGE/TvMOrxpWl3I/AAAAAAAAAS4/Nz2UqeRBSeE/w257-h195-k/cal.png[/IMG]

---

### Post by d2btoo on 2011-12-22
> **Trevor Burton said:**
> 
That seems right doesn't it?

Looks fine.
> **Trevor Burton said:**
> 
but cal *does* start with a Monday :confused:
Is this only happening to cal? what happens in the drop-down calender, the one which drops-down when you click on the clock at the top-right on the desktop?


EDIT: According to google LC_TIME=en_GB.UTF-8, means by default weeks starts on monday. I'm not familiar with UK time, do you think this info is right? If yes then everything seems alright! ... no?

EDIT2: Indeed it's "en_GB.UTF-8" is the problem, as it seems, see bellow:

[[IMG]http://img31.imageshack.us/img31/2797/callocale.th.png[/IMG]](http://img31.imageshack.us/i/callocale.png/)

---

### Post by btindie on 2011-12-22
In the UK the first day of the week is Monday, so technically it's your  other system that has the problem which is the case with mine.

I'm currently using 11.04 on one of my laptops and under cal it  incorrectly starts with Sun when LANG=en_GB.UTF-8 while the calendar  correctly starts on Monday. Go figure...

The values are defined in /usr/share/i18n/locales/en_GB

It seems that the version of cal that is installed doesn't support locale so by default it does it the American way, i.e. Sunday being the first day of the week.
ldd /usr/bin/cal
    linux-gate.so.1 =>  (0xb77b4000)
    libncurses.so.5 => /lib/libncurses.so.5 (0xb776b000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb760a000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb7605000)
    /lib/ld-linux.so.2 (0xb77b5000)

There's supposed to be an '-M' flag that you can pass to cal to tell it to start from Monday which is mentioned in the man page but doesn't actually work with the program.

---

### Post by d2btoo on 2011-12-22
> **btindie said:**
> 
There's supposed to be an '-M' flag that you can pass to cal to tell it to start from Monday which is mentioned in the man page but doesn't actually work with the program.

As far as I know, the -M and -S options are for ncal, not for cal, but anyway, as you say, those options don't work even for ncal under Lucid.

I'm curious what **ncal** and **ncal -p** outputs on your machine!?

---

### Post by Trevor Burton on 2011-12-22
Thanks everybody.

I've checked locale on both my lucid desktop and oneiric laptop and they both have en_GB_UTF for everything.

Nevertheless, cal does display differently on them.

The manpages for cal are slightly different too, though both are dated "March 14, 2009".  There are also slightly different options for them, with the oneiric one having an -A and a -B option.

Neither has a -M for Monday option and this does seem to be an ncal option alone.

Additionally, there are differences when printing a full year calendar:
LUCID
a blank line after the year
a blank line after each row of months

ONEIRIC
no blank line after the year
no blank line after each row of months

However, both do print each row of months on 8 lines even if 7 suffice (and this is apparently the intended behaviour).

I noticed this as I was trying to create a compendium of annual calendars from 1752 to 2100 in a text file which I would then print to .pdf and the page breaks went squiffy on the second machine I tried.

Very curious that such an old Unix command should differ between Ubuntu versions, but there you go.

---

### Post by Vaphell on 2011-12-22
```
$ for l in C en_GB.UTF-8 en_US.UTF-8; do echo $l first_weekday=$( LANG=$l locale first_weekday); done

**C** first_weekday=**1**
**en_GB.UTF-8** first_weekday=**2**
**en_US.UTF-8** first_weekday=**1**

```
as you can see USian locale and default non-locale (C) differ from GB so british week starts from monday.
you can force commands to a different locale by using LANG=.... before them

oneiric version of cal is broken, it seems to ignore locale entirely.

**ncal -C** in oneiric should be ok, it's ncal in cal mode, it appears to be localized by default and accepts all the ncal options (including -M/-S for monday/sunday)

---

