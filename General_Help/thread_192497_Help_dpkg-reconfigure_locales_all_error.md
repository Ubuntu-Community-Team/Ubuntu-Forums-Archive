---
title: "Help: dpkg-reconfigure locales: all error"
date: 2006-06-08
forum: General Help
---

### Post by xoui on 2006-06-08
This is what I get when I do dpkg-reconfigure locales. And whenever I install something the "perl: warnig: setting locale failed" jump out. I believe this occur since I did the Chinese font smoothening. I tried to search in this forum and google and found no way so far. My kernel is 2.6.15-23-k7 and I checked English and Chinese in the Language Support. Anyone can help me? I am a newbie and I don't know what to do. :confused: 
> perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LC_PAPER = "en_GB.UTF-8",
        LC_ADDRESS = "en_GB.UTF-8",
        LC_MONETARY = "en_GB.UTF-8",
        LC_NUMERIC = "en_GB.UTF-8",
        LC_TELEPHONE = "en_GB.UTF-8",
        LC_MESSAGES = "en_GB.UTF-8",
        LC_COLLATE = "en_GB.UTF-8",
        LC_IDENTIFICATION = "en_GB.UTF-8",
        LC_MEASUREMENT = "en_GB.UTF-8",
        LC_CTYPE = "zh_CN.GBK",
        LC_TIME = "en_GB.UTF-8",
        LC_NAME = "en_GB.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
Error: Bad entry 'POSIX '
  en_AU.UTF-8... up-to-date
Error: Bad entry 'en_AU.utf8 '
  en_BW.UTF-8... up-to-date
Error: Bad entry 'en_BW.utf8 '
  en_CA.UTF-8... up-to-date
Error: Bad entry 'en_CA.utf8 '
  en_DK.UTF-8... up-to-date
Error: Bad entry 'en_DK.utf8 '
  en_GB.UTF-8... up-to-date
Error: Bad entry 'en_GB.utf8 '
  en_HK.UTF-8... up-to-date
Error: Bad entry 'en_HK.utf8 '
  en_IE.UTF-8... up-to-date
Error: Bad entry 'en_IE.utf8 '
Error: Bad entry 'en_IN '
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
Error: Bad entry 'en_NZ.utf8 '
  en_PH.UTF-8... up-to-date
Error: Bad entry 'en_PH.utf8 '
  en_SG.ISO-8859-1... up-to-date
  en_SG.UTF-8... up-to-date
Error: Bad entry 'en_SG.utf8 '
  en_US.UTF-8... up-to-date
Error: Bad entry 'en_US.utf8 '
  en_ZA.UTF-8... up-to-date
Error: Bad entry 'en_ZA.utf8 '
  en_ZW.UTF-8... up-to-date
Error: Bad entry 'en_ZW.utf8 '
Error: Bad entry 'zh_CN '
  zh_CN.GB2312... up-to-date
  zh_CN.UTF-8... up-to-date
Error: Bad entry 'zh_CN.utf8 '
  zh_HK.UTF-8... up-to-date
Error: Bad entry 'zh_HK.utf8 '
  zh_SG.UTF-8... up-to-date
Error: Bad entry 'zh_SG.utf8 '
  zh_TW.UTF-8... up-to-date
Error: Bad entry 'zh_TW.utf8 '
Generation complete.
Current default timezone: 'Asia/Singapore'.
Local time is now:      Fri Jun  9 08:31:08 SGT 2006.
Universal Time is now:  Fri Jun  9 00:31:08 UTC 2006.
Run 'tzconfig' if you wish to change it.


---

