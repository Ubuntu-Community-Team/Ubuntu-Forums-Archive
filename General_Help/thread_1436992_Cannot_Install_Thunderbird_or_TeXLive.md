---
title: "Cannot Install Thunderbird or TeXLive"
date: 2010-03-23
forum: General Help
---

### Post by amonaaron on 2010-03-23
I just recently upgraded Karmic 32 bit to 64 bit (as I wish to have the full functionality of my 64 bit system). Unfortunately, I now cannot seem to install Thunderbird or TeXlive.

When I go to the terminal and try to install this is what I get:

```
sudo apt-get install texlive-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package texlive-full
```

The same occurs for Thunderbird.

I have added the Universe and Main repositories, so I don't believe that is an issue.

Thank you in advance for any help. :D

---

### Post by colorlessprism on 2010-03-23
try checking synaptic, i do not know about tex, but thunderbird is something to the effect of "mozilla-thunderbird"...

sometimes i forget "sudo apt-get update"

---

### Post by amonaaron on 2010-03-23
Silly me, all I had to do was hit "Reload" in the Synaptic Package Manager and that took care of my issues. Thanks for the help!

---

