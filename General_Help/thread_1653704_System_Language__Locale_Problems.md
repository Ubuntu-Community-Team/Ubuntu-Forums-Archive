---
title: "System Language / Locale Problems"
date: 2010-12-27
forum: General Help
---

### Post by Doctor_Pain on 2010-12-27
Have been playing with Ubuntu 10.10, now have it installed and was trying to get an second Keyboard Input method (Russian) and accidentally installed a second system Language (Russian).

Thought I had managed to remove the second language, but now when I install anything from the terminal the messages that are output are in Russian, and odd Menu options are in Russian ?

When I Type Locales in the terminal I see......

lena@lena-VGN-SZ3XWP-C:~$ locale
LANG=en_GB.utf8
LANGUAGE=en_GB:ru:en
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

The LANGUAGE variable is showing en_GB;ru:en

I have changed this value in etc\environment to remove the ru, but it is still there when I type locale or printenv.

How do I remove the Russian variable, and will this solve my problem ? If not, how do I remove the Russian language completely from my system without a full install.

Here's a screen shot of one of menu options in Russian
[IMG]file:///home/lena/Desktop/Screenshot-Ubuntu%20Forums%20-%20Post%20New%20Thread-Mozilla%20Firefox.png[/IMG]

Thanks

---

### Post by Doctor_Pain on 2010-12-27
Ok...further searching directed me to this thread ,[http://ubuntuforums.org/showthread.php?t=1651256&highlight=language](http://ubuntuforums.org/showthread.php?t=1651256&highlight=language),  and I found the offending variable in my ~/.profile in this line at the end of that file

export LANGUAGE=en_GB:ru:en

Edited this to show

export LANGUAGE=en_GB:en

Rebooted my system and now all seems ok.

---

