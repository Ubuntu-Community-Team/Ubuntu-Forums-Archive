---
title: "VLC script"
date: 2009-09-12
forum: General Help
---

### Post by NoaHall on 2009-09-12
I'm planning to make a bash script which turns off the computer after a video file has finished playing. Has anyone got any idea how to get the output from VLC to tell if it's finished playing?

---

### Post by mc4man on 2009-09-12
Don't have a clue, but if no success there...

you could try using a different start command for vlc

vlc --play-and-exit

Then you'd be looking to  vlc closing as a 'trigger'

Not sure if that command can be run on a group of files at once and work right, will certainly on a single one

---

### Post by NoaHall on 2009-09-12
Hm. I'll give that a try, and if I don't reply , it worked :) I'll look into a more advance one tomorrow morning.

```

vlc --play-and-exit file.avi && poweroff 
``` 
is what I'm going to try just for now.

---

### Post by mc4man on 2009-09-12
I think I'd make it a bit more all 'purpose' by not specifing the target file. (will also work on a group of files if run on the dir.

more like
vlc --play-and-exit "$1" &&  <your shutdown command>

Noting that you'll need to be able to run the shutdown without a password (fairly straightforward, there's a Sudoers page in ubuntu help, though I'd make sure you know how to use the default editor or set one you do as default

this worked fine though I'm not up on cli shutdowns, using shutdown seemed best, for some reason I also preferred +1 over now for time (now seemed so abrupt

```
#!/bin/bash
vlc --play-and-exit "$1" && sudo shutdown -h +1


```

I guess the shutdown command could also be executed in a terminal, don't see that it matters

---

### Post by NoaHall on 2009-09-13
One little edit to your script - 

```

#!/bin/bash
echo "Choose a file:"
read $1
	if [$1 != ""]
	then 
		sudo -i &
		vlc --play-and-exit $1
&& shutdown -h
	else 
		echo "Please enter a file name"
read $1
sudo -i &
		vlc --play-and-exit $1
&& shutdown -h
fi
exit 0

```

So then it'll ask for the password at the start, then you don't need to worry about getting up to do it when it's time to shutdown ;)

---

### Post by newsoft on 2009-09-13
thanks noahall for this :)

---

