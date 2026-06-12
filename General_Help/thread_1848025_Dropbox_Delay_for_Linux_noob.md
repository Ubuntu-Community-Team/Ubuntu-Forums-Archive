---
title: "Dropbox Delay for Linux noob"
date: 2011-09-21
forum: General Help
---

### Post by boma23 on 2011-09-21
hi all,

My Dropbox for Ubuntu app keeps starting before my data partition (and dropbox) folder mounts, so I'm trying to apply a fix as per these threads:

[http://wiki.dropbox.com/DropboxAddons/DelayAndIONice]("http://wiki.dropbox.com/DropboxAddons/DelayAndIONice")
[http://superuser.com/questions/132853/how-to-set-dropbox-startup-delay-in-ubuntu]("http://superuser.com/questions/132853/how-to-set-dropbox-startup-delay-in-ubuntu")
[http://forums.dropbox.com/topic.php?id=7686&replies=9#post-352138]("http://forums.dropbox.com/topic.php?id=7686&replies=9#post-352138")

Trouble is, they're a bit hard to follow for a complete noob, and they assume some basic knowledge of where certain files are, and how to edit them, and make them executable etc.

The 3rd link above seems quick and easy, if I knew HOW to do the actual steps below:

* * * * * * * * * * * * * * * * * * * * * 

My general solution is this script:


[COLOR="Green"]#!/bin/sh

sleep $1
shift
exec "$@"[/COLOR]


Put that somewhere in your $PATH in an executable file called "delay"**[COLOR="Red"] How do I do this?[/COLOR]**. Here's an example of how to use this script:


[COLOR="green"]delay 60 dropbox[/COLOR]


That will wait 60 seconds, then execute dropbox. You can add delays to your startup programs by editing their commands in "Startup Applications".[B][COLOR="red"]I've found where to edit the command, it currently says

dropbox start -i

Do I need to point the command to somewhere else (the executable)?  Or edit the command itself?

 [/COLOR][/B]

Thanks for any help in advance

---

### Post by boma23 on 2011-09-25
can anyone help...?

---

### Post by nothingspecial on 2011-09-25
First type 

```
gedit ~/.bashrc
```

Add this line to the end

```
export PATH=$PATH:/home/[COLOR="Red"]username[/COLOR]/bin
```

change the red username for your real username.

Then type

```
. ~/.bashrc
```

Next type

```
mkdir ~/bin
```

Then

```
gedit ~/bin/delay
```

copy and paste this into that empty file
```

#!/bin/sh

sleep $1
shift
exec "$@"
```

Save and close.

Lastly

```
chmod +x ~/bin/delay
```

That's it :D

---

### Post by boma23 on 2011-09-25
you're a saviour and a gent sir  :)

I'm appreciating the signature too!

---

### Post by nothingspecial on 2011-09-26
No problem :D

---

