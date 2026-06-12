---
title: "DansGuardian + polipo glitches"
date: 2010-06-19
forum: General Help
---

### Post by student68 on 2010-06-19
Hello,


I recently installed DansGuardian (a web filter) and polipo but I'm experiencing some problems:

1) On some pages I get the following error with Firefox, but not with Chrome.
"The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing connections."

2) DansGuardian doesn't block https pages. E.g. If I blacklist twitter.com, [https://twitter.com](https://twitter.com) isn't blocked.

3) All of amazon.com's images are being blocked.


Thanks in advance for any help.

---

### Post by student68 on 2010-06-23
Found answer to (3) by looking at dansguardian logs:

Comment out images-amazon.com from the audio-video blacklist.

You can get there by typing Alt+F2 then 
```
gksudo gedit /etc/dansguardian/lists/blacklists/audio-video/domains.
```

---

