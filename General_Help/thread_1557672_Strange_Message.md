---
title: "Strange Message"
date: 2010-08-21
forum: General Help
---

### Post by uaebuntu on 2010-08-21
I use 64 bit Ubuntu 10.04 with Firefox 3.6.8 just recently every time I open my home page ([www.bbc.co.uk](www.bbc.co.uk)) I get a pop up "Authentication Required"
with the message "A username and password are being requested by [http://localhost:54066](http://localhost:54066). The site says: "administrator" " it has a boxes for the username and password and keeps coming back every time I cancel it. I've attached a screenshot.

What does it do and how do I get rid of it?

---

### Post by surfer on 2010-08-21
is this the only page where this happens?

your firefox tries to connect to some proxy on your localhost... did you configure a proxy?

---

### Post by uaebuntu on 2010-08-21
Yes it is popping up on everything though it used to go away when I went off my homepage. haven't knowingly configured any proxys or anything like that, this is my main machine so pretty stable, I have others that I "play" on before doing it to this machine.

---

### Post by lovinglinux on 2010-08-21
Do you have a server installed?

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by uaebuntu on 2010-08-22
Thanks,

started Firefox in safe mode and the pop up does not occur so that's a start, however when I logged out of firefox the terminal was full of error messages.... see new screenshot, doesn't look good.

Don't use many plug ins so I will disable them all and load one by one and let you know which one is the culprit.

---

### Post by uaebuntu on 2010-08-22
The culprit was "bindwood 1.0.4" strange for two reasons, I didn't knowingly install it, and it is for synching my favourites with a couch DB, which I'm not aware of wanting to do!

Anyway it's disabled and all seems well

---

