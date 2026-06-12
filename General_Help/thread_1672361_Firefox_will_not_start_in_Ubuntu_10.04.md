---
title: "Firefox will not start in Ubuntu 10.04"
date: 2011-01-20
forum: General Help
---

### Post by nam42589 on 2011-01-20
Everytime I try to open firefox i keep getting this message 
"We're Sorry
Firefox had a problem and crashed. We'll try to restore your tabs and windows when it restarts.

To help us diagnose and fix the problem, you can send us a crash report."

I restarted it, updated it, reinstalled it, but it still wont work. I do not know whats wrong with this, I am running in Ubuntu 10.04 LTS, everything was working fine and now all of the sudden it stopped running. If anyone could please help me, it would be greatly appreciated.

Thank you in advance

---

### Post by Ex_Machina on 2011-01-20
try:
```
apt-get purge <firefox package>
```
and then:
```
apt-get install <firefox package>
```

It will entirely remove FF with all config files.
Btw, I like the FF error message, makes me think of that DP episode of south park with coon and friends 2 :')

---

### Post by mikewhatever on 2011-01-20
Any extension?  Try starting Firefox in safe mode - **firefox -safe-mode** -.

---

### Post by nam42589 on 2011-01-21
@Ex-Machina
whenever i type in the first command it gives me

"bash: syntax error near unexpected token `newline'"


@mikewhatever

it gives me the same error message when I try to open it in safe mode

---

### Post by pqwoerituytrueiwoq on 2011-01-21
try a new profile 
firefox -P
if it works there is probably an evil page crashing it (blames flash)
try cleaning temp files with bleachbit
sudo apt-get install bleachbit

---

### Post by nam42589 on 2011-01-21
when i try to clean it with bleachbit, it gives me these 4 errors

[Errno 13] Permission denied: '/home/nirav/.mozilla/firefox/39x4sek9.default/Cache/_CACHE_MAP_'
[Errno 13] Permission denied: '/home/nirav/.mozilla/firefox/39x4sek9.default/Cache/_CACHE_002_'
[Errno 13] Permission denied: '/home/nirav/.mozilla/firefox/39x4sek9.default/Cache/_CACHE_003_'
[Errno 13] Permission denied: '/home/nirav/.mozilla/firefox/39x4sek9.default/Cache/_CACHE_001_'

---

### Post by Stylesmarino on 2011-03-26
Having similar problems.

It all started when I updated to the FF 4 (RC) Via the firefox stable PPA (am I saying that right?) using apt-get update, apt-get upgrade.

If I run firefox from terminal (~$ firefox)
it give me the following:

> Traceback (most recent call last):
  File "/usr/lib/firefox-4.0/xulapp-profilemigrator", line 459, in <module>
    update_stamp (options.profile + '.last-version', options.series if migrator.ask_again == False else migrator.last_series.raw)
  File "/usr/lib/firefox-4.0/xulapp-profilemigrator", line 437, in update_stamp
    fd = open (stampfile, 'w')
IOError: [Errno 13] Permission denied: '/home/cormac/.mozilla/firefox.last-version'


Same thing happens in Safe mode.

So far I have tried:

> remove firefox and install firefox
> Purge firefox and Install firefox
> BleachBit

It is annoying me that FF4 RC is working nicely on XP at work yet not at home on Ubuntu.
Any Ideas?

Also its not giving me the "firefox has crashed message"

---

### Post by mendieta on 2011-04-23
I just had this error. It turned out I had lost permission on my /home/myUserName/.mozilla

If you know how to change ownership of a file, great. Otherwise you can just get .mozilla off the way and start all over

```
cd ~
sudo mv .mozilla .mozilla_back
```

---

