---
title: "Firefox search .com rather than .co.uk after 10.04 upgrade"
date: 2010-05-03
forum: General Help
---

### Post by r-senior on 2010-05-03
I've only just spotted this, but after upgrading (upgrade, not clean install) from 9.10 to 10.04 (both Ubuntu and Xubuntu), my Firefox search is using .com, e.g. google.com, rather than .co.uk. So, for example, if I search for "cheap laptop" I get things coming up in USD. Or eBay search takes me to eBay.com.

I've searched the forum and through Firefox settings but can't see anything. Now, I could go to "Manage Search Engines" in Firefox and install .co.uk variants but is there an easy way?

I'm on a fixed IP with a .co.uk domain BTW, and Firefox was giving be localised searches before upgrade. 

Any ideas?

---

### Post by Dayofswords on 2010-05-03
check your location settings, maybe they got changed from the upgrade

other than that i have no idea

---

### Post by r-senior on 2010-05-03
In Ubuntu (if so where? - About Me?) or Firefox (if so where?)?

```

richard$ locale
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

---

### Post by dino99 on 2010-05-03
firefox choice prefs to tweak

---

### Post by warfacegod on 2010-05-03
> **r-senior said:**
> In Ubuntu (if so where? - About Me?) or Firefox (if so where?)?

```

richard$ locale
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

System> Admin.> Time & Date Settings> click the padlock icon on the bottom.

---

### Post by r-senior on 2010-05-03
Edit - Preferences - Content - Languages is set to en_GB
Edit - Preferences - General - Manage Add Ons - Languages only has en_GB

???

---

### Post by r-senior on 2010-05-03
> **warfacegod said:**
> System> Admin.> Time & Date Settings> click the padlock icon on the bottom.
Yup - looked at that - that's set to Europe/London.

---

### Post by Vaphell on 2010-05-03
check in about:config -> distribution.searchplugins.defaultLocale.

maybe you got en-US instead of en-GB there or something.

---

### Post by lovinglinux on 2010-05-03
Check **keyword.URL** preference in **about:config**.

---

### Post by r-senior on 2010-05-03
Thanks for all your suggestions. Certainly distribution.searchplugins.defaultLocale was set to en-US and I've set that to en-GB.

But, I think I may have been throwing you all a red herring. If I type "Manchester", regardless of the setting of the above, I get my local one in the UK, so it appears localised. For some reason though, the "Shopping Results For ..." entry in Google is still showing US products.

I'll have a stew on this. Maybe it' a Google glitch? I honestly don't remember exactly whether these shopping results ever came up in GBP using the default Google. Maybe I do need to add the google.co.uk search engine. I tried keyword.URL but that didn't seem to make any difference.

I'll mark as "Solved", because there isn't a "totally confused" option. ;)

---

### Post by tobsco on 2010-05-22
Or you can go to

/usr/lib/firefox-addons/searchplugins/en-US

and edit the file google.xml. Simply replace every .com with a .co.uk and everything will work fine.
Don't forget that you need root privileges to edit this file so use

```
gksudo nautilus /usr/lib/firefox-addons/searchplugins/en-US
```

to open the file.

There is also an en-GB folder with a google.xml file in it, I changed both but i'm not sure which one is used.

---

