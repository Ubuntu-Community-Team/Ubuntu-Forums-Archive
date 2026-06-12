---
title: "ipod problems"
date: 2006-04-19
forum: General Help
---

### Post by ravi on 2006-04-19
hey everyone.

so, for the first time since i switched over to linux (ubuntu) i tried to update my ipod.  i did this using amarok (gtkpod was WAY too slow and seemed very sketchy and unreliable).  all i did was try to add one song, and after i unmounted the ipod i can only access like 12 or 13 bands' music.  (i have probably around 300 bands on there).  it is bizarre.  rhythm box and amarok can still accesss all the music, however the ipod itself can't do anything.  do you guys know of any way to fix this.

another note that may give some info is that every time i unmount it gives an error message saying "unable to unmount" and the details say something like "last line: invalid argument"  i have some friends who have the same problem (we all have the 5G ipod videos)  i just ignored that error message and disconnected anyways.  however, when i actually updated the ipod, it screwed things up.

this is really annoying and really frustrating (i have a lot of music on there that i don't have anywhere else, so i really don't want to lose that stuff).

i appreciate any help in advance.  thanks

---

### Post by ninotob on 2006-04-19
I'm sure it goes without saying at this point -- never experiment with your only copy of something.

I don't have 5g ipod, but some things I would try in your shoes (i.e., these are guesses, I can't ensure they will work).

#1:  Mount it on your linux box.  Then try to unmount it.  If you get an error, don't unplug.  First, make sure the music program is exited and nothing is accessing the ipod (not even a file browser).  Then try unmounting with the right click/unmount method.  

#2:  If #1 fails, open a terminal window.  Type:

df

and press enter.  You will get some output, look for the line corresponding to your ipod.  The last column tells you where it is mounted.  type:

sudo umount <mount_point>

and press enter where <mount_point> is /mnt/ipod or whatever place "df" said the ipod is mounted at.  You'll have to enter your password after issuing this command.  If it works, test out your ipod.  If it won't, perhaps some program still has control of the ipod.  Perhaps try a shutdown with the ipod connected in the hopes it can be unmounted cleanly at that point.  Test the ipod.

#3:  Try mounting it on a windows or mac machine with itunes but turn off the autoupdate settings to prevent erasure.  See if all your music is there and if so, properly unmount and then check your ipod to see if all is well.

#4:  if all else fails, while the ipod is mounted in linux, open it up with your file browser (the "df" command above will tell you where to point the file browser to) and copy all your files to your linux machine.  Perhaps you can copy them all back again in itunes (windows or mac) and have it work.  You'd lose your ratings and such most likely, but still have the files at least.

Anyway, this how I'd start troubleshooting the problem.

---

