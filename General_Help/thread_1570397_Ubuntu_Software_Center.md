---
title: "Ubuntu Software Center"
date: 2010-09-08
forum: General Help
---

### Post by WALu on 2010-09-08
I'm new to UBUNTU might make you laugh but i'm learning this new OS so please help me

using 10.04 Desktop Edition Ubuntu.. 

want to install adobe flash player on this OS tried every thing present to solve this problem of mine on this forum but couldn't get it.. 

its giving me this error can anybody help me and tell me whats wrong with it?

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 116, in _process_transaction
    self.update_cache()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 426, in update_cache
    self._cache.update(progress, raiseOnError=True)
  File "/usr/lib/python2.6/dist-packages/apt/deprecation.py", line 103, in deprecated_function
    return func(*args, **kwds)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 309, in update
    raise LockFailedException("Failed to lock %s" % lockfile)
LockFailedException: Failed to lock /var/lib/apt/lists/lock

---

### Post by Rasa1111 on 2010-09-08
Hiyah,
Welcome here. 

 Im not sure about those error messages.

 But have you tried to install ubuntu-restricted-extras ?
 If not, type that into the software center search bar,
and install it.
 That should take care of your issues with flash, etc. 

 Ive never once installed "flash player" in Ubuntu,
only the restricted extras, and that has given me everything I need. 
Flash, codecs, etc etc. 

 G'luck.

---

### Post by bashphoenux on 2010-09-08
how did you install flash?
like '[Rasa1111]("http://ubuntuforums.org/member.php?u=1029120")' said install ubuntu-restricted-extras !
if you are using x64 then install gnash which is replacement for adobe flash 64-bit .

---

### Post by Rasa1111 on 2010-09-08
> LockFailedException: Failed to lock

 I do seem to remember a message like this though. 

and If I correctly recall..

 It is given when one is trying to install something ~ say from the software center~ but when synaptic package manager is also open. 
Or vice versa. 

 Ive found that you cannot have open, both software center, and synaptic package manager at the same time, and try to download/install something. 

if they are both open, 
Whichever one your trying to install from, 
Wont let you, and will give a "failed to lock" error message,
Until you close one or the other,
either software center or synaptic.

 Any chance you had both of these open?

---

### Post by lovinglinux on 2010-09-08
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Don't forget to close the Software Center or other package manager before running it.

---

