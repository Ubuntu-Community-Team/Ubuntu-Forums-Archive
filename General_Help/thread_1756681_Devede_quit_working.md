---
title: "Devede quit working"
date: 2011-05-12
forum: General Help
---

### Post by ewaynec on 2011-05-12
I am using 10.04.
  I have used Devede for a year or more and it has worked great untill a couple of weeks ago. When I go on the menu and select it the menu goes away and nothing happens. When I run it fron the terminal I get;
devede

(process:751): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
DeVeDe 3.16.9
Locale: en_US
Using package-installed files
Traceback (most recent call last):
  File "/usr/bin/devede", line 138, in <module>
    locale.setlocale(locale.LC_ALL,"")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

 I do not know what this means, can someone help?
Thanks, Wayne

---

### Post by khelben1979 on 2011-05-12
It looks to me that the Devede software tries to adapt it's language settings from your Ubuntu system, and that it fails in doing so.

Does the software start up at all?

---

### Post by irv on 2011-05-12
When I have a App stop working, the first things I do is completely remove it. Then try re-installing it and sometimes this fixes the problem. It is worth a try. and sometimes the easy way is the best.

---

### Post by ewaynec on 2011-05-12
No, the program does not run. There is no indication that anything is happening.
  I tried to remove it and re-istall, same problem. I went to the website to look for answers, I found a newer version that I had. I downloaded and installed the upgrade. The problem persist, I don't know anything else to try.
  Wayne

---

### Post by khelben1979 on 2011-05-12
Have you checked if you got [Python]("http://en.wikipedia.org/wiki/Python_%28programming_language%29") correctly installed?

Also you can check that by doing a search for it in the [Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center").

---

### Post by irv on 2011-05-12
Besides checking for Python, Try running devede from the command prompt, and see if you get an error in the terminal. 
[ATTACH]191982[/ATTACH]
Also you need to make sure these packages are removed when installing Devede.
[ATTACH]191983[/ATTACH]

---

### Post by ewaynec on 2011-05-13
Thank you for your input.
  I have Python installed, this is what it showed;
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2

  I also checked to make sure the three programed listed are not installed.
  Don't give up on me yet.
   Wayne.

---

### Post by irv on 2011-05-13
I am running 11.04 and I was running 10.10 and it runs in both version. I have 10.04 on my server, I will try to run it on it and let you know if there is any problems.

EDIT: OK, I just installed it on my server (10.04) and it works great. It has something to do with your setup. Maybe a theme? Try changing your theme. This is going to be one of those trial and error things. Also try changing from Compiz to Metacity. I will have to look up the command to do this I forgot what it was.

---

### Post by ewaynec on 2011-05-13
While trying to find if there was another program that was acting like this, I found "aptocd" that does similar, (it tries to load). When I run from terminal it shows;

aptoncd

(process:2275): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/aptoncd", line 28, in <module>
    from APTonCD.core import constants
  File "/usr/lib/python2.6/dist-packages/APTonCD/core/constants.py", line 41, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

This looks a lot like the error I get when I run devede from terminal.(as shown in my original post. I don't understand either, I hope you do.
  BTW; everything else seems to work.
    Wayne

---

### Post by irv on 2011-05-13
OK, to switch from Compiz to Metacity press the Alt F2 and type in this command:
```
metacity --replace
```
Then try running devede
To switch back to compiz just do the Alt F2 again and type:
```
compiz --replace
```

---

### Post by jerome1232 on 2011-05-13
maybe reconfigureing your locale settings (this is your default language setting btw, have you messed with that recently?)

```
sudo dpkg-reconfigure locales
```

---

### Post by irv on 2011-05-13
After re-reading your post try this in a terminal. 
Type this command:
```
sudo dpkg-reconfigure locales
```

EDIT: sorry jerome1232 you got the jump on me.

---

### Post by ewaynec on 2011-05-13
I did as you said, with no positive results. here is what happened;

sudo dpkg-reconfigure locales
[sudo] password for wayne: 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

Devede still does not run.

---

### Post by ewaynec on 2011-05-13
I found this is another thread, tried it and it worked. I am going to test a few things and if it is OK I will come back and mark this solved.

locale-gen en_US en_US.UTF-8 hu_HU hu_HU.UTF-8

I think I know what this command is doing, but I would like to know why it is necessary. How did this get changed?
   Wayne.

  I have everything working now, Devede and Aptoncd are both working.
Thanks for the help. You didn't give me the solution, but you got me looking in the right place, and I would not have found it otherwise.

---

### Post by vlaporte on 2011-06-13
I could not start Devede after I upgraded PClinuxOS 2010 to 2010.12.
The error -- Error: unsupported locale setting.
I tried -- "locale-gen en_US en_US.UTF-8 hu_HU hu_HU.UTF-8" -- at command line but error - "locale-gen command not found".
Sooooo I concluded that I had a locales problem:
then I used Synaptic and installed "locales-en" and now we are GOOD.
I guess that "locales-en" got lost in the upgrade process.
Luck,
Vince

---

