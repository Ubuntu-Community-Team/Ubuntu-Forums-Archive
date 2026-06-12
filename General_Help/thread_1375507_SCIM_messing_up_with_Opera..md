---
title: "SCIM messing up with Opera."
date: 2010-01-08
forum: General Help
---

### Post by Pawbla on 2010-01-08
I don't know why, but SCIM is messing up with Opera. Sometimes I just stop being able to input text (in a box in some webpage, the bar, whatever) or just plainly use the keyboard. The "solution" is to minimize the window and maximize again. It's been like this for a while but it's deeply annoying me now. Does anybody knows how can I avoid this?

---

### Post by Zorael on 2010-01-08
SCIM is being phased out of Ubuntu in favor of I-Bus, which seems to be the default in Karmic. There's also UIM, which I'm using.

I've had similar issues with SCIM, which prompted me to look into the alternatives. If you don't need alternative language input in Opera, you could always make a script that disables SCIM and then starts it.
```
#!/bin/bash

unset QT_IM_MODULE         # unsets the variable pointing to the Qt input method module
XMODIFIERS="@im="          # tells X to not use any specific custom input method, instead falling back to the default vanilla XIM
/usr/bin/opera $@ &        # starts opera in a child process, passing arguments to it
disown %1                  # disowns the child process so your browser won't die if the shell dies
```
If you save it as **/usr/local/bin/opera** (and set it as executable), all your normal Opera launchers should default to using it instead of the normal binary (which is in **/usr/bin/**).

SCIM is supposedly dead-ish upstream, so the migration to other input methods isn't entirely unwarranted. I-Bus is a newcomer and still lacks some functionality, while UIM has been around for a good while and does the job nicely for me. Only UIM has a Qt4 panel, which is obviously a factor for me, running KDE SC.

---

### Post by Pawbla on 2010-01-09
I do need SCIM.

So UIM is an alternative to SCIM? You recommend me to switch to UIM?

---

### Post by Zorael on 2010-01-09
Give either (uim or ibus) a try at least. There are packages for both in the repos, and you can find some *unofficial* upgrades by doing [ppa searches](https://launchpad.net/ubuntu/+ppas). [ppa:ibus-dev/ibus-1.2-karmic](https://launchpad.net/~ibus-dev/+archive/ibus-1.2-karmic) has ibus upgrades for Karmic, and [ppa:japanese-testers/ppa](https://launchpad.net/~japanese-testers/+archive/ppa) has a fresher UIM (but not by much). If you're aiming for Japanese, [ppa:japaneseteam/ppa](https://launchpad.net/~japaneseteam/+archive/ppa) has a newer Anthy.

But the official repo packages should do the trick just as nicely.

**edit:** If you're unfamiliar with input methods and how to switch between them, I go over them in abstract in [this post](http://ubuntuforums.org/showthread.php?p=8415508).

That said, what language are you trying to input in?

---

### Post by Pawbla on 2010-01-10
Nope, I just need accents (á) and ñs, it's Spanish. Ok, I'll give it a try and read it. Thanks a lot!

---

### Post by Pawbla on 2010-01-11
Hum... Opera doesn´t recognize UIM now. Works fine with the rest of the system, it seems. But I checked here:

```
pawbla@pawbla-laptop:~$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
GTK: uim, Qt: uim, XMOD: @im=uim
```

Does anything need to be configured with Opera?

---

### Post by Pawbla on 2010-01-12
Solved. Qt needs to be set to xim for it to work with Opera, seen here: [http://wiki.archlinux.org/index.php/Input_Japanese_using_UIM#Cannot_input_Japanese_on_Opera](http://wiki.archlinux.org/index.php/Input_Japanese_using_UIM#Cannot_input_Japanese_on_Opera)

Now I get my ás and ñs :3

---

