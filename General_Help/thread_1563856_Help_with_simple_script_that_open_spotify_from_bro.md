---
title: "Help with simple script that open spotify from browser"
date: 2010-08-29
forum: General Help
---

### Post by Bidermaier on 2010-08-29
Hello. I am using spotify native for linux. I would like to make it work with the browser so when I click on a spotify link it opens spotify and it goes to the right song/playlist/user

I have not much idea of linux. I am a standard user. I am a philosophy student if you know what I mean.

On their website I found a script. But it is for wine. I need one that uses the native binaries (I have checked that  /usr/bin/spotify actually exists)
 
```
echo '#!/bin/sh' > $HOME/bin/openspotify
echo 'exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$@"' \
>> $HOME/bin/openspotify
chmod 755 $HOME/bin/openspotify

```

I would really apreciate if you could change that script so it works with spotify native.
Thanks.

---

### Post by birdy on 2010-09-18
Have a look here [http://ubuntuforums.org/showthread.php?p=9463706](http://ubuntuforums.org/showthread.php?p=9463706)

---

