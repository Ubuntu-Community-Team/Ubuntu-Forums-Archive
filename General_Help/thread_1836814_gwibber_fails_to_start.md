---
title: "gwibber fails to start"
date: 2011-08-31
forum: General Help
---

### Post by pabc on 2011-08-31
on a fully updated Lucid Gwibber has suddenly stopped loading.

starting from a terminal I get;
```

Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 448, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 59, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 145, in setup_ui
    self.stream_view.set_state(self.model.settings["streams"] or DEFAULT_SETTINGS["streams"])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 439, in set_state
    self.update()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 427, in update
    self.message_view.render([self.navigation.selected_stream["view"]])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 737, in render
    accounts=accounts)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 285, in render
    self.load_html_string(content, "file://%s/" % os.path.dirname(template_path))
TypeError: WebKitWebView.load_html_string() argument 1 must be string without null bytes, not str 
```

I've done a complete removal/reinstall but get the same thing.

Any suggestions on what I can do? Or alternative clients which intergrate as well with gnome?

---

### Post by krytorii on 2011-08-31
Try empathy perhaps. It integrates facebook, msn and several other chat clients.

---

### Post by pabc on 2011-08-31
empathy is a twitter client? I thought it only handles instant message protocols

---

### Post by pabc on 2011-08-31
OK, I installed a twitter plugin for pidgin (Dont like empathy) and I'm back up and running, but if anyone can suggest a workaround to get gwibber working I'd prefer that solution

twiiter plugin for pidgin : [http://www.lostintechnology.com/software/how-to-add-twitter-to-pidgin/](http://www.lostintechnology.com/software/how-to-add-twitter-to-pidgin/)

---

### Post by pabc on 2011-09-06
Still trying to sort it out. Wife says the pidgin solution isn't as pretty so I added the gwibber ppa and upgraded to the latest version and the problem still exist so I suspect they problem lies elsewhere . Any ideas?

I think i'm gong to hose the system and rebuild with mint. Her emails are on imap and  personal stuff on dropbox so no biggy. My son uses it and it seems not to suffer these niggles. If I wait a few Weeks for oo she'll kill me as the change will be too much

---

### Post by pabc on 2011-09-06
ok - for anyone else;
```

sudo gedit /usr/lib/python2.6/dist-packages/gwibber/gwui.py
```

then add the line
```

content = content.replace("\0","")
```

before the line
```

self.load_html_string(content, "file://%s/" % os.path.dirname(template_path))
```

ensure you keep the indentation the same (4 spaces i think - I dont know python but without the indentation it through a different error)

---

