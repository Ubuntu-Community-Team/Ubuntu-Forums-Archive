---
title: "Nautilus crashes and then gnome-settings-daemon"
date: 2012-09-18
forum: General Help
---

### Post by wiseguy12851 on 2012-09-18
I'm running Ubuntu 12.04 64-bit and using lightdm and Unity  Here is what happens:   


[LIST=1]
[*]Sometime after login (Can't figure out if it's random or if it's triggered) but nautilus crashes. After this happens any attempts to open nautilus cause it to open and then immediately close.
[*]Shortly after (Again I can't decide if it's triggered or random)  gnome-settings-daemon crashes. I don't notice any immediate effects from  this.
[*]Shortly after Ubuntu switches themes (Window Theme, Icon Theme, etc...). This new theme appears to be radiance but the controls are drawn very simplistic and old looking.
[*]Shortly after that other random programs (different every time) start to crash and Ubuntu becomes very slow/sluggish and often unresponsive.
[*]Eventually it locks up completely and I usually have to switch to one of the terminals via ctrl + alt + F# and reboot.
[*]After reboot everything works like a charm until the events start again.
[/LIST]

This first started happening on my laptop and after installing on my desktop it started happening there as well. It's always in this exact order.

---

### Post by wiseguy12851 on 2012-09-18
Is anyone on that can help me?

---

### Post by wiseguy12851 on 2012-09-19
Here's some more information that may be useful,

When I tried to manually start nautilus from the terminal it failed and spat this out

```
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
nautilus-wipe-Message: Initializing
Intializing nautilus-pastebin extension...
Initializing nautilus-ideviceinfo extension
Initializing nautilus-image-converter extension
Initializing nautilus-dropbox 0.7.1
Traceback (most recent call last):
  File "/usr/share/nautilus-python/extensions/nautilus-bzr.py", line 427, in get_widget
    controldir, path = ControlDir.open_containing(uri)
  File "/usr/lib/python2.7/dist-packages/bzrlib/controldir.py", line 732, in open_containing
    return klass.open_containing_from_transport(transport)
  File "/usr/lib/python2.7/dist-packages/bzrlib/controldir.py", line 766, in open_containing_from_transport
    raise errors.NotBranchError(path=url)
bzrlib.errors.NotBranchError: Not a branch: "/home/russell/".
Traceback (most recent call last):
  File "/usr/share/nautilus-python/extensions/nautilus-bzr.py", line 144, in get_background_items
    controldir, path = self._open_bzrdir(vfs_file)
  File "/usr/share/nautilus-python/extensions/nautilus-bzr.py", line 54, in _open_bzrdir
    controldir, path = ControlDir.open_containing(uri)
  File "/usr/lib/python2.7/dist-packages/bzrlib/controldir.py", line 731, in open_containing
    transport = _mod_transport.get_transport(url, possible_transports)
  File "/usr/lib/python2.7/dist-packages/bzrlib/transport/__init__.py", line 1679, in get_transport
    return get_transport_from_url(location_to_url(base), possible_transports)
  File "/usr/lib/python2.7/dist-packages/bzrlib/transport/__init__.py", line 1663, in get_transport_from_url
    raise errors.UnsupportedProtocol(url, last_err)
bzrlib.errors.UnsupportedProtocol: Unsupported protocol for url "x-nautilus-desktop:///"
Traceback (most recent call last):
  File "/usr/share/nautilus-python/extensions/nautilus-bzr.py", line 427, in get_widget
    controldir, path = ControlDir.open_containing(uri)
  File "/usr/lib/python2.7/dist-packages/bzrlib/controldir.py", line 731, in open_containing
    transport = _mod_transport.get_transport(url, possible_transports)
  File "/usr/lib/python2.7/dist-packages/bzrlib/transport/__init__.py", line 1679, in get_transport
    return get_transport_from_url(location_to_url(base), possible_transports)
  File "/usr/lib/python2.7/dist-packages/bzrlib/transport/__init__.py", line 1663, in get_transport_from_url
    raise errors.UnsupportedProtocol(url, last_err)
bzrlib.errors.UnsupportedProtocol: Unsupported protocol for url "x-nautilus-desktop:///"
Maximum number of clients reachedMaximum number of clients reachedSegmentation fault (core dumped)
```

I'm going to need some help, I have this problem on 2 computers, I can't work with it and don't know how to fix it. Somebody please help.

---

### Post by Achillobator on 2012-09-20
I'm having the same/a similar problem (12.04 x64): Nautilus crashes after the computer's been on for a while, and then it reports that gnome-settings-daemon has crashed as soon as I close the notice saying that Nautilus crashed. I can occasionally start Nautilus after the initial crash, but not usually.

Additionally, it looks like both of my CPUs and my RAM spike way up in usage after this happens (Firefox also seems to be using much more CPU than it normally does). I can't say for sure whether this sharp increase in resource usage is related to the crashes and have only just noticed it after the most recent crash, but I wasn't at the computer when the Nautilus crash report first popped up so I'm not sure how long ago it happened this time. I'm going to restart my computer as soon as I finish posting this, and I'll keep an eye on the system status and processes before and after I see the report so I can better try to figure out any correlation that might exist.

If there's any other information I can provide that would help solve this problem, just let me know.

Thanks in advance!

---

### Post by Achillobator on 2012-09-23
It's happened again; far as I can tell the crashes do seem to correspond with a spike in resource usage. I also notice that attempting to close or minimize active windows takes a long time; I can click on a window icon, nothing happens, I go do something else, and then eventually the other window will minimize or Firefox will give me the close tabs warning or what have you.

I realize this is still kind of vague, but I'm not really sure what else to check or to say. Any insight at all, anyone, or at least a nudge in the right direction for uncovering more about the problem?

---

### Post by wiseguy12851 on 2012-09-24
I can't figure it out, it appear this is yet another topic the community doesn't care about helping with. I even tried to beg for help, sad.

I might carry on just because I hate Windows and Mac is too expensive but frankly if this keeps up I'm going to have to switch to something else since I can't work like this. I'm already putting up with a ton of other errors and I can't even get the first one solved.

How can I fix Linux if I know nothing about fixing problems on it, can't find help anywhere, and nobody here will help me. This is becoming routine with every question.

@Achillobator - It seems we have the same issue, although I found that a full restart isn't required, a simple logoff and logon solves it.

---

### Post by predato on 2013-09-03
Follow this topic:[http://askubuntu.com/questions/64244/nautilus-crashes-when-accessing-some-folders#](http://askubuntu.com/questions/64244/nautilus-crashes-when-accessing-some-folders#) if it doesn't work rename ~/.local directory and log out

---

