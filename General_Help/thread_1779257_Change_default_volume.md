---
title: "Change default volume"
date: 2011-06-10
forum: General Help
---

### Post by jony121 on 2011-06-10
Problem: I have a large sony vaio laptop with very loud speakers. When I login the volume is way up and I can't turn it down. This produces ear smashing results. The reason I can't turn it down is because my laptop like many others uses software to control the volume. The system still loading up cannot respond quick enough to my button pressing. Every time the computer starts up the login prompt sound and start up sound are painfully high even if I turn them down before restart.

A bug I found: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284947](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284947)
Sound cards being varied with their maximum volume this bug has made it to the way side of wishlist.

Ideal world: In such a place there would be the ability to set the default volume level for every startup (regardless of what it was previous to shut down.)

My solution: I am going to attempt to write a script to run on startup that will set the volume to a level you prior specify. Not advanced enough for a gui tick box and slider and my coding might be a little rough but fingers crossed I can figure this out. I will post what I write here for those who may also be affected.

If anyone has any pointers or hints then please reply. All help and encouragement accepted.

Edit:
Found this also: [http://brainstorm.ubuntu.com/idea/21778/](http://brainstorm.ubuntu.com/idea/21778/)
Please bump this idea.

---

### Post by pqwoerituytrueiwoq on 2011-06-10
set login volume at startup
i change my login sound startup item into a script that sets volume plays login sound then waits for rhythm-box to open then hits play makes sure it took and try again till it plays
line 3 sets volume to about 5%
```
me@linux-desktop:~$ cat /opt/sound
#!/bin/sh
pacmd set-sink-volume 0 3500
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
# Make sure rhythmbox is open
while [ 0`pidof rhythmbox` -eq 0 ]; do
    sleep 2
done
# Now lets hope the song is not actually named "Not playing"
# Loop is cause it likes to be stubborn my guess is
# rhythmbox is open but not ready to play sometimes.
while [ "`rhythmbox-client --print-playing`" = "Not playing" ]; do
    rhythmbox-client --play
    sleep 2
done
exit
```

---

### Post by jony121 on 2011-06-14
I really had hoped for a better way to get this done but it just can't be done by me.

system settings
startup applications
Add. Command: pacmd set-sink-volume 0 3500

Must be repeated for every user.

Big thanks to pqwoerituytrueiwoq

Atleast it has stopped my ear ache! :)

---

