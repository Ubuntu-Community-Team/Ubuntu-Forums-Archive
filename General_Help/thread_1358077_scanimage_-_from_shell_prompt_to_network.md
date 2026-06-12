---
title: "scanimage - from shell prompt to network"
date: 2009-12-17
forum: General Help
---

### Post by caue.rego on 2009-12-17
Here's my shell script:
```
#!/bin/bash

sudo scanimage -pv --format=tiff > out.tiff
sudo chown bs00:bs00 out.tiff
sudo chmod 777 out.tiff

```

This is working, but I want to do two things with it:
1. scan directly to JPEG instead of TIFF
2. be able to execute it from the LAN - thinking in using HTTP

Up to now I couldn't find any clues on how to do it. Can somebody shred me some light, pretty please? :)

edit: oh yeah, plus one more extra question:
I'm currently running this using this "Run" script on the right mouse click menu:
```
#!/bin/bash

app-runner "$1"

```

How could I run it with a simple double click?

---

