---
title: "Thunderbird 3.0.4 and Enigmail don't work"
date: 2010-05-02
forum: General Help
---

### Post by bestoe on 2010-05-02
Hi,  well i just migrated from debian testing to ubuntu 10.04 since the newly introduced thunderbird 3.0.4 did not work with enigmail anymore and i need that to read about half of my e-mails. Now, it doesn't work on ubuntu either. I have the version (of the distribution) 1.0.1 of enigmail installed. In the testing version i also deinstalled it and downloaded the version given by the addons. Still didn't work. If i start from command-line, i get: 

> 2010-05-02 18:19:17.383 enigmail.js: Enigmail.initialize: START 
2010-05-02 18:19:17.384 enigmail.js: Logging debug output to  ~/work//enigdbug.txt 2010-05-02 18:19:17.384 enigmail.js: Enigmail  version 1.0.1 
2010-05-02 18:19:17.384 enigmail.js: OS/CPU=Linux i686 
2010-05-02 18:19:17.384 enigmail.js: Platform=X11 
2010-05-02 18:19:17.384 enigmail.js: composeSecure=false 
2010-05-02 18:19:17.384 enigmail.js: Enigmail.initialize: Error -  Enigmime-Service nicht verf&#65533;gbarsaying Enigmime-Service is not available. Usually i get a window saying the same thing each mail i open. Anybody has a workaround?

---

### Post by rsriniv on 2010-10-07
You need to uninstall enigmail package (using synaptic), remove the enigmail extension from Thunderbird, then reinstall the enigmail package again.

This solved the problem got me.

(Ubuntu Maverick 10.10 64 bit)

--Rajiv

---

### Post by zerubbabel on 2010-10-07
That didn't work for me. I just installed the latest Thunderbird update, version 3.1.5 (Lucid, amd64), but I can't find a compatible version of Enigmail...

---

### Post by zerubbabel on 2010-10-07
Found it [here]("http://enigmail.mozdev.org/download/index.php.html").

---

