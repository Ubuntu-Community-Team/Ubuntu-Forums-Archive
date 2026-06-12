---
title: "Subliminal software"
date: 2010-10-10
forum: General Help
---

### Post by confused_user on 2010-10-10
Hi, i've been using some subliminal software on windows for a while now and have found it to be really good.  It basically just flashes up a message on screen over the top of whatever is going on at that time but the message is only there for about 30 milli seconds

The message is not there long enough for your conscious mind to read it but the theory is that your subconscious mind will read it.

It actually works really well.

THe problem is that they dont package a linux version although they do have an OSX version, i'd really like this on ubuntu.

Tried it in wine and it installs but nothing happens after that.

Alternatively perhaps somebody can tell me how you could get a message to flash up on screen based on a list of messages in a text file?

A little script maybe?

Thanks

---

### Post by nothingspecial on 2010-10-11
You might be able to do it with xmessage.

It can read from a file and there is a display time option

```
man xmessage
```

---

### Post by confused_user on 2010-10-11
Thanks, some further googleing led me to this 

[http://ubuntuforums.org/showthread.php?p=8021986](http://ubuntuforums.org/showthread.php?p=8021986)

and it works perfectly

xsublim and thanks loads to Greg Knauss for writing it and alpharesearch for packaging it

now if i can just find the config file to configure it...

---

### Post by stinkeye on 2010-10-11
> **confused_user said:**
> Thanks, some further googleing led me to this 

[http://ubuntuforums.org/showthread.php?p=8021986](http://ubuntuforums.org/showthread.php?p=8021986)

and it works perfectly

xsublim and thanks loads to Greg Knauss for writing it and alpharesearch for packaging it

now if i can just find the config file to configure it...

Do you know where the messages are kept?
I would like to tell myself "Go and do the dishes you lazy b*st**d!"
:P

---

### Post by confused_user on 2010-10-12
the default ones are hard coded, you can over ride them with the --file argument

create a text file and list your messages with each message on a new line

my fileis called .xsublim but you can call it anything

eg

do dishes
i like a clean kitchen
clean kitchens are good
clean is good

then start xsumblim with the following arguments

```
xsublim --file /path/to.file/.xsublim --delayPhraseMax 5000000 --no-screensaver --random
```

I have it set to make the messages random, changed to delay between new messages and set it to no screensaver so that it comes up over the top of everything

Only thing i cant do yet is change the font color and size

---

