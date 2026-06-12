---
title: "Bluetooth disabled on resume from suspend / hibernate"
date: 2011-05-02
forum: General Help
---

### Post by lotharmat on 2011-05-02
I was having a problem with bluetooth being disabled after resuming from suspend:

Laptop: Fujitsu Siemens Lifebook T4215

Solution:

Create a file /etc/pm/sleep.d/20_restart_bluetooth
paste this code into it
```
#!/bin/sh

case "${1}" in
	(suspend|hibernate)
		service bluetooth stop
		;;
	(resume|thaw)
		service bluetooth restart
		;;
esac
```
give it execute permissions with 

```
sudo chmod 755 /etc/pm/sleep.d/20_restart_bluetooth
```

Worked like a charm for me!

---

### Post by luc765 on 2012-01-27
Thanks for the informations.

This solves the problem for my Dell XPS M1210 - ubuntu 11.10 (oneiric)

Lucien

---

### Post by wolframarnold on 2012-10-01
I found the solution on this thread: [http://ubuntuforums.org/showthread.php?t=1387211]("http://ubuntuforums.org/showthread.php?t=1387211") to be a more reliable solution. That also worked for me on 10.08 already.

---

