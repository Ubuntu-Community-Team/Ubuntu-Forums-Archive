---
title: "Voice recognition"
date: 2011-02-18
forum: General Help
---

### Post by megabuffen on 2011-02-18
Does anyone know of a utility that can recognize voice commands using a standard microphone?

It shouldn't be a desktop utility, but rather just a program that listens for manually configured voice commands and takes predefined actions. All I really need is some kind of daemon that allows me to record a voice command and map it to a specific file with a bash script. If I can just make that part work, I should be able to use the script to do anything I want.

---

### Post by lykeion on 2011-02-18
I don't really know what you mean by mapping a voice to a specific file. Take a look at [gnome-voice-control]("http://www.youtube.com/watch?v=GCSgkUnlGGA"). You can install it from the repositories.

---

### Post by megabuffen on 2011-02-18
What I mean is that the program continuously listens for voice commands using a 3.5 mm computer microphone. When a voice command, which I have pre-recorded, is detected, it will run a script that I specify. It would be quite similar to a voice password that I tried on an old Mac a few years ago. It had me read a line of text four times. When I logged in, I would read it again and the computer would perform some kind of test to see if it matched. This should be the same principle, comparing my voice command to a database of pre-recorded command.

For example, if I say "Computer, turn on lights", then I want the program to run the executable file /some-path/lights-on.

Gnome-voice-control is not what I'm looking for, as the computer has no GUI. I control it using SSH, but I can use a local terminal if necessary.

---

### Post by Grenage on 2011-02-18
Some apps that may be of interest.

[http://www.linux.com/archive/feed/41723](http://www.linux.com/archive/feed/41723)

---

