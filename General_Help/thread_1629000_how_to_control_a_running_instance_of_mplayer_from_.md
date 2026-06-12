---
title: "how to control a running instance of mplayer from bash script?"
date: 2010-11-23
forum: General Help
---

### Post by tobytoby on 2010-11-23
I am starting an instance of mplayer from a bash script, opening an audio stream:
```
mplayer http://location.of.audiostream.com
```

How do I do to control this mplayer instance from another script? I want to control volume and pause it from within the bash script.

I know the commands for doing so from terminal, but once mplayer gets started from the script, how do I 'direct' the commands to that specific mplayer instance?

---

### Post by DaithiF on 2010-11-23
you start it in -slave mode, reading input from 'somewhere' -- in your cases perhaps a named pipe that your other controlling process will write to.

something like:

```
mkfifo /tmp/mplayer-control
mplayer -slave -input file=/tmp/mplayer-control /path/to/some/file/to/play

```

then in another terminal you could do something like:
```
echo "pause" > /tmp/mplayer-control
echo "quit" > /tmp/mplayer-control

```etc

---

### Post by nothingspecial on 2010-11-23
You could just use keybindings.

You can customise them if the default ones don`t suit your needs.

---

### Post by tobytoby on 2010-11-26
DaithiF, that was a perfect example and just what I was after! Great, thanks!

---

### Post by tobytoby on 2010-11-26
I now understand how to send commands to mplayer and that is great and the above example with 'PAUSE' worked. However, what I would like to do is to change the volume (intention is to fade out/in). I tried the following w/o any success:
```
echo "-af volume=0" > /home/user/script/mplayer.pipe
```and also tried:
```
echo "-volume 0" > /home/user/script/mplayer.pipe
```

---

### Post by DaithiF on 2010-11-26
why -af volume or -volume?  just volume.

```
echo "volume 0" > yourpipe

```

```
mplayer -input cmdlist | more 

``` for acceptable commands

---

### Post by tobytoby on 2010-11-26
sorry, that was a typo, it should have been "volume 0". That does not work, although 'pause' or 'mute' do.

---

### Post by DaithiF on 2010-11-26
works fine for me ... e.g.:

```
echo "volume +1" > yourpipe
echo "volume -1" > yourpipe

```
to increase / decrease volume by 1notch respectively

---

### Post by tobytoby on 2010-11-26
I just tried to fiddle a bit with it and noticed that mplayer increases/decreases the volume this way, but is it possible to send a command to set the volume at a specific level? (besides doing it when starting mplayer by '-volume 100' e.g.)

---

### Post by DaithiF on 2010-11-26
```
echo "set_property volume 0"
```

or any value from 0 to 100

---

