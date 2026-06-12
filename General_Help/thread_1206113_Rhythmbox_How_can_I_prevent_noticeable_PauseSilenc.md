---
title: "Rhythmbox: How can I prevent noticeable Pause/Silence Between Tracks?"
date: 2009-07-06
forum: General Help
---

### Post by OzzyFrank on 2009-07-06
Hi. I've looked in the Preferences for any sign of a setting for pause/silence/gap between tracks when playing, but cannot find anything related. Now, I can assure you the tracks themselves have no extra silence at the beginning or end, which I know can happen when ripping MP3s with some programs (I only ever had that happen in Windows). I can also tell you that **Amarok does not do this**, so when (for example) I am playing a live album, it sounds pretty seamless, whereas in Rhythmbox there is a noticeable gap. Is there some setting in some config file somewhere that I can edit to stop this? I had a look in Gconf Editor and couldn't see anything that looked useful, but I'm hoping there is an answer and one of you knows it. Cheers.

---

### Post by Elep.Repu on 2009-07-28
This is the type of problem people who use linux ignore. 
lol (But windows "sucks" of course.)

---

### Post by OzzyFrank on 2009-07-28
Hehe... this is only an issue in Rythmbox, not the whole of Ubuntu, let alone Linux in general. This doesn't affect apps like Amarok. In most cases, I vastly prefer apps like Rhythmbox to Windows Media Player. And that's not just because I prefer not to be in Windows unless I really need to (this is because, as you have noted, Windows sucks).

On the whole, most media apps in Linux are superior to WMP because of the simplicity of use. Everything is there and easy to access. Some like Rhythmbox have all sorts of cool/useful plugins, while WMP comes with some useless features you can't get rid of - it's like Microsoft are always trying to sell you something or get you to spend money at this site or another (like iTunes, hehe).

Lastly, while not everything in Linux is perfect (just as in Windows, and I can tell you after 16 years experience I have seen MANY imperfections), at least you can file bug reports and things might happen. So I guess I should go and file a bug report since I haven't gotten any answers here, hehe. Cheers

---

### Post by DeMus on 2009-07-28
> **OzzyFrank said:**
> Hi. I've looked in the Preferences for any sign of a setting for pause/silence/gap between tracks when playing, but cannot find anything related. Now, I can assure you the tracks themselves have no extra silence at the beginning or end, which I know can happen when ripping MP3s with some programs (I only ever had that happen in Windows). I can also tell you that **Amarok does not do this**, so when (for example) I am playing a live album, it sounds pretty seamless, whereas in Rhythmbox there is a noticeable gap. Is there some setting in some config file somewhere that I can edit to stop this? I had a look in Gconf Editor and couldn't see anything that looked useful, but I'm hoping there is an answer and one of you knows it. Cheers.

Sorry to say this but you did not look well enough. Look at the attached picture and set the top setting like I did, choose the time to your liking. Then try again.

---

### Post by OzzyFrank on 2009-07-28
> **DeMus said:**
> Sorry to say this but you did not look well enough. Look at the attached picture and set the top setting like I did, choose the time to your liking. Then try again.

Actually, I did see that, but thought it was like the fade in/out feature in Amarok (which I don't particularly want). I'll give that a try, but admit the "Crossfade" bit has me worried.

OK, just tried it, and it was as I thought. While it certainly gets rid of the slight gap between songs, it mangles the first and last 4 secs of songs together, so really wasn't what I was looking for. But many thanks anyway!

But I did experiment with the particular album that made me start this post (a live Frank Zappa one) and with a half second crossfade, it is almost perfect - just like a slight bump in between. Go to a 1 sec crossfade, and there is no noticeable transition, but then there is a bit of noticeable effect of the crossfade.

So at least I can set this manually for Live albums if need be, though would have to disable it for most others (songs that end on a bang would die with a whimper!). So if anyone knows how to get rid of this gap (that apps like Amarok aren't putting in) without the use of crossfade, please let me know. I know other apps have settings for gaps between audio tracks (or am I thinking burning apps here?), and like I said, Rhythmbox is doing something the others are not, so hopefully there is a config setting somewhere that can rectify this.

---

### Post by Elep.Repu on 2009-07-30
This is an issue with linux in general.
This does affect amarok, and every other application *nix (besides the Mozilla funded Songbird)

---

