---
title: "got a few question and problems"
date: 2009-11-01
forum: General Help
---

### Post by starcraftmaster on 2009-11-01
hey guys
first question:how much longer is ubuntu 9.04 being supported(updates)
2nd question : can you upgrade ubutnu 9.04 to 9.10 with the 9.10 install CD. i need to do it this way because i got slow internet and can not leave the computer on for 3 days just to update thourgh ubuntu update
so i just do it the ISO way so i can stop and resume any time i want to.
3rd question: with ocra can it read text in Firefox/opera ? as i like to try to learn a new language/learn to read a different language.

Problem:ocra wont start or i dont know how to start it . i type ocra in terminal and this comes up with lots of languages and i pick EU(to test) and this comes up:

Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/orca/orca.py", line 1086, in _showPreferencesConsole
    module.showPreferencesUI(_commandLineSettings)
  File "/var/lib/python-support/python2.6/orca/orca_console_prefs.py", line 440, in showPreferencesUI
    (not setupSpeech(prefsDict)):
  File "/var/lib/python-support/python2.6/orca/orca_console_prefs.py", line 257, in setupSpeech
    speechServerChoice)) # speech server
ValueError: invalid literal for int() with base 10: 'eu'




when i type brltty -d /dev/term/0 -bxw -xno -p none -A auth=none -n.
its comes up with this :

brltty: unknown option: -.
BRLTTY 3.11dev [[http://mielke.cc/brltty/]](http://mielke.cc/brltty/])
brltty: NoScreen Screen Driver:
brltty: BrlAPI Server: release 0.5.3
brltty: making socket directory error 13: Permission denied.
brltty: Error while initializing socket 0
brltty: Console open error 13: Permission denied.
brltty: XWindow Braille Driver: version 0.1, 2004
brltty: Console open error 13: Permission denied.
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  28 (X_GrabButton)
  Serial number of failed request:  169
  Current serial number in output stream:  596

when i run python -c "import brlapi"
no erros come up


thanks for the help

---

### Post by starcraftmaster on 2009-11-02
comeeeee onnnnnnn:(

---

