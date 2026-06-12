---
title: "Ubuntu 12.04 Switches Language"
date: 2012-04-29
forum: General Help
---

### Post by phosphide on 2012-04-29
Hi all,

I did a fresh install of 12.04 two days ago and was not having any problems. However, when I turn on my machine today, somehow the language switched to Chinese. I never once did anything with chinese and the only changes I have made were going back to the gnome panel.

i tried removing the chinese languages from the terminal and re-installing the english, but still no avail. I eventually went into user accounts and clicked english as the language (which was in Chinese), rebooted, and that worked. Though, I can't figure out why it changed. Is this a bug? If so, how can I find out? Is there anywhere that logs when it is changed?

---

### Post by merlinus on 2012-04-29
This just happened to me!  (see earlier post)

How did you figure out which one was English in the User Accounts list?

---

### Post by merlinus on 2012-04-30
Trial and error solved the problem for now, but is there any way to report this as a bug to be fixed?

---

### Post by gman16000 on 2012-04-30
i had a fresh install of 12.04 from the weekend.  it switched as well. 

definitely making my day non-fun. bugs like these are embarrassing when i'm recommending colleges to give ubuntu a try.

---

### Post by ABE3K on 2012-04-30
Same thing happened here .... anyway to rollback through the terminal?

Edit:

gksudo gedit /etc/default/locale

then modify as follows

LANG="en_GB"
LANGUAGE="en_GB:en"

then reboot

---

### Post by Francisco Serrano on 2012-04-30
:( Same problem. It select Chinese without reason after a reboot in a fresh Ubuntu 12.04 (not an upgrade) set to Spanish that worked fine in a spanish environment for two days.  

Is a very frustrating bug. Even if you know gnome-language-selector  :confused:  and you are able to find it in a semi-Chinese environment :-k,   the program is  useless as any help inside is completely in Chinese  #-o (except if you know Chinese, of course). 

To  survive to this environment,  I open a terminal  (Crtl-Alt_T) to change locale LANG=zh_CN.UTF-8  by LANG=es_ES.UTF-8 and then launch gnome-language-selector (from the terminal) to use it in spanish.  However, after making the changes  to put Spanish first (as root and as  normal user) and reboot, the locale is again zh_CN.UTF-8 ](*,) Then I tried to run (with and without sudo) run  locale-gen and dpkg-reconfigure locales,  which seem generated well only the en_XX.UTF-8 and es_XX.UTF-8 locales and finally I edit /etc/default/locale to see that all is set with es_ES.UTF-8 or es_ES:en  (without  any reference to chinese locale): After another reboot seem that the problem was solved.

---

### Post by Tobsi on 2012-04-30
For me, I had the same bug. However fix was easy, I did change .pam_environment and set both LANG=en_EN and Language=en_EN
I did also the steps above, but this was not sufficient
Hope this helps others
Tobsi

---

### Post by sacadough on 2012-05-01
I also had this problem after the first automatic update of 12.04.  To recap the solution (by ABE3K and Tobsi):

1) edit /etc/default/locale:
LANG="en_GB"
LANGUAGE="en_GB:en"

2) edit ~/.pam_environment:
LANG=en_EN
Language=en_EN

Use en_US if you are American.  Then reboot.

---

### Post by TeamOliva on 2012-07-07
Much easier fix.

Go to "System Settings"

Open "User Accounts"

Change your "Language" to whatever the very 1st selection is.

Then "Restart"

---

### Post by RogerDavis on 2012-08-09
Mine switched to Chinese after setting numeric keypad in System Settings.  Maybe the Chinese computer spy operation extends to Ubuntu?

---

### Post by Austin Texas on 2012-08-09
I can't believe it took 10 posts for someone to say that Big Blother is watching.

---

### Post by DarwinSurvivor on 2012-08-10
My /etc/default/locale was corrent (en_CA for Canadian), by ~/.pam_environment was all chinese though. Simply "rm ~/.pam_environment" and then logging out/in fixed it for me. Mine was the only account on the whole system (out of 4) that even HAD a .pam_environment file! WTF?

---

### Post by Bramkaandorp on 2012-10-22
> **TeamOliva said:**
> Much easier fix.

Go to "System Settings"

Open "User Accounts"

Change your "Language" to whatever the very 1st selection is.

Then "Restart"

Rather late, but still very important:

I tried this, but the list of languages is in Chinese symbols, so I don't know which one to choose. I need Dutch, but I can't make heads or tails of it.

---

### Post by Bramkaandorp on 2012-10-22
It's al-right now.

Here's the thing. In the system settings there is a "language" section, in which a list of languages is shown. The language at the top is the default language. For me, it was Dutch (as it should be), but that clearly wasn't the case, because half of the things on my computer were in Chinese (if not more), some in English, and the rest (which was very little )was in Dutch.

I don't know what the long-term repercussions are, but I removed Ibus. It started at start-up (though it wasn't in the start-up list), and after I removed it and restarted, I could see that Chinese was at the top of the language list. So I put it to the bottom (rendering it greyed) and put Dutch up top thereby. Then I applied it system wide (I had to guess which of the two buttons did it, but luckily the other button did nothing definite).

And here's why I removed Ibus: It gave two options to select, and they were both some form of Chinese. So after removing those two from the list didn't do anything (they were back after restarting), I figured: "If I break my computer by removing it, at least I know that I was the one who screwed it up, and not a program". That, and the fact that I have all of my files safely backed up at all times, gave me enough confidence to push through.

After the restart, everything is back to normal.

I will however do a virus-scan to be safe.

---

### Post by Orbitize on 2013-01-30
This happened to me, even though I am running Mint 14.

My /etc/default/locale is as follows:
LANG="en_US.UTF-8"

but my .pam_environment looks like this:
```
LANGUAGE=zh_CN:en
LANG=zh_CN.UTF-8
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_US.UTF-8
LC_MONETARY=en_US.UTF-8
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8
```

I have found a workaround, but not fix:
in my users .profile at the end I added:
```
LANG=en_US.UTF-8
LANGUAGE=en_US:en
```


The thing is I don't think this is because of any setting on my normal user. When I switch to root and check locale or locale -a I get the same output. Furthermore, when I do aptitude update, I see it still looking for Chinese translations:
```

...
Hit http://archive.ubuntu.com quantal/main Translation-en                                                                                                          
Hit http://archive.ubuntu.com quantal/main Translation-zh_CN                                                                                                                                    
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages                                                                                          
Ign http://archive.canonical.com quantal/partner Translation-en_US                                                                                                                              
Ign http://archive.canonical.com quantal/partner Translation-en      
...

```

So anyone have any idea what might be causing this and how to fix it properly?

---

