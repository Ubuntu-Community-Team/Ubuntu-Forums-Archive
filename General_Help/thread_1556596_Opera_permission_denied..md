---
title: "Opera: permission denied."
date: 2010-08-19
forum: General Help
---

### Post by kcinholland on 2010-08-19
Hello Forum.

Ref:
Ubuntu 10.4 Lucid Lynx
Fluxbox
Opera 10.61

Has anyone a clue how I can solve following (minor but annoying) problem?

It takes a relative long time (a few seconds) as normal user before Opera starts in my fluxbox environment. I expected a quicker startup time.
Also because when I start opera as root the startup time is shorter.

I started opera in a terminal. 
No messages when started as root with gksudo
But 5 lines of:
open: Permission denied
when started as normal user. Startup succeeds after these messages.

So I figured out that there is some kind of authorisation problem but have no clue how to find out which files opera tries to open and fails and what to do at this point.

I searched for similar problems on this forum and also via google but could not find any real answers.

Any hint is much appreciated.

Thank you
kc

---

### Post by Vaphell on 2010-08-19
my bet - config dir of opera is owned by root, not by you, because you ran opera with sudo which is not a good thing to do. Browsers have no business running with root privileges, especially when they are a big attack vector. Once your browser is owned, your whole system is owned too because you hand out root access to the attacker.

```
ls -la ~/.opera
``` to confirm

```
sudo chown -R yourname:yourname ~/.opera
``` to fix

---

### Post by kcinholland on 2010-08-20
> **Vaphell said:**
> my bet - config dir of opera is owned by root, not by you, because you ran opera with sudo which is not a good thing to do. Browsers have no business running with root privileges, especially when they are a big attack vector. Once your browser is owned, your whole system is owned too because you hand out root access to the attacker.

```
ls -la ~/.opera
``` to confirm

```
sudo chown -R yourname:yourname ~/.opera
``` to fix

Hello Vaphell,
Thnx for your time 
Yes I agree about the running of opera as gksudo. I will never use that method for normal operation, maximum for testing like I did here.

But, sorry to say, I think you lost the bet.
I tried your suggestion and this is the result. (gelly = the username)

[FONT="Courier New"]rwx------  18 gelly gelly   4096 2010-08-20 07:21 .
drwxr-xr-x 140 gelly gelly   8192 2010-08-19 21:41 ..
drwxr-xr-x   3 gelly gelly   4096 2010-07-21 22:12 application_cache
-rw-r--r--   1 gelly gelly   1154 2010-08-18 21:38 autoupdate_response.xml
-rw-r--r--   1 gelly gelly   2114 2010-08-20 07:21 bookmarks.adr
-rw-r--r--   1 gelly gelly 106112 2010-08-18 21:38 browser.js
drwxr-xr-x  12 gelly gelly   4096 2010-08-19 22:45 cache
-rw-------   1 gelly gelly  83898 2010-08-19 23:15 cookies4.dat
drwxr-xr-x   2 gelly gelly   4096 2009-09-16 19:29 dictionaries
-rw-r--r--   1 gelly gelly     12 2010-08-19 22:17 download.dat
-rw-------   1 gelly gelly    448 2010-07-21 00:22 fontswitch.ini
-rw-r--r--   1 gelly gelly 178615 2010-08-20 07:21 global_history.dat
drwxr-xr-x   3 gelly gelly   4096 2010-07-25 08:11 icons
-rw-r--r--   1 gelly gelly      0 2010-08-19 22:25 lock
drwxr-xr-x   4 gelly gelly   4096 2010-08-19 22:25 mail
drwxr-xr-x   4 gelly gelly   4096 2010-08-15 12:05 opcache
-rw-r--r--   1 gelly gelly  30542 2010-08-19 22:15 opcacrt6.dat
-rw-r--r--   1 gelly gelly     27 2010-08-19 22:17 opcert6.dat
-rw-------   1 gelly gelly  41086 2010-08-19 22:25 operaprefs.ini
-rw-r--r--   1 gelly gelly   9042 2010-08-19 22:15 opicacrt6.dat
-rw-r--r--   1 gelly gelly   4096 2010-08-19 22:17 oprand.dat
-rw-r--r--   1 gelly gelly  11972 2010-08-19 22:17 opssl6.dat
-rw-r--r--   1 gelly gelly    126 2010-08-06 07:25 opthumb.dat
-rw-r--r--   1 gelly gelly     96 2010-07-21 00:26 optrb.dat
-rw-r--r--   1 gelly gelly     12 2010-08-19 22:15 optrust.dat
-rw-r--r--   1 gelly gelly     12 2010-08-19 22:15 opuntrust.dat
-rw-------   1 gelly gelly   3607 2010-08-18 21:38 override_downloaded.ini
-rw-------   1 gelly gelly    599 2010-07-21 22:15 override.ini
-rw-------   1 gelly gelly    306 2010-08-18 21:38 pluginpath.ini
drwxr-xr-x   3 gelly gelly   4096 2010-07-26 19:51 pstorage
-rw-------   1 gelly gelly   3202 2010-08-19 22:49 search_field_history.dat
-rw-------   1 gelly gelly    209 2010-08-02 21:04 search.ini
drwxr-xr-x   2 gelly gelly   4096 2010-08-20 07:21 sessions
drwxr-xr-x   2 gelly gelly   4096 2010-07-25 14:18 skin
-rw-------   1 gelly gelly    303 2010-07-26 19:46 speeddial.ini
drwxr-xr-x   3 gelly gelly   4096 2009-09-16 19:28 styles
-rw-------   1 gelly gelly    242 2010-08-13 19:58 tasks.xml
drwxr-xr-x   2 gelly gelly   4096 2010-08-19 21:42 temporary_downloads
drwxr-xr-x   2 gelly gelly   4096 2010-08-06 07:25 thumbnails
drwxr-xr-x   2 gelly gelly   4096 2010-08-08 17:22 toolbar
-rw-r--r--   1 gelly gelly   9014 2010-08-19 22:43 typed_history.xml
-rw-------   1 gelly gelly   1463 2010-04-02 19:03 unite.adr
-rw-r--r--   1 gelly gelly      0 2010-07-21 00:25 upgrade.log
-rw-------   1 gelly gelly     12 2010-08-20 07:15 vlink4.dat
drwxr-xr-x  11 gelly gelly   4096 2010-08-19 23:11 vps
-rw-------   1 gelly gelly   1954 2009-09-16 20:09 wand.dat
drwxr-xr-x   2 gelly gelly   4096 2010-04-02 19:04 webserver
drwxr-xr-x   9 gelly gelly   4096 2010-08-15 11:18 widgets
[/FONT]

To me it looks that I own all the files.

Any other tricks I could try?

kc

---

### Post by Vaphell on 2010-08-20
what happens when you start from scratch with fresh profile? rename your current .opera and give the browser a spin.

---

### Post by kcinholland on 2010-08-20
> **Vaphell said:**
> what happens when you start from scratch with fresh profile? rename your current .opera and give the browser a spin.

Hello Vaphell,
Tried your suggestion and renamed folder .opera to old.opera.
Then started up opera in a terminal and noticed following:
- 7 lines with message: open: permission denied
- Then the agrteement window of opera to welcome new users
- Then the browser.
Meaning that his was not the solution.
I have thrown away the new .opera folder and renamed my old.opera back to .opera.

My idea is, but I have no clue how to check, that during the startup some underlying files or programs are accessed. And that these files/oprograms are owned by root.

thnx.
kc

---

