---
title: "Zenity multiple column output?"
date: 2011-10-26
forum: General Help
---

### Post by qckdrw777 on 2011-10-26
How can I read the output of individual columns in a multiple column zenity GUI? 

IE here is my script:

```
#!/bin/bash 
zenity --list --title="Test" --column=Alias --column=IP --column=Protocol Test 10.0.0.1 RDP Test2 10.0.0.2 VNC

```

How can I get the output from the IP column (or other columns) specifically? 

Right now regardless of what I do, I only get the output from the first column. and I really don't understand how that's happening either as I just put an echo at the end of the script and it happens. :confused:

---

