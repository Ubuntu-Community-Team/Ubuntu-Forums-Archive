---
title: "dvd audio wont stop in vlc"
date: 2006-05-13
forum: General Help
---

### Post by pellgarlic on 2006-05-13
apologies for starting 2 threads within minutes of one another, but this problem is unconnected from the other, and i thought it best to give it its own thread. if moderators disagree, i'll be humble in my error!

the problem is this: if i open a dvd in vlc, whether from the dvd disc itself, or a "temporary, honest i'm going to delete it after i've watched it, i own the dvd ;)" file on my hard drive, then close vlc without stopping the playback, the sound track keeps playing. :-k 

re-opening vlc doesn't help. even if i open another file, or the same file again, the "new" audio plays, but the "old" audio is still there, playing away.

if i open the "system monitor" (through "applications > system tools), and right-click on "wxvlc" and select "stop process", the audio stops, so i'm guessing that process is erroneously contuing when it shouldn't. if i click on the "stop" button in vlc before i close it, there is no problem.

i'm not sure whether to alert the makers of vlc, or if the "wxvlc" is made by someone else. i'm appealling for those more experienced linux users to point me in the right direction here. if anyone can, it would be most appreciated.

---

### Post by skymt on 2006-05-13
I've had that problem also. The solution is simple: wait. It's a known bug, and I haven't seen it since I upgraded to Dapper. Meanwhile, here are some solutions: 

* Keep a System Monitor open to kill it when you're done.
* Open vlc from the terminal, and use control-C to kill the process.
* Use MPlayer, Totem or Xine.
* Upgrade to Dapper (it's almost ready anyway).

P.S. wxvlc is the official vlc interface. It's in a seperate package because in theory someone could write another vlc interface, but the only one I've seen is gvlc, which is no longer in development.

---

### Post by pellgarlic on 2006-05-13
:) cool - thanks for the quick reply. the "upgrade to dapper" solution sounds spot on, but i think i'll wait til dapper is properly ready before i upgrade, as i'm still a bit of a beginner with linux. i'd rather do my learning on a "stable" release, even if dapper is almost as stable.

---

### Post by Tapeworm on 2006-12-26
I am experiencing the same DVD audio problem with VLC.

Edgy + VLC 0.8.6 so everything is up to date.

Any ideas? 

Tapeworm

---

### Post by pellgarlic on 2006-12-27
@tapeworm - 

don't know if there has been any progress made on this bug, but there is one easy way to avoid the problem - press the "stop" button before you close the player window :)

sorry i can't be more help than that. as it does not cause the computer to freeze or crash, i just lived with it, and haven't really noticed it happening since i upgraded from breezy to dapper (now on edgy)

---

### Post by eldaria on 2007-01-15
Have same issue, also with Edgy.
And doing the stop is not really solution since process is still running.
I noticed that after viewing a couple of Video clibs, I had 15 instances of the wxvlc process.
So there is certainly a bug in the package, that aperantly has followed all the way to Edgy..

---

