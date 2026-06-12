---
title: "Gwibber in 9.10 won't run"
date: 2010-03-01
forum: General Help
---

### Post by booksnmore4you on 2010-03-01
Gwibber in 9.10 won't run. From the command line it gives:

```

WARNING:root:desktopcouch is not available. .  falling back to gconf

** (gwibber:5041): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (gwibber:5041): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (gwibber:5041): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 57, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 107, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 190, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 262, in setup_ui
    self.input = gwui.Input(self)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 395, in __init__
    self.textview = InputTextView(client)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 455, in __init__
    self.spell = gtkspell.Spell(self, None)
glib.GError: enchant error for language: en_US.UTF-8
```

Any ideas?

---

### Post by dosox on 2010-03-01
I don't know about those codes & lines but Gwibber works fine on my laptop. [u910]
I can receive, retweet & reply with twitter and friendfeed BUT I didn't find an option to post my tweets :)

---

### Post by jflarm on 2010-03-07
I had the same problem and just "fixed" now.
On a terminal run:
gwibber-accounts
This will open the account settings dialog. Add your accounts and close it.
Now try to run gwibber....it worked for me.

---

### Post by chuckh1958 on 2010-03-29
I'm having the same problem. Just started today AFAICT. There is no gwibber-accounts command and nothing in the repo for me to install with that name either.

---

### Post by chuckh1958 on 2010-04-02
bump

---

### Post by Benchamoneh on 2010-04-14
I don't have Gwibber installed but you could try searching your system for the gwibber-accounts binary, it might be that it's installed but there's no link for it in your bin directory. Try running
```
sudo updatedb && locate -i gwibber-accounts
```
to see if the binary exists. If so you'll see the location so run it from there.

---

