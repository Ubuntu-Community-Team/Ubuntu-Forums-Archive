---
title: "GUI help"
date: 2011-04-25
forum: General Help
---

### Post by thomas515 on 2011-04-25
Okay so I want to write a script that will start or stop the GUI respectively.  This is what I have so far... 
```
#!/bin/bash
if [ "gdm running" = true ]; then

sudo service gdm stop
else
udo service gdm start
fi

```

I know the second line is completely wrong, but thats where I'm trying to go.  How do I write a "if the GUI is running then..." command?

---

### Post by DaithiF on 2011-04-25
a couple of ways ... firstly using pgrep to search for the running gdm-binary:
```
if pgrep -x gdm-binary > /dev/null; then
etc

```
and using service:
```
if [[ "$(service gdm status)" =~ "start/running" ]]; then 
etc.

```

---

### Post by thomas515 on 2011-04-26
Thank you very much.

---

