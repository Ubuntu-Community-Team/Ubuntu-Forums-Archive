---
title: "Problem with Ubuntu Tweak third party software (9.10)"
date: 2009-10-10
forum: General Help
---

### Post by Trelo on 2009-10-10
Hi all,

I just did a fresh install of 9.10.  I installed Ubuntu Tweak, that's what I did...

# add key
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220
# add this software source to sources.list
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) karmic main
# install
sudo apt-get update
sudo apt-get install ubuntu-tweak

Now, when I run Ubuntu Tweak I don't have a problem with Add/Remove but the Sources and the Third Party tabs can't be edited.  When I click on Third Party it tells me "PPA sources has expired, some of your PPA sources need to be updated, do you wish to continue?" I hit Yes but nothing happens.  Can't install any Third Party software or edit Sources.list from Ubuntu Tweak.

Does anyone have a clue what's the problem?

Thanks in advance.

---

### Post by kellemes on 2009-10-10
Hit the Unlock-button on these tab-pages. (bottom right)
It'll ask for your password before you can continue.

---

### Post by Trelo on 2009-10-10
> **kellemes said:**
> Hit the Unlock-button on these tab-pages. (bottom right)
It'll ask for your password before you can continue.

I forgot to mention this.  When I hit unlock nothing happens.

---

### Post by kellemes on 2009-10-10
Please start "ubuntu-tweak" from the commandline.
Do you get any terminal-feedback when hitting the unlock-button?

---

### Post by Trelo on 2009-10-10
> **kellemes said:**
> Please start "ubuntu-tweak" from the commandline.
Do you get any terminal-feedback when hitting the unlock-button?

Thanks for your replies Kellemes.

Yes I do get feedback

Traceback (most recent call last):
  File "/usr/share/ubuntu-tweak/common/policykit/polkitbutton.py", line 97, in on_button_clicked
    self.action.authenticate()
  File "/usr/share/ubuntu-tweak/common/policykit/polkitbutton.py", line 55, in authenticate
    self.do_authenticate()
  File "/usr/share/ubuntu-tweak/common/policykit/polkitbutton.py", line 61, in do_authenticate
    policykit = self.session_bus.get_object('org.freedesktop.PolicyKit.AuthenticationAgent', '/')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PolicyKit.AuthenticationAgent was not provided by any .service files

---

### Post by kellemes on 2009-10-10
A quick google teached me this..
Seems to be [a confirmed bug]("https://bugs.launchpad.net/ubuntu-tweak/+bug/446430").
As I understand to be fixed (bypassed?) like so..
```
sudo apt-get install policykit-gnome
```

---

### Post by Trelo on 2009-10-10
> **kellemes said:**
> A quick google teached me this..
Seems to be [a confirmed bug]("https://bugs.launchpad.net/ubuntu-tweak/+bug/446430").
As I understand to be fixed (bypassed?) like so..
```
sudo apt-get install policykit-gnome
```

many thanks mate, it worked!! :):):)
cheers.

---

