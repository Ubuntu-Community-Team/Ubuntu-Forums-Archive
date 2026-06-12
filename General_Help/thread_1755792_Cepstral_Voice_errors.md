---
title: "Cepstral Voice errors"
date: 2011-05-11
forum: General Help
---

### Post by john_beachbum on 2011-05-11
Ubuntu 11.04 / 64 clean install.  installed ccsm for screen mag. (visually handicap).
purchased Cepstral Allison for Linux, installed and registered the voice.

in terminal, "swift hello"  gets the response;   

oss_audio: failed to open audio device /dev/dsp 

in terminal, "padsp swift hello" will get the voice to say hello.

how do I go about solving this problem so the voice will work?
so far Cepstral has been of very little help on this issue.

thanks for reading my post, sure hope someone has done this successfully.

---

### Post by SATA on 2011-11-24
Hey mate

If this is still an issue, here is a workaround / fix


1. when you install cepstral voice engine it places the engine in 
/opt/swift/bin/swift 
this binary is pointed to by /usr/local/bin/swift, i.e., 
/usr/local/bin/swift -> /opt/swift/bin/swift 
remove the link, i.e. /usr/local/bin/swift and replace it with a file 
called swift that looks like this: 

```

#!/bin/sh 
if test -x /usr/bin/padsp ; then 
exec /usr/bin/padsp /opt/swift/bin/swift "$@" 
else 
exec /opt/swift/bin/swift "$@" 
fi

```

chmod +x this file (/usr/local/bin/swift) or you will get permission errors.

---

