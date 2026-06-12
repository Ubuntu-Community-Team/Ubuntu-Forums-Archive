---
title: "speaker icon and sound preference dialog confusion!"
date: 2010-12-16
forum: General Help
---

### Post by Buckufuntu on 2010-12-16
Hey everyone, absolute newb here, installed the new ubuntu distro on my new Asus eeepc 4 days ago.....and I suspect it will be the death of me. Lots of minor frustrations, but the biggest is the sound.

First sound worked, then I downloaded some plugins for firefox, and then it didn't work! I've uninstalled n reinstalled all my media plugins, nothing. The strangest thing, is that my speaker icon shows mute, but my sound preference dialog has me CLEARLY unmuted on everything (of course, 'everything' includes 'dummy output' as my stereo choice)

This is what I got when I ran the ubuntu -bug audio command

symptom script /usr/share/apport/symptoms/audio.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 54, in thread_collect_info
    package = symb['run'](report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 28, in run
    package, card = soundcard_query(report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 206, in soundcard_query
    for card in open('/proc/asound/cards'):
IOError: [Errno 2] No such file or directory: '/proc/asound/cards'


Total gibberish to my eyes. Any help would be appreciated.

---

