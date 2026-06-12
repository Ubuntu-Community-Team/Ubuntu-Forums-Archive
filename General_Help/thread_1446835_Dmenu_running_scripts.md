---
title: "Dmenu running scripts"
date: 2010-04-04
forum: General Help
---

### Post by Kodpoet on 2010-04-04
Hi,

So I've been using xmonad as my permanent window manager for a while and just recently understood what a great thing dmenu is. Now, one thing that hasn't worked great is starting spotify. At the moment I have an alias in my .bashrc that goes:

```
alias spotify='wine .wine/drive_c/Program\ Files/Spotify/spotify.exe'
```

Which does the job but I'd like to be able to launch spotify by just typing "spotify" in *dmenu* instead. I figured I could put the command in a script, make it executable and then put it somewhere, but the question is where? Or is there a better way?

---

### Post by Kodpoet on 2010-04-06
I managed to figure it out! ^^ So what I did was:

First I created a script launching spotify, simply called "spotify".

```

#!/bin/sh

wine ~/.wine/drive_c/Program\ Files/Spotify/spotify.exe

```Then I gave it executable status with chmod.

```

chmod 777 spotify

```lastly I moved the script to /usr/bin/ which seems to contain lots of other executables.

```

mv spotify /usr/bin/

```The next time I logged in I could run the spotify script as if it was just any other application.

Mission Accomplished!

---

### Post by guriinii on 2010-04-27
Thank you! I love writing simple scripts.

---

