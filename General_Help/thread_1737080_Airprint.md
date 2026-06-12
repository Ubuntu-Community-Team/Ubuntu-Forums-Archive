---
title: "Airprint"
date: 2011-04-23
forum: General Help
---

### Post by peterhocking on 2011-04-23
Hi

I'm running Ubuntu 10.10 64 bit & I've attempted to setup airprint so that I can print from my iPad using the howto at [http://www.micromux.com/2010/11/22/airprint-for-mac-on-linux/#more-401](http://www.micromux.com/2010/11/22/airprint-for-mac-on-linux/#more-401).

When I run the script, I get the following error;
[I]tv@mythtv-server:~/Downloads$ ./airprint-generate.py
./airprint-generate.py: line 6: syntax error near unexpected token `newline'
./airprint-generate.py: line 6: `<!DOCTYPE html>'[/I]

I'm new to Ubuntu & have no experience with python. Can anyone assist?

TIA

Peter

---

### Post by mgchan on 2011-06-29
> **peterhocking said:**
> Hi

I'm running Ubuntu 10.10 64 bit & I've attempted to setup airprint so that I can print from my iPad using the howto at [http://www.micromux.com/2010/11/22/airprint-for-mac-on-linux/#more-401](http://www.micromux.com/2010/11/22/airprint-for-mac-on-linux/#more-401).

When I run the script, I get the following error;
[I]tv@mythtv-server:~/Downloads$ ./airprint-generate.py
./airprint-generate.py: line 6: syntax error near unexpected token `newline'
./airprint-generate.py: line 6: `<!DOCTYPE html>'[/I]

I'm new to Ubuntu & have no experience with python. Can anyone assist?

TIA

Peter

Don't know if you figured it out... if you "save file" on the airprint-generate.py link on that page it actually downloads a web page. You need to actually follow the link and copy/paste the text into a file called airprint-generate.py, then you can run it.

---

