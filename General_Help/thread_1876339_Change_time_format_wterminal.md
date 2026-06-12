---
title: "Change time format w/terminal"
date: 2011-11-06
forum: General Help
---

### Post by DapperMe17 on 2011-11-06
I'd like to know how to change the system time to use a "custom" format. 

I use 12 hour with am/pm, however, between 12am and 1am, the hour indicator shows "0" instead of "12". 

I believe this is the correct format....%l:%M %p

How would I change to that in terminal?

---

### Post by mike555 on 2011-11-06
You shouldn't need to use terminal, just rt. click on clock and in properties put the format you want.....

Codes;
%%   a literal %
%a   locale's abbreviated weekday name (e.g., Sun)
%A   locale's full weekday name (e.g., Sunday)
%b   locale's abbreviated month name (e.g., Jan)
%B   locale's full month name (e.g., January)
%c   locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
%C   century; like %Y, except omit last two digits (e.g., 21)
%d   day of month (e.g, 01)
%D   date; same as %m/%d/%y
%e   day of month, space padded; same as %_d
%F   full date; same as %Y-%m-%d
%g   last two digits of year of ISO week number (see %G)
%G   year of ISO week number (see %V); normally useful only with %V
%h   same as %b
%H   hour (00..23)
%I   hour (01..12)
%j   day of year (001..366)
%k   hour ( 0..23)
%l   hour ( 1..12)
%m   month (01..12)
%M   minute (00..59)
%n   a newline
%p   locale's equivalent of either AM or PM; blank if not known
%P   like %p, but lower case
%r   locale's 12-hour clock time (e.g., 11:11:04 PM)
%R   24-hour hour and minute; same as %H:%M
%s   seconds since 1970-01-01 00:00:00 UTC
%S   second (00..60)
%t   a tab
%T   time; same as %H:%M:%S
%u   day of week (1..7); 1 is Monday
%U   week number of year, with Sunday as first day of week (00..53)
%V   ISO week number, with Monday as first day of week (01..53)
%w   day of week (0..6); 0 is Sunday
%W   week number of year, with Monday as first day of week (00..53)
%x   locale's date representation (e.g., 12/31/99)
%X   locale's time representation (e.g., 23:13:48)
%y   last two digits of year (00..99)
%Y   year
%z   +hhmm numeric timezone (e.g., -0400)
%Z   alphabetic time zone abbreviation (e.g., EDT)

As an example, I entered this for my Custom clock format.

%l:%M %p

That's a lower case "L" not a capital "i". The resulting time display looks like this.

8:44 PM

---

### Post by DapperMe17 on 2011-11-06
Ok, that worked just fine. I had to switch back to "digital" to see the actual time format options.

Thanks!

---

### Post by DapperMe17 on 2011-11-07
Mike555,

I spoke too quickly.

For some reason, "LCD" mode is the only mode that isn't allowing "12"am...it's still showing "0"am, after the time format change.

?

---

