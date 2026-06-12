---
title: "Displaying the Time as Metric Time in Ubuntu 10.04"
date: 2010-11-12
forum: General Help
---

### Post by Joseph Schwenker on 2010-11-12
I recently found that I can change the date format on the calendar applet in Ubuntu 10.04 by editing /apps/panel/clock_screen0/prefs/format and /apps/panel/clock_screen0/prefs/custom_format.
If format is changed to "custom", the calendar applet will display the date and time in the format specified in "custom_format".  The description of "custom_format" said that you can use conversion specifiers referenced in the manual page for strftime.  The man page reads:

> STRFTIME(3)                Linux Programmer's Manual               STRFTIME(3)



NAME
       strftime - format date and time

SYNOPSIS
       #include <time.h>

       size_t strftime(char *s, size_t max, const char *format,
                       const struct tm *tm);

DESCRIPTION
       The  strftime()  function  formats the broken-down time tm according to
       the format specification format and places the result in the  character
       array s of size max.

       Ordinary characters placed in the format string are copied to s without
       conversion.  Conversion specifications are introduced by a '%'  charac&#8208;
       ter,  and  terminated  by  a  conversion  specifier  character, and are
       replaced in s as follows:

       %a     The abbreviated weekday name according to the current locale.

       %A     The full weekday name according to the current locale.

       %b     The abbreviated month name according to the current locale.

       %B     The full month name according to the current locale.

       %c     The preferred date  and  time  representation  for  the  current
              locale.

       %C     The century number (year/100) as a 2-digit integer. (SU)

       %d     The day of the month as a decimal number (range 01 to 31).

       %D     Equivalent to %m/%d/%y.  (Yecch — for Americans only.  Americans
              should note that in other countries %d/%m/%y is  rather  common.
              This  means that in international context this format is ambigu&#8208;
              ous and should not be used.) (SU)

       %e     Like %d, the day of the month as a decimal number, but a leading
              zero is replaced by a space. (SU)

       %E     Modifier: use alternative format, see below. (SU)

       %F     Equivalent to %Y-%m-%d (the ISO 8601 date format). (C99)

       %G     The ISO 8601 week-based year (see NOTES) with century as a deci&#8208;
              mal number.  The 4-digit year corresponding to the ISO week num&#8208;
              ber  (see %V).  This has the same format and value as %Y, except
              that if the ISO week number belongs  to  the  previous  or  next
              year, that year is used instead. (TZ)

       %g     Like  %G,  but  without  century,  that  is, with a 2-digit year
              (00-99). (TZ)

       %h     Equivalent to %b.  (SU)

       %H     The hour as a decimal number using a 24-hour clock (range 00  to
              23).

       %I     The  hour as a decimal number using a 12-hour clock (range 01 to
              12).

       %j     The day of the year as a decimal number (range 001 to 366).

       %k     The hour (24-hour clock) as a decimal number (range  0  to  23);
              single digits are preceded by a blank.  (See also %H.)  (TZ)

       %l     The  hour  (12-hour  clock) as a decimal number (range 1 to 12);
              single digits are preceded by a blank.  (See also %I.)  (TZ)

       %m     The month as a decimal number (range 01 to 12).

       %M     The minute as a decimal number (range 00 to 59).

       %n     A newline character. (SU)

       %O     Modifier: use alternative format, see below. (SU)

       %p     Either "AM" or "PM" according to the given time  value,  or  the
              corresponding  strings  for the current locale.  Noon is treated
              as "PM" and midnight as "AM".

       %P     Like %p but in lowercase: "am" or "pm" or a corresponding string
              for the current locale. (GNU)

       %r     The  time in a.m. or p.m. notation.  In the POSIX locale this is
              equivalent to %I:%M:%S %p.  (SU)

       %R     The time in 24-hour notation (%H:%M). (SU) For a version includ&#8208;
              ing the seconds, see %T below.

       %s     The number of seconds since the Epoch, that is, since 1970-01-01
              00:00:00 UTC. (TZ)

       %S     The second as a decimal number (range 00 to 60).  (The range  is
              up to 60 to allow for occasional leap seconds.)

       %t     A tab character. (SU)

       %T     The time in 24-hour notation (%H:%M:%S). (SU)

       %u     The  day of the week as a decimal, range 1 to 7, Monday being 1.
              See also %w.  (SU)

       %U     The week number of the current year as a decimal  number,  range
              00  to  53,  starting  with the first Sunday as the first day of
              week 01.  See also %V and %W.

       %V     The ISO 8601 week number (see NOTES) of the current  year  as  a
              decimal  number,  range 01 to 53, where week 1 is the first week
              that has at least 4 days in the new year.  See also %U  and  %W.
              (SU)

       %w     The  day of the week as a decimal, range 0 to 6, Sunday being 0.
              See also %u.

       %W     The week number of the current year as a decimal  number,  range
              00  to  53,  starting  with the first Monday as the first day of
              week 01.

       %x     The preferred date representation for the current locale without
              the time.

       %X     The preferred time representation for the current locale without
              the date.

       %y     The year as a decimal number without a century (range 00 to 99).

       %Y     The year as a decimal number including the century.

       %z     The time-zone  as  hour  offset  from  GMT.   Required  to  emit
              RFC 822-conformant   dates  (using  "%a, %d %b %Y %H:%M:%S %z").
              (GNU)

       %Z     The timezone or name or abbreviation.

       %+     The date and time in date(1)  format.  (TZ)  (Not  supported  in
              glibc2.)

       %%     A literal '%' character.

       Some conversion specifications can be modified by preceding the conver&#8208;
       sion specifier character by the E or O modifier  to  indicate  that  an
       alternative format should be used.  If the alternative format or speci&#8208;
       fication does not exist for the current locale, the behavior will be as
       if  the  unmodified conversion specification were used. (SU) The Single
       Unix Specification mentions %Ec, %EC, %Ex, %EX,  %Ey,  %EY,  %Od,  %Oe,
       %OH, %OI, %Om, %OM, %OS, %Ou, %OU, %OV, %Ow, %OW, %Oy, where the effect
       of the O modifier is to use alternative  numeric  symbols  (say,  roman
       numerals),  and  that  of  the  E modifier is to use a locale-dependent
       alternative representation.

       The broken-down time structure tm is defined  in  <time.h>.   See  also
       ctime(3).

RETURN VALUE
       The  strftime() function returns the number of characters placed in the
       array s, not including the terminating null byte, provided the  string,
       including  the  terminating  null byte, fits.  Otherwise, it returns 0,
       and the contents of the array is  undefined.   (This  behavior  applies
       since  at  least  libc  4.4.4;  very old versions of libc, such as libc
       4.4.1, would return max if the array was too small.)

       Note that the return value 0 does not necessarily  indicate  an  error;
       for example, in many locales %p yields an empty string.

ENVIRONMENT
       The environment variables TZ and LC_TIME are used.

CONFORMING TO
       SVr4, C89, C99.  There are strict inclusions between the set of conver&#8208;
       sions given in ANSI C (unmarked), those given in the Single Unix Speci&#8208;
       fication  (marked  SU), those given in Olson's timezone package (marked
       TZ), and those given in glibc (marked GNU), except that %+ is not  sup&#8208;
       ported  in  glibc2.   On  the other hand glibc2 has several more exten&#8208;
       sions.  POSIX.1 only refers to ANSI C; POSIX.2 describes under  date(1)
       several extensions that could apply to strftime() as well.  The %F con&#8208;
       version is in C99 and POSIX.1-2001.

       In SUSv2, the %S specifier allowed a range of 00 to 61,  to  allow  for
       the  theoretical  possibility  of  a minute that included a double leap
       second (there never has been such a minute).

NOTES
   ISO 8601 Week Dates
       %G, %g, and %V yield values calculated from the week-based year defined
       by the ISO 8601 standard.  In this system, weeks start on a Monday, and
       are numbered from 01, for the first week, up to 52 or 53, for the  last
       week.  Week 1 is the first week where four or more days fall within the
       new year (or, synonymously, week 01 is: the first week of the year that
       contains  a  Thursday;  or,  the  week that has 4 January in it).  When
       three of fewer days of the first calendar week of  the  new  year  fall
       within that year, then the ISO 8601 week-based system counts those days
       as part of week 53 of the preceding year.  For example, 1 January  2010
       is a Friday, meaning that just three days of that calendar week fall in
       2010.  Thus, the ISO 8601 week-based system considers these days to  be
       part  of  week 53 (%V) of the year 2009 (%G) ; week 01 of ISO 8601 year
       2010 starts on Monday, 4 January 2010.

   Glibc Notes
       Glibc provides some extensions for conversion  specifications.   (These
       extensions  are  not specified in POSIX.1-2001, but a few other systems
       provide similar features.)  Between the '%' character and  the  conver&#8208;
       sion specifier character, an optional flag and field width may be spec&#8208;
       ified.  (These precede the E or O modifiers, if present.)

       The following flag characters are permitted:

       _      (underscore) Pad a numeric result string with spaces.

       -      (dash) Do not pad a numeric result string.

       0      Pad a numeric result string with zeros even  if  the  conversion
              specifier character uses space-padding by default.

       ^      Convert alphabetic characters in result string to upper case.

       #      Swap  the case of the result string.  (This flag only works with
              certain conversion specifier characters, and  of  these,  it  is
              only really useful with %Z.)

       An  optional  decimal  width specifier may follow the (possibly absent)
       flag.  If the natural size of the field is  smaller  than  this  width,
       then the result string is padded (on the left) to the specified width.

BUGS
       Some  buggy  versions  of gcc(1) complain about the use of %c: warning:
       `%c' yields only last 2 digits of year in some locales.  Of course pro&#8208;
       grammers are encouraged to use %c, it gives the preferred date and time
       representation.  One meets all kinds of strange obfuscations to circum&#8208;
       vent this gcc(1) problem.  A relatively clean one is to add an interme&#8208;
       diate function

           size_t
           my_strftime(char *s, size_t max, const char *fmt,
                       const struct tm *tm)
           {
               return strftime(s, max, fmt, tm);
           }

       Nowadays, gcc(1) provides the -Wno-format-y2k  option  to  prevent  the
       warning, so that the above workaround is no longer required.

EXAMPLE
       The program below can be used to experiment with strftime().

       Some examples of the result string produced by the glibc implementation
       of strftime() are as follows:

           $ ./a.out '%m'
           Result string is "11"
           $ ./a.out '%5m'
           Result string is "00011"
           $ ./a.out '%_5m'
           Result string is "   11"

   Program source

       #include <time.h>
       #include <stdio.h>
       #include <stdlib.h>

       int
       main(int argc, char *argv[])
       {
           char outstr[200];
           time_t t;
           struct tm *tmp;

           t = time(NULL);
           tmp = localtime(&t);
           if (tmp == NULL) {
               perror("localtime");
               exit(EXIT_FAILURE);
           }

           if (strftime(outstr, sizeof(outstr), argv[1], tmp) == 0) {
               fprintf(stderr, "strftime returned 0");
               exit(EXIT_FAILURE);
           }

           printf("Result string is \"%s\"\n", outstr);
           exit(EXIT_SUCCESS);
       } /* main */

SEE ALSO
       date(1), time(2), ctime(3), setlocale(3), sprintf(3), strptime(3)

COLOPHON
       This page is part of release 3.23 of the Linux  man-pages  project.   A
       description  of  the project, and information about reporting bugs, can
       be found at [http://www.kernel.org/doc/man-pages/](http://www.kernel.org/doc/man-pages/).



GNU                               2009-09-28                       STRFTIME(3)

To the more advanced users out there who would be able to sort this out: I would like to use, firstly, Ubuntu with 24-hour time and the European day/month/year format.
Secondly, I would like to use Ubuntu with local metric time, as it was already requested by a user in 2006, and I also happen to like metric time.  For those who do not know, metric time consists of two times: Local Metric Time (LMT) and Universal Metric Time (UMT), which is equivalent to GMT.  In metric time, the base unit is the day.  The day is divided up into ten hours (decidays).  There are ten centidays (about fifteen minutes) in a deciday, and ten millidays (minutes) in a centiday.  Since the base unit is the day, the second is changed, and equates to 0.864 seconds.  Looking in terms of the date, there are ten days in a metric week (dekade), ten dekades in a metric month (centade, maybe?), and ten metric months in a metric year (millade, possibly?).
Metric time can be displayed as 8:02:41.  8 is the deciday, 0 is the centiday, 2 is the milliday, and 41, out of 100, is the microday, or metric second (0.864 seconds).
Ideally, I would like the clock to display the date in day/month/year.  Since the weekdays in metric time are Oneday, Twoday, Threeday, etc. up to Tenday, the dates should be written as 3/5/1337, not as Thr Fiv 1333.
We should create two versions, one with seconds, and one without seconds.  Keep in mind that seconds (microdays) update every 0.864 seconds.
Then again, since displaying the date in metric time has not been that clearly defined  yet, we could always use the regular ABT date, but still in d/m/y.  In that case, we could have three versions.
Thanks for your consideration of this, and thanks for your potential work!

---

### Post by Joseph Schwenker on 2010-11-12
If you're still confused about metric time, then check out [these]("http://zapatopi.net/metrictime/") [links]("http://www.minkukel.com/en/time/metric_clock.htm").

---

### Post by Joseph Schwenker on 2010-11-14
bump

---

### Post by Joseph Schwenker on 2010-11-20
bump

---

### Post by dcstar on 2010-11-20
> **Joseph Schwenker said:**
> bump

This is **not** a support question, is it really necessary to keep annoying people where this is obviously no interest?

---

### Post by Joseph Schwenker on 2010-11-20
> **dcstar said:**
> This is **not** a support question, is it really necessary to keep annoying people where this is obviously no interest?

There was a thread in 2006 where a user wanted to use their system in metric time, and now, in 2010, I want to use Ubuntu in metric time.  Instead of trashing the topic, why not contribute something related?  Getting Ubuntu to work with the systems that I use is a support issue for me.

---

### Post by dcstar on 2010-11-20
> **Joseph Schwenker said:**
> There was a thread in 2006 where a user wanted to use their system in metric time, and now, in 2010, I want to use Ubuntu in metric time.  Instead of trashing the topic, why not contribute something related?  Getting Ubuntu to work with the systems that I use is a support issue for me.

System enhancements are **not** support issues.

If you want something new then go to the appropriate places for that sort of thing, you are continually wasting yours and everyone elses' time here with a thread no one obviously want to contribute to.

How long are you going to indulge yourself with this?

---

### Post by cascade9 on 2010-11-20
Theres still people pushing base-10 time? LOL, I thought that had disappeared years ago....

---

### Post by Joseph Schwenker on 2010-11-20
> **cascade9 said:**
> Theres still people pushing base-10 time? LOL, I thought that had disappeared years ago....

Please stay on-topic.

---

### Post by cascade9 on 2010-11-20
If thats not 'on topic' then report me :P

---

### Post by Joseph Schwenker on 2010-11-20
> **cascade9 said:**
> If thats not 'on topic' then report me :P

The topic is understanding and applying the syntax for the time configuration, NOT which time system is better.  If you can't help me with metric time, then perhaps you could help me with my D/M/Y problem?

---

