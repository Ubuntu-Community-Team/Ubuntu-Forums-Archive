---
title: "Date format does not follow locale."
date: 2010-06-12
forum: General Help
---

### Post by jatoo on 2010-06-12
The date displayed in my panel is in the American format: Sat Jun 12, but my locale is set to Australian for everything.  I have tried switching to different regions (System->Administration->Language Support), but this appears to have no effect on the date format.

Is this a bug?  Anyone know how to fix it?.

Thanks!

(Ubuntu 10.04)

```
$ locale
LANG=en_AU.utf8
LC_CTYPE="en_AU.utf8"
LC_NUMERIC="en_AU.utf8"
LC_TIME="en_AU.utf8"
LC_COLLATE="en_AU.utf8"
LC_MONETARY="en_AU.utf8"
LC_MESSAGES="en_AU.utf8"
LC_PAPER="en_AU.utf8"
LC_NAME="en_AU.utf8"
LC_ADDRESS="en_AU.utf8"
LC_TELEPHONE="en_AU.utf8"
LC_MEASUREMENT="en_AU.utf8"
LC_IDENTIFICATION="en_AU.utf8"
LC_ALL=
```

---

### Post by dcstar on 2010-06-12
> **jatoo said:**
> The date displayed in my panel is in the American format: Sat Jun 12, but my locale is set to Australian for everything.  I have tried switching to different regions (System->Administration->Language Support), but this appears to have no effect on the date format.
........

Gconf key:

```
/apps/panel/applets/clock_screen0/prefs/custom_format
```
I use:
```
%a %d/%m/%y %T
```

---

### Post by jatoo on 2010-06-12
Thanks David,

My gconf-editor doesn't have that item.  In /apps/panel/ there is no applets, only default_setup, general and global.  Under default_setup there is an applets folder which contains 'clock' but no clock_screen0, and it doesn't have prefs or custom format.

I've had a look through and I can't find anything like that in gconf-editor.

Shouldn't this format be changed by the system settings anyway?

---

### Post by dcstar on 2010-06-13
> **jatoo said:**
> Thanks David,

My gconf-editor doesn't have that item.  In /apps/panel/ there is no applets, only default_setup, general and global.  Under default_setup there is an applets folder which contains 'clock' but no clock_screen0, and it doesn't have prefs or custom format.
.........

I have now checked 3 different 10.04 systems and that gconf key exists in all of them.

---

### Post by golanbatrac on 2010-06-13
How are you opening gconf-editor?

You don't need to sudo to modify anything in gconf-editor.  Try it without.  It should be exactly as dcstar described.

---

### Post by hawthornso23 on 2010-06-13
It is questionable just how strongly linked long date formats really are to locale. 

Most people in a given locale are quite capable of reading dates equally well in a variety of long formats and they may in fact use several formats with equal facility themselves.  Which long date format to use is thus in large part a matter of personal preference and not locale, with most people expressing no strong preference and being quite willing to read dates in any format, but with a small minority professing to be annoyed if the date isn't written in a certain way.

Abbreviated date formats are somewhat different and are more strongly locale linked.

---

### Post by jatoo on 2010-06-13
Thanks guys, i was using sudo. :roll:

My menu is exactly as described without.

Problem now however is that modifying custom_format doesn't appear to have any effect.  I've tried several different formats, even simple ones like just %d, but nothing.  I also tried your example, dcstar (and thanks for checking those systems), but it doesn't have any effect. 

Any idea why this could be?

Thanks again!

---

### Post by golanbatrac on 2010-06-13
In the same place (apps >panel > applets > clock_screen0 > prefs) set **format = custom**.

---

### Post by jatoo on 2010-06-13
Thanks for that, working now, i guess i really needed it spelled out for me this time.

hawthornso23, i'm sure in most (if not all) regions people are capable of reading the date in all formats, so i agree it's not a big issue, but different regions do have different standards for date formats, primarily 'month day year' being American and 'day month year' being Commonwealth.  The thing is just that in the language settings (System->Administration->Language Support, Text tab) changing the region says it will change number currency and date formats, but doesn't in this case.

---

