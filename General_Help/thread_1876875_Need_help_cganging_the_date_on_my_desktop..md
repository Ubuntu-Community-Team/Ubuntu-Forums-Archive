---
title: "Need help cganging the date on my desktop."
date: 2011-11-07
forum: General Help
---

### Post by Spc 4 on 2011-11-07
My clock says: Day/ Month/ Date/ Time. How do you change it to: Day/ Date/ Month/ Time?

---

### Post by DapperMe17 on 2011-11-07
Right click to "properties" on your clock applet....then change the time format with any combination of the following...

Codes;
%% a literal %
%a locale's abbreviated weekday name (e.g., Sun)
%A locale's full weekday name (e.g., Sunday)
%b locale's abbreviated month name (e.g., Jan)
%B locale's full month name (e.g., January)
%c locale's date and time (e.g., Thu Mar 3 23:05:25 2005)
%C century; like %Y, except omit last two digits (e.g., 21)
%d day of month (e.g, 01)
%D date; same as %m/%d/%y
%e day of month, space padded; same as %_d
%F full date; same as %Y-%m-%d
%g last two digits of year of ISO week number (see %G)
%G year of ISO week number (see %V); normally useful only with %V
%h same as %b
%H hour (00..23)
%I hour (01..12)
%j day of year (001..366)
%k hour ( 0..23)
%l hour ( 1..12)
%m month (01..12)
%M minute (00..59)
%n a newline
%p locale's equivalent of either AM or PM; blank if not known
%P like %p, but lower case
%r locale's 12-hour clock time (e.g., 11:11:04 PM)
%R 24-hour hour and minute; same as %H:%M
%s seconds since 1970-01-01 00:00:00 UTC
%S second (00..60)
%t a tab
%T time; same as %H:%M:%S
%u day of week (1..7); 1 is Monday
%U week number of year, with Sunday as first day of week (00..53)
%V ISO week number, with Monday as first day of week (01..53)
%w day of week (0..6); 0 is Sunday
%W week number of year, with Monday as first day of week (00..53)
%x locale's date representation (e.g., 12/31/99)
%X locale's time representation (e.g., 23:13:4
%y last two digits of year (00..99)
%Y year
%z +hhmm numeric timezone (e.g., -0400)
%Z alphabetic time zone abbreviation (e.g., EDT)


Example is....%l:%M%p (which will read something like 3:45pm)

---

### Post by Spc 4 on 2011-11-07
You see what you did? This is the kind of BS that turns people off from Linux. No easy to understand answer. [DapperMe17]("http://ubuntuforums.org/member.php?u=193830") is this the best answer? or are you just trying to show how smart you are? I can not get ( Right click to "properties" on your clock applet) to work.

---

### Post by critin on 2011-11-07
> How do you change it to: Day/ Date/ Month/ Time?

Which version are you running?

---

### Post by FootySr on 2011-11-07
Ask for help, get help, get face spit on! lol

Funny transaction! :)

I'm certain he is trying to be helpful Spc 4, I went and looked about the clock settings too, just to see if it was possible. Maybe that would work for a non Unity version of Ubuntu, not sure but you could give more information like your version number too, maybe that would help.

---

### Post by Spc 4 on 2011-11-08
I apologise for sounding rude, I just get a little frustrated some times.  Any way I am running Ubuntu11.10 I have used Ubuntu for 4 years now and this is my first time using Unity, and I am still finding my way around the interface.

---

### Post by howefield on 2011-12-20
Try clicking on the Power icon on the top panel and select System Setting > Language Support > Regional Formats and have a play in there.

Any changes you make may need a logout/login to take effect.

---

### Post by stinkeye on 2011-12-20
In 11.10 you need to run dconf-editor to change the date format.
dconf-editor is in the **dconf-tools** package.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=11503654#post11503654").
This command in terminal will change as shown in attached pic...uses 12hour format.
```
gsettings set com.canonical.indicator.datetime time-format custom && gsettings set com.canonical.indicator.datetime custom-time-format "%a %e %b %l:%M%P"
```

---

