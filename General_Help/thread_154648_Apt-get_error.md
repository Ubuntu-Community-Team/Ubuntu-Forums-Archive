---
title: "Apt-get error"
date: 2006-04-03
forum: General Help
---

### Post by Minn3h on 2006-04-03
I do: sudo apt-get install noteedit
And get:
```
Setting up lilypond-data (2.6.3-9~breezy1) ...
/var/lib/dpkg/info/lilypond-data.postinst: line 15: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What does it mean and what do I do?

---

### Post by Minn3h on 2006-04-04
The solution was simple, I did:
```
sudo apt-get install tetex-bin
```

---

### Post by NewbieNik on 2006-04-04
you might find that "sudo apt-get -f install" would have helped, but cannot guarantee it. Has helped me in the past.

a little knowledge is a dangerous thing, but not as dangerous as a little gun!!!

---

### Post by Minn3h on 2006-04-05
Ya that was the first thing I tried, but it just gave the same kind of error when trying to deal with that lilypond package.

---

### Post by renzokuken on 2006-04-06
i have this exact error as well, and i think its responsible for synaptic/apt-get playing up and not installing stuff properly

---

