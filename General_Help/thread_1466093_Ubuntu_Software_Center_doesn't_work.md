---
title: "Ubuntu Software Center doesn't work"
date: 2010-04-30
forum: General Help
---

### Post by klasjosh30 on 2010-04-30
[SIZE=4]When I go in Ubuntu software center and try to download ANYTHING I get this error message.[/SIZE]
[IMG]http://i830.photobucket.com/albums/zz228/jhk30/Screenshot.png[/IMG]

[SIZE=4] the picture cuts off part of the error but this is what it says.[/SIZE]

```
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

```[SIZE=4]I am using Ubuntu 10.04 LTS[/SIZE]

---

### Post by ssj6akshat on 2010-04-30
You should file a bug report

---

### Post by jobix on 2010-04-30
Can you try to delete that lock file and see if you get the error?

---

### Post by klasjosh30 on 2010-04-30
the lock file isn't deleteable.

---

### Post by RAD-MAN on 2010-04-30
Oh wow I did it. I had the same problem. I tried to add the CD as a repository in software sources but that didn't work, so I decided to go through the terminal.

I put the 10.04 disk in, opened the terminal and ran

sudo apt-cdrom add

then

sudo apt-get update

At least, that worked for me.

---

### Post by jobix on 2010-04-30
> **klasjosh30 said:**
> the lock file isn't deleteable.

What do you mean? What command did you try? What error message, if any, do you get? Also, remember you'll need to do this using sudo because of the permissions.

---

### Post by an78gubad on 2010-05-03
No hablo mucho inglés así que esto lo pongo en español y traducido por google. A mi me pasó lo mismo. Yo borré el arhivo /var/lib/apt/lists/lock como root e hice sudo apt-get update y solucioné el problema.

I do not speak much English so I put it in Spanish and translated by google. The same thing happened to me. I deleted the arhive /var/lib/apt/lists/lock as root and did sudo apt-get update and solved the problem.

---

### Post by fumacapena on 2010-09-18
Translated by Google:
My case:
In Terminal
sudo /etc/apt/ sources.list

So I copied all the mirrors that were something like [http://br](http://br) .* (I'm brazilian) and put a # in one (backup). So I deleted the "br." as in:

# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted

Saved, then:
sudo apt-get update

=)

---

