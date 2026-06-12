---
title: "Running update script at shutdown/logoff??"
date: 2012-06-29
forum: General Help
---

### Post by Phear46 on 2012-06-29
I would like to run a script to perform updates on my laptop as I turn it off. I could just shutdown using somethng like 'apt-get upgrade && shutdown -h now' but I want something that will work even if I forget to click/run that script.

I was thinking of writing something like this:
```

#!/bin/bash
apt-get update
apt-get upgrade
```and placing it in init.d then placing sym links in rc0/6.d.

Question, would this work? I belive everything in /etc is owned and run as root but im still learning here.
Or is there a better way? Like I say, I'm still learning so I'm not totally up on all the ins an outs of how Linux functions.

Also, once I figured out where this script goes and how to invoke it, any help on a 'if on AC power then update &&  shutdown, else shutdown' script would be great :)
Like I say, I'm still a novice really so if I've missed any info here please don't hesitate to ask.

Nathan

---

### Post by Phear46 on 2012-06-30
Bump (sorry)

---

