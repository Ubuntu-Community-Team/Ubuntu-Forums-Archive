---
title: "easyubuntu aborting with errors"
date: 2006-05-22
forum: General Help
---

### Post by gwpritch on 2006-05-22
I was running easyubuntu and it was interrupted mid stream. Now when I try to continue I get the following:

```
Traceback (most recent call last):
  File "easyubuntu.py", line 10, in ?
    replace(confdir)
  File "/home/greg/easyubuntu/detect.py", line 113, in replace
    if "cdrom" in line or (line.startswith("deb ") and repos_URI == line.split()[1]):
UnboundLocalError: local variable 'repos_URI' referenced before assignment

```

Can anyone tell me what the problem is and how to rectify it.
Thanks.

---

### Post by glinsvad on 2006-05-22
From the looks of it, it's probably a bug somehow. Looks like it chokes while reading the repositories to download packages from. I quickly browsed through the code - it works flawless on breezy :)

Have you altered /etc/apt/sources.list somehow - possibly through Synaptic or System->Administration->Software Properties?

Could you paste back the output of these commands?
```

python /home/greg/easyubuntu/detect.py

```
And possibly the output in the resulting file
```

cat /home/greg/easyubuntu/conf/sources.list

```

Anyway, you could also try if the latest version works.
[http://users.on.net/~goetz/EasyUbuntu/get.html]("http://users.on.net/~goetz/EasyUbuntu/get.html")

---

### Post by gwpritch on 2006-05-22
Here are the two outputs:

```
You are running a DAPPER
system on X86 architecture
GNOME-KDE available
Traceback (most recent call last):
  File "/home/greg/easyubuntu/detect.py", line 149, in ?
    replace(confdir)
  File "/home/greg/easyubuntu/detect.py", line 80, in replace
    targetlist = open(os.path.join(confdir, 'sources.list'),'w')
IOError: [Errno 13] Permission denied: '/home/greg/conf/sources.list'

```

```
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb http://wine.sourceforge.net/apt/ binary/
deb http://deb.opera.com/opera etch non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

```

I tried tried the 'bleeding edge' as outlined on the easyubuntu download page and got the same results.

The thing of it is, it was working fine until I accidentally aborted the downloads. They were probably about half done. Nothing else changed between then and my trying to restart the process.

---

### Post by gwpritch on 2006-05-22
I reconstituted my sources.list from *source-o-matic*, based on your question about whether it had been changed with Synaptic.  I ran *easyubuntu* again and it worked flawlessly.
I'm not sure what we did....but thanks.,

---

### Post by glinsvad on 2006-05-22
I'm glad that worked - I was pretty lost about what to do next :D

---

### Post by robotgeek on 2006-05-22
[QUOTE=glinsvad]I'm glad that worked - I was pretty lost about what to do next :D[/QUOTE]
Good debugging there!

---

### Post by glinsvad on 2006-05-24
[QUOTE=robotgeek]Good debugging there![/QUOTE]

Really? A nightly job - and had absolutely no idea what EasyUnuntu was :mrgreen:

Cool little tweak though (if you don't care about GPL)

---

