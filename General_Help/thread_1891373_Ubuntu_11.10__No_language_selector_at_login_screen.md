---
title: "Ubuntu 11.10 : No language selector at login screen"
date: 2011-12-05
forum: General Help
---

### Post by fmmarzoa on 2011-12-05
Hi,

I cannot find the language selector on the login screen of my recently installed Ubuntu 11.10. I've installed both, Spanish and English, with Spanish by default, but sometimes I rather prefer to use English -most of the time, certainly-.

The best way to switch seems to be with language selector at login screen. The only problem is that I've no language selector at my login screen...

:confused:

Where is it supposed to be?

Thanks a lot in advance,

---

### Post by azertyh on 2011-12-05
hello,

i asked the same question : [http://ubuntuforums.org/showthread.php?t=1891144](http://ubuntuforums.org/showthread.php?t=1891144)

the right command is :
```
sudo gnome-language-selector
```

and with xubuntu, the application is in the menu parameters.

---

### Post by fmmarzoa on 2011-12-05
Hi,

I've yet configured that, but there was still no language selector on the login screen after.

As a workaround, I found that you can change the language for each users on System Settings / User Accounts, but this is a bit annoying if you want to switch often between languages.

Regards,

---

### Post by gordintoronto on 2011-12-05
> **fmmarzoa said:**
> ... I found that you can change the language for each users on System Settings / User Accounts, but this is a bit annoying if you want to switch often between languages.

Regards,

In many cases, this is what you want. I speak English, my wife speaks Chinese....

---

### Post by Flanmaster on 2012-01-02
And in many cases the new limitations are NOT what you want.  I am a student of languages and I practice by immersion, which includes using both the language and keyboard layouts of that language. I even use overlays for the keyboard when in a different language layout. I am still not fluent in several of the languages so I have to do configuration/software changes in my native language.

1) Different Phonetic languages have symbols in different locations for different keyboard Layouts. being able to choose the keyboard layout (language layout) at login addresses this.  but now all users are forced to use the system wide keyboard on login and have learn a different layout that they may not be used to, Additionally they have to select a password in the system layout instead of their own. this becomes especially irritating for asian, arabic, greek, hebrew, hindi,languages and others.

2) Students learning Different languages will often change language to native language when first logging in so they can add/alter configuration or software that they thought of when pc/lt not running. but now they have to login,  language, log out, log in, do configurations/software, change language, log out, log in.  Instead of change language @ login, do configuration/software, logout, change language at login.  Twice as many steps as before. 

So my question is what huge advantage did they gain by removing this feature, esp since they had it coded into lightdm at one point before the final release?  what makes it worth while to inconvenience many who use 
ubuntu specifically for it's (previous) flexibility on language selections, etc.?

---

