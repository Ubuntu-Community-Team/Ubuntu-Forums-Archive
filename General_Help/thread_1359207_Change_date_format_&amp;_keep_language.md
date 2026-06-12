---
title: "Change date format &amp; keep language?"
date: 2009-12-19
forum: General Help
---

### Post by bovender on 2009-12-19
Hi all,

I would like to change the date & time formats of my Ubuntu 9.10 system to the German locale while keeping the English language for all applications. How can I do this? In Windows, it was very easy to customize any of these settings (including currency and number formats as well) in the Control Panel, but I can't find an equivalent in "Linux for human beings".

Please don't tell me I have to edit config files from the command line, although if this is the only way to accomplish it, I'd probably have to swallow that pill I guess... ;-)

Thanks

---

### Post by avanhel on 2010-01-06
I just found a simple solution to the problem I had as well.

use menu System-> Administration -> Language support 
then choose the language English United Kingdom. This wil change all the settings to europe but it will keep the English language.

It worked for me

---

### Post by bovender on 2010-01-07
Hi,

thanks for the suggestion. That will at least fix the way the date is written (Day-Month-Year instead of Month-Day-Year). However, it would be great if I could also have the numbers written in a different way, i.e. use a comma instead of a dot as a decimal separator.

---

### Post by size_XXM on 2010-01-07
Read [this](http://publib.boulder.ibm.com/infocenter/wmbhelp/v6r0m0/index.jsp?topic=/com.ibm.etools.mft.doc/ae19494_.htm) or [this](http://www.linux.com/archive/feature/53781).
It lists the locale-related variables and which have precedence over others, and which are used when a specific variables (collation, paper..) are not set. You ma need to run a command or two to "compile" some locales (sorry, can't remember what was necessary, I did this a long time ago).

I think I'm in the same boat as you - want the English interface, everything else "local", in my case Slovak. I use KDE and tried the preferences for International configuration, but it only affected KDE apps and (I think) only the current user - not that useful for me, as I'm in the terminal or non-KDE apps quite often. My solution - works for _most_ apps (smplayer and googleearth ignore this), is to edit **/etc/default/locale** (backup the existing one, of course) and set LANG to (for your case) German and LC_MESSAGES to English. You'll probably want to keep UTF8 encoding if you're using it already. (Mixing different encodings is not recommended) My /etc/default/locale file contains:```
LANG="sk_SK.UTF-8"
LC_MESSAGES="en_US.UTF-8"
```. Reboot and you should be done. To check locale, run the locale command:```
$ locale
LANG=sk_SK.UTF-8
LANGUAGE=
LC_CTYPE="sk_SK.UTF-8"
LC_NUMERIC="sk_SK.UTF-8"
LC_TIME="sk_SK.UTF-8"
LC_COLLATE="sk_SK.UTF-8"
LC_MONETARY="sk_SK.UTF-8"
LC_MESSAGES=en_US.UTF-8
LC_PAPER="sk_SK.UTF-8"
LC_NAME="sk_SK.UTF-8"
LC_ADDRESS="sk_SK.UTF-8"
LC_TELEPHONE="sk_SK.UTF-8"
LC_MEASUREMENT="sk_SK.UTF-8"
LC_IDENTIFICATION="sk_SK.UTF-8"
LC_ALL=
```

Bonus: for programs which ignore the LC_MESSAGES variable, you should be able to use the *env* tool to change the LANG variable for that program only - this will make the program see everything set to english:```
$ env LANG="en_US.UTF-8" locale
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES=en_US.UTF-8
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

---

### Post by bovender on 2010-01-12
Hi,

thanks for the info. Somehow I managed to mess up my system though, I get this now when I enter the "locale" command into a terminal:

```

LANG=C
LANGUAGE=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=

```

The content of my /etc/default/locale file is this now (reverted back to the old version after playing with de_DE locales):

```

LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

```

This is a problem because I get all kinds of problems now, e.g. rsync cannot handle file names that contain German umlauts, etc.

How can I make the system respect the content of /etc/default/locale?????

Thanks!

---

### Post by size_XXM on 2010-01-12
Umm, what was your locale before you changed the config file? As for filenames - yes, that does happen, so be careful and after you get the locale  set up, reboot the computer to re-mount the partitions with UTF-8 encoding.

If I remember correctly, the other steps involved the locale compilation/installation using the *localedef* utility - See the linux.com article for more details. The charmaps directory they reference is in /usr/share/i18n/, so the command you need would go like this I think:
```
localedef -i de_DE -f /usr/share/i18n/charmaps/UTF-8 de_DE
localedef -i en_US -f /usr/share/i18n/charmaps/UTF-8 en_US
```
Other than that, you need to run
```
sudo dpkg-reconfigure locales
```I'm not sure if you need to run it before or after the localedef command. It says which locales it's configuring, so make sure it mentions both de_DE and en-US. My example:
```
$ sudo dpkg-reconfigure locales
Generating locales...
  en_US.UTF-8... up-to-date
  sk_SK.UTF-8... up-to-date
Generation complete.

```

Also, either I'm  misunderstanding what it is you want to achieve, or you're misunderstanding the locale variable hierarchy. See:> If the appropriate component-specific environment variable -- e.g. LC_COLLATE -- is set and non-null, its value is used.
If the LANG environment variable is defined and is not null, its value is used.
Reading your first post, what you want is to set LANG to de_DE and LANGUAGE and LC_MESSAGES to en_US.

Edit: Specifcally, your /etc/default/locale should read:
```
LANG="de_DE.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LANGUAGE="en_US:de_DE"
```

---

### Post by bovender on 2010-01-12
Thanks for the quick response.

In my previous post I showed the current settings after I had stopped playing around with German locale variables, and tried to revert everything back to English. That's why it looked like I hadn't gotten the point of the different locale variables.

I tried your suggestions, to no avail. But when I used the System->Administration->Language support command now to set the language, the problem with the "C" locale that I had shown in my previous post was finally fixed.

This is what I have now:

```
$ more /etc/default/locale
LANG="en_US.UTF-8"
LANGUAGE="en_US.UTF-8:en_GB:en"
LC_MESSAGES="en_US.UTF-8"
LC_TIME="de_DE.UTF-8"
LC_MONETARY="de_DE.UTF-8"
```

And this is the output of locale:

```
$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME=de_DE.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=de_DE.UTF-8
LC_MESSAGES=en_US.UTF-8
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

(What's interesting here is that those variables that I manually defined in the /etc/default/locale file appear without quotes, while all the other (automatic) variables appear with quotes.)

Of note, the date & time applet in the Gnome panel still shows the American date ("Jan 12"), however with German names ("Di Jan 12" instead of "Tue Jan 12"). When I type "date" in a terminal, I get an all-German output:

```
$ date
Di 12. Jan 09:12:56 EST 2010
```

Thunderbird's Lightning calendar does not care at all about the locale settings.

It would be great if there was a way to define your own date/time formats, for example -- the way other operating systems can do it (e.g. Windows which allows full customization).

I still don't entirely understand all of the ins and outs of Linux locales, but at least it sort of works now. Thanks for your help!

---

