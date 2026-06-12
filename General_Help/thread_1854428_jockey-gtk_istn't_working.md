---
title: "jockey-gtk istn't working"
date: 2011-10-04
forum: General Help
---

### Post by Neutrosider on 2011-10-04
Hello
I have an Ubuntu on my usb stick and im using on multiple computers. As i don't need any additional drivers on my laptopt everything is fine there. but when i try to install additional drivers, jockey istn't working for me. i klicked on the icon, and a window popped up taht  told me that hes looking for drivers. after about 10 minutes it just disappears without any comment. So i tried starting jockey with the terminal to see if there are any outputs, and there are. these are the error messages i get:
```
heiko@USB-Heiko:~$ jockey-gtk
Exception in thread thread_call_progress_dialog:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 505, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 461, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 98, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 274, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 812, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
heiko@USB-Heiko:~$ 
```i googled through half of the web but was unable to find a working solution.

if i remember correctly, jockey worked some time ago, but at some day it just stopped working. becaus of that i think its because of an update, but even booting wit an older kernel didn't help.

I hope you can help me here :)

---

### Post by Mark Phelps on 2011-10-04
It won't work if there are no restricted drivers available for the version of Ubuntu that you are using.

If you're looking for video drivers, please post the make and model video card in your PC.  If you don't know what that is, open a terminal, enter "lspci" and look for the line containing "VGA" -- and post that info back here.

---

### Post by Neutrosider on 2011-10-04
its not working on any PC i testet it.

My Laptop: jockey doestn't start

My PC (wich has a 8500 GT and jockey is working on the ubuntu that is installed on the hard drive there): jockey doestn't start

in the school (where the PC has a Geforce 7025 if i remember correct): jockey doestn't start.

because auf that and because of the error message, i don't think it'sa hardware problem, but im vry sure its a software problem. i mean, when i start jocky at my PC at home, everything is fine, but when i boot from the usb stick at the SAME pc, jocky doetn't start, as i said before.

---

### Post by Neutrosider on 2011-10-05
Push?

---

### Post by Neutrosider on 2011-10-06
PUSH

i really need help...

---

### Post by Neutrosider on 2011-10-06
PUSH

btw, how long do i have to wait until repush according to the rules? and how often am i allowed to push my thread?

btw, i need jockey tomorrow, so can someone help me?

---

### Post by Neutrosider on 2011-10-07
srsly? still no one?

---

### Post by Neutrosider on 2011-10-14
problem is still alive ^^

---

