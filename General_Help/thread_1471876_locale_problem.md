---
title: "locale problem"
date: 2010-05-03
forum: General Help
---

### Post by satimis on 2010-05-03
Hi folks,

Ubuntu Lucid

I have problem on locale

On running;
$ on typing
$ sudo nono /e[Tab]
it generates;
$ sudo nano /e-bash: warning: setlocale: LC_CTYPE: cannot change locale (zh_CN.UTF-8 )

$ sudo dpkg-reconfigure locales```

Generating locales...
  en_HK.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  zh_CN.UTF-8... up-to-date

```

I tried running;
$ sudo aptitude remove locales
then
$ sudo aptitude install locales

It didn't popup the window allowing me to select languages.

Please advise how to fix the problem.  TIA

B.R.
satimis

---

### Post by gmargo on 2010-05-04
The following was used to change locale to "en_GB.UTF-8", substitute your preferred locale, and reboot.

```

$ sudo locale-gen en_GB.UTF-8
$ sudo update-locale LANG=en_GB.UTF-8 

```

---

### Post by satimis on 2010-05-07
> **gmargo said:**
> The following was used to change locale to "en_GB.UTF-8", substitute your preferred locale, and reboot.

```

$ sudo locale-gen en_GB.UTF-8
$ sudo update-locale LANG=en_GB.UTF-8 

```

Hi gmargo,

Thanks for your advice.

After running a couple update and upgrade Lucid seems working nicely.

$ locale```

LANG=en_HK.UTF-8
LC_CTYPE="en_HK.UTF-8"
LC_NUMERIC="en_HK.UTF-8"
LC_TIME="en_HK.UTF-8"
LC_COLLATE="en_HK.UTF-8"
LC_MONETARY="en_HK.UTF-8"
LC_MESSAGES="en_HK.UTF-8"
LC_PAPER="en_HK.UTF-8"
LC_NAME="en_HK.UTF-8"
LC_ADDRESS="en_HK.UTF-8"
LC_TELEPHONE="en_HK.UTF-8"
LC_MEASUREMENT="en_HK.UTF-8"
LC_IDENTIFICATION="en_HK.UTF-8"
LC_ALL=

```

Do I need to run the commands suggested?  Thanks


B.R.
satimis

---

### Post by kibrun on 2010-09-06
I got the same problem. When i hit "tab" like what you normally do to go to the next level in directory (ie. cd /et[TAB] will give you /etc) the error will be produced. Mine said> bash: warning : setlocale: LC_TYPE: cannot change locale (en_US.UTF-8)

when i do 
$sudo dpkg-reconfigure locales
- it gives me:
Generating locales...
   en_US.UTF-8... up-to-date
Generation complete.

so how to fix this? hope can get some input since I do use tab to type in CLI. This warning message is really annoying. :confused:

---

### Post by surfer on 2010-09-06
i'd really be interested in that one as well!

---

### Post by gmargo on 2010-09-06
What do you get for the output of the **locale** command?

---

### Post by kibrun on 2010-09-06
> **gmargo said:**
> What do you get for the output of the **locale** command?

Mine put out exactly like the locale output command produced by "satimis" but replace the "en_HK" with "en_US". Sorry can't cut and paste because this one is on my ubuntu server (no GUI).

---

### Post by kibrun on 2010-09-07
newest update from me:

I visited my server again today and** rebooted **the server. To my surprise, the [tab] problem disappear. Don't know why but I'm happy. maybe the server just need a reboot.. it was running for 1 week after the last reboot.

so, case close for me. TQ. ):P

---

### Post by nnahler on 2011-05-02
I experienced the same problem using Ubuntu 10.04LTS (64bit).

I managed to fix it by adding the line:

#-----------------------
LC_ALL="en_GB.UTF-8"
#-----------------------

in /etc/default/locale

You can first test it in the terminal:

nnahler@xxxxxxx:~$ export LC_ALL="en_GB.UTF-8"

I hope that may help some other people.

---

### Post by sole2000 on 2011-05-09
Hi, I successfully installed and used jdatestamp to print date stamp on  my picture from exif information, but I have a locale problem.

When I want to print the name of the month in the date, i.e. 7 **may** 2011, I cannot get it in my language which is Italian, and therefore 7 **maggio** 2011.

I think to have some issue regarding locale settings, but I don't know how to fix it.

I run Ubuntu Lucid.

Thanks for help !!!

---

### Post by biocyberman on 2011-07-22
> **nnahler said:**
> I experienced the same problem using Ubuntu 10.04LTS (64bit).

I managed to fix it by adding the line:

#-----------------------
LC_ALL="en_GB.UTF-8"
#-----------------------

in /etc/default/locale

You can first test it in the terminal:

nnahler@xxxxxxx:~$ export LC_ALL="en_GB.UTF-8"

I hope that may help some other people.

This solved my problem with the same ubuntu version without restarting the server. Thanks :guitar:

---

### Post by sig_ on 2011-09-29
I did 

 export LC_ALL=en_US.UTF-8

and the problem just disappeared.

---

### Post by braun_schweiger on 2011-10-15
Thanks sig_, worked like a charm.

---

