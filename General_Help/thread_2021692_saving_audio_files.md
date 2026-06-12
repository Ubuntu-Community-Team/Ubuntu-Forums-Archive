---
title: "saving audio files??"
date: 2012-07-09
forum: General Help
---

### Post by beanco on 2012-07-09
Hi All,

I need to play this

[http://www.bbc.co.uk/ouch/old/columnists/audio/fran3.ram](http://www.bbc.co.uk/ouch/old/columnists/audio/fran3.ram) in a class I teach. No net in the class room.

How can I save the file?

Thanks

Robi

PS. I am on Meerkat using Chrome and/or Mozilla for what it's worth.

---

### Post by ron999 on 2012-07-09
> **beanco said:**
> 

How can I save the file?



Hi
**mPlayer** will do the job.
Like this:-
```
mplayer -bandwidth 999999 rtsp://rmv8.bbc.net.uk/ouch/columnists/fran3.ra -vc null -vo null -ao pcm:fast:file=fran3.wav
```

---

### Post by beanco on 2012-07-09
Ron999

Once I have run that, what do I do? Where do I find the file?

And thanks!

RObi

---

### Post by ron999 on 2012-07-09
> **beanco said:**
>  Where do I find the file?

Hi
Before you start...
enter this command:-
```
cd ~/
```
Then the file "**fran3.wav**" will be saved in your /home/user directory

---

### Post by beanco on 2012-07-10
> **ron999 said:**
> Hi
Before you start...
enter this command:-
```
cd ~/
```
Then the file "**fran3.wav**" will be saved in your /home/user directory

And there it is. Now to show my boss and prepare some exercises on it and then show the students... thakns!!!!!


Robi

---

### Post by HermanAB on 2012-07-10
or streamtuner.

---

### Post by beanco on 2012-07-10
What's streamtuner?

---

### Post by Nixarter on 2012-07-10
It does that automatically.

It's in the repositories.

---

