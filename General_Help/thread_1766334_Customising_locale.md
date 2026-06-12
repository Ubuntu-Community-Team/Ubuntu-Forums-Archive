---
title: "Customising locale"
date: 2011-05-24
forum: General Help
---

### Post by sridharpandu on 2011-05-24
I have installed 10.04 and wine for a friend. His windows app expects the date to be in dd-mm-yyy format. When I type locale I get the following output
LANG=en_IN
LC_CTYPE="en_IN"
LC_NUMERIC="en_IN"
[COLOR=Red]LC_TIME="en_IN"[/COLOR]
LC_COLLATE="en_IN"
LC_MONETARY="en_IN"
LC_MESSAGES="en_IN"
LC_PAPER="en_IN"
LC_NAME="en_IN"
LC_ADDRESS="en_IN"
LC_TELEPHONE="en_IN"
LC_MEASUREMENT="en_IN"
LC_IDENTIFICATION="en_IN"
LC_ALL=

I 'd like to change the date format reported by ubuntu to dd-mm-yyyy. Is it possible for me to change the format for LC_TIME by specifying it in the locale file or in the "en_IN" file if such a thing exits. Or is it possible to do it some other way? Searched several pages of threads but couldn't find a solution that works. Any help would be appreciated.

---

### Post by hwttdz on 2011-05-25
Could you be a little more specific with what you want to accomplish? You can find documentation for lc_time here: [http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap07.html](http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap07.html)
But if you just want to change the format of the date command the easiest way is to just use 'date +"%d-%m-%y"' did you really mean to have 3 digits for the year?  I'm not sure there's an elegant way to do that, but you could do
date +"%d-%m-0%y", which will work for the next 89 years or so.

---

