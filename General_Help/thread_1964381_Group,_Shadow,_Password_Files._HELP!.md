---
title: "Group, Shadow, Password Files. HELP!"
date: 2012-04-23
forum: General Help
---

### Post by Bigsirhc on 2012-04-23
Hey good people! I need a hand, if you all could comment and tell me what im looking at in these files. I would good extremely grateful.

File 1: "**group**[URL="http://www.flickr.com/photos/67383756@N07/6962180780/in/photostream/"]"
[/URL][http://www.flickr.com/photos/67383756@N07/6962180780/in/photostream/](http://www.flickr.com/photos/67383756@N07/6962180780/in/photostream/)
File 2: "**passwd**"
[http://www.flickr.com/photos/67383756@N07/7108252763/in/photostream/](http://www.flickr.com/photos/67383756@N07/7108252763/in/photostream/)
File 3: "**shadow**"
[http://www.flickr.com/photos/67383756@N07/7108252743/in/photostream](http://www.flickr.com/photos/67383756@N07/7108252743/in/photostream)

I have a tiny bit of understanding of what im looking at with these three files so the more information and detail the better! Thank you friends!

---

### Post by strask on 2012-04-23
Take down the image of the shadow file, and immediately change ALL passwords on that system.

NEVER reveal the contents of the shadow file, it has all your passwords in it. They are encrypted, but even the encrypted versions are not safe to share because it opens you up to brute force cracking attempts. By posting that image you have told the entire internet WAY too much about your passwords.

The contents of these files is explained in the man pages for them, try these commands for some good reading:```
man -s5 passwd
man -s5 shadow
man -s5 group
```

---

### Post by Bigsirhc on 2012-04-24
Thank you sir for your help! In conclusion those were sample files, not from my own system! I just need help understanding what exactly im looking at when I open those!

---

