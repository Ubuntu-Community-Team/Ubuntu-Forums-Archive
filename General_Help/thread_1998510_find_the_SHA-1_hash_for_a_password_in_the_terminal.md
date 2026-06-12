---
title: "find the SHA-1 hash for a password in the terminal"
date: 2012-06-06
forum: General Help
---

### Post by supportagent11 on 2012-06-06
_[this link]("http://nakedsecurity.sophos.com/2012/06/06/millions-of-linkedin-passwords-reportedly-leaked-take-action-now/")_ about the linkedin password leak got me thinking today about how to generate a SHA-1 hash in the ubuntu terminal (see _[http://leakedin.org]("http://leakedin.org/?check=70ccd9007338d6d81dd3b6271621b9cf9a97ea00")_ using the unsalted SHA-1 hash for "Password1").

"sha1pass Password1" keeps giving me random hashes, because if i do not specify a salt it will use a random salt...
"pwgen" will let me specify -sha1 as an option, but will not allow me to specify text (only a file).

any idea what command i could use in the terminal to get an unsalted SHA-1 hash of a plain text password? ideally, i would like to enter "Password1" as the input, and have "70ccd9007338d6d81dd3b6271621b9cf9a97ea00" returned every time.

---

### Post by Sarteck on 2012-06-07
Could run PHP to do it:

If **php5-cli** is installed, the following would work fine:
```
php -r "echo sha1('Password1');"
```



EDIT: There might be a regular BASH command for it, but I just don't know, obviously.  XD  Until someone suggests a better alternative, though, you could do this.  Or even make a simple script that'll take command-line arguments if you don't feel like typing that stuff each time.

---

### Post by Sarteck on 2012-06-07
Double-posting because this is an alternate answer:

**echo -n Password1 | sha1sum | awk '{print $1}'**

I am not so proficient with the command line that I even know quite what this does, lol, but it seems to be reliable.

I stole it from this blog:
[http://albertech.blogspot.com/2011/08/generate-sha1-hash-from-command-line-in.html](http://albertech.blogspot.com/2011/08/generate-sha1-hash-from-command-line-in.html)

The author explains it rather well. :3

---

### Post by supportagent11 on 2012-06-07
sometimes the simplest solutions are the best, and i was just missing the php command :)

i installed **php5-cli **and ran this in the terminal:
> php -r &#8216;echo sha1(&#8220;Password1&#8221;) . &#8220;\n&#8221;;&#8217;the output was "70ccd9007338d6d81dd3b6271621b9cf9a97ea00" (plus a return character at the end)

that leakedin.org site seems pretty reputable for checking to see if your linkedin password was compromised... mine does not appear to be on the list, but i changed it anyways.

thanks for the assist!

---

### Post by Habitual on 2012-06-07
food for thought:
```

#!/bin/bash
date +%s | sha256sum | base64 | head -c 12 ; echo
date +%s | sha1sum | base64 | head -c 12 ; echo
openssl rand -base64 9
< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c${1:-12};echo;
gpg --gen-random --armor 1 9

```

---

