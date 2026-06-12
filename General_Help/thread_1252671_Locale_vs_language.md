---
title: "Locale vs language"
date: 2009-08-29
forum: General Help
---

### Post by dixon on 2009-08-29
Hi,
I've always preferred English language when it comes to OS. But at the same time I want to have Slovak locales. So basically what I want - I want to have all the text in English, but I want my hours format to be set to 24h by default, firefox preffered language to be set to Slovak, default Number delimeter to be "," instead of "." in all applications etc.... Is this possible?

---

### Post by bertilow on 2009-08-29
I don't think that is possible in Ubuntu. Interface language and locale are interrelated in a very illogical way. I have not managed to separate my Esperanto locale from the interface language for the programs. Some programs insist on using the (bad) Esperanto translations just because I use an Esperanto locale.

These things should be completely separated, but that's not the case in Ubuntu.

You can however set your preffered language in Firefox to anything you like. That's not dependent on the locale of your system.

---

### Post by dixon on 2009-08-29
I know I can set my preferred language in Firefox as in many other applications. I just wanted to set by default all the default and newly installed language specific part of applications to Slovak, just leave the language (all the text etc.) to English.

If it's true that I can't set it apart. It means I have two choices 
1) Use English language and change all the language specific stuff in my OO, Firefox and every newly installed application.
2) Use Slovak language by default

None of these two options really suits me :(

---

### Post by Leor on 2009-09-15
Basically, I had the same problem. So, in my case I wanted to have the English language and on the same time have the locale monetary settings for the Netherlands.

What I did was:

1) edit the file /etc/default/locale
2) changed it to:[INDENT]LANG="en_US.UTF-8" 
LC_MONETARY="nl_NL.UTF-8"
[/INDENT]3) reboot
4) In this case I have the en_US language settings and the monetary settings nl_NL. Other settings seems to default to en_US.
5) At least GNUcash changed the way i wanted. (Did not try other programs.)
6) I assume other locales can be changed in a similar manner, found under /usr/lib/locale/en_US.utf8: LC_ADDRESS, LC_COLLATE, LC_CTYPE, LC_IDENTIFICATION, LC_MEASUREMENT, LC_MESSAGES, LC_MONETARY, LC_NAME, LC_NUMERIC,  LC_PAPER, LC_TELEPHONE, LC_TIME

---

### Post by dixon on 2009-09-15
> **Leor said:**
> Basically, I had the same problem. So, in my case I wanted to have the English language and on the same time have the locale monetary settings for the Netherlands.

What I did was:

1) edit the file /etc/default/locale
2) changed it to:[INDENT]LANG="en_US.UTF-8" 
LC_MONETARY="nl_NL.UTF-8"
[/INDENT]3) reboot
4) In this case I have the en_US language settings and the monetary settings nl_NL. Other settings seems to default to en_US.
5) At least GNUcash changed the way i wanted. (Did not try other programs.)
6) I assume other locales can be changed in a similar manner, found under /usr/lib/locale/en_US.utf8: LC_ADDRESS, LC_COLLATE, LC_CTYPE, LC_IDENTIFICATION, LC_MEASUREMENT, LC_MESSAGES, LC_MONETARY, LC_NAME, LC_NUMERIC,  LC_PAPER, LC_TELEPHONE, LC_TIME

Thank you very much, I'll definitely try that...

---

### Post by pete.urban on 2009-09-23
Could you help me how can I change the character encoding for gnome-terminal? I want to use iso-8859-2 instead of utf-8.
I tried to change it in /etc/default/locale but it still won't work :(

Regards,
Pete

---

### Post by rolandjo on 2009-11-16
Hello to all,
I find a solution in a post related to Gimp language issue.

In Ubuntu, go to System->Preferences->Main Menu.
Find GnuCash (under Office), rightclick on it and select properties,
where it says **Command**, change 
```
gnucash %f  
```to 
```
env LANGUAGE=ro gnucash %f 
```If you want a different language than Romanian ;) (in my case) simply change **ro** from 
LANGUAGE=**ro** to **sl **(Slovak) I gues, in your case.

**Be advice that **

[LIST=1]
[*] you need to create your accounts from start again, (is better to export your accounts and other transactions before you change your language) in my case it was easy because is the firs time when I use Gnucash,
[*]you need to have bouth language instaled in your machine.
[/LIST]
 
All the best,

Roland

---

