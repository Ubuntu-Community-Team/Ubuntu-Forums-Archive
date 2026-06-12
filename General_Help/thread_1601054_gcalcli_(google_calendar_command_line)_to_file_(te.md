---
title: "gcalcli (google calendar command line) to file (tee) shows weird characters"
date: 2010-10-19
forum: General Help
---

### Post by cedardoc on 2010-10-19
Hi,

when I enter this in the terminal:
gcalcli calw 2 | tee '/home/david/2weeks.txt'

(using gcalcli - the command line google calendar access tool), 

the information is displayed correctly at the terminal, but in the text file there are all these weird characters.  For example here's what's supposed to be the top of the week view in text:

[0m
[0;37m+----------+----------+----------+----------+----------+----------+----------+[0m
[0m[0m[0;37m|[0m[0;33mSunday    [0m[0;37m|[0m[0;33mMonday    [0m[0;37m|[0m[0;33mTuesday   [0m[0;37m|[0m[0;33mWednesday [0m[0;37m|[0m[0;33mThursday  [0m[0;37m|[0m[0;33mFriday    [0m[0;37m|[0m[0;33mSaturday  [0m[0;37m|[0m


does anyone know a way to make it look like it does at the terminal?  I assume it has something to do with ascii or utf-8 or something like that, but I'm not sure.

Thanks

---

