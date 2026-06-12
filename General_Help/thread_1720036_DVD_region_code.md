---
title: "DVD region code"
date: 2011-04-02
forum: General Help
---

### Post by TimmyK. on 2011-04-02
Hello again. Yesterday, to my great delight, I realized I can watch DVDs on my laptop. I tried the first DVD that I had tried it on, and it didn't work. I am thinking this may be something to do with region codes. First of all, how do I see which region code I am currently on? Secondly, how do I reset the region code? Is there any way to use multiple region codes at once?

---

### Post by davidmohammed on 2011-04-02
its more likely that you dont have all the restricted codecs installed.

from a terminal session type


sudo apt-get install ubuntu-restricted-extras

---

### Post by TimmyK. on 2011-04-02
Nope, I've already got it. Any other ideas?

---

### Post by davidmohammed on 2011-04-02
does anything described [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") help you?

---

### Post by hansdown on 2011-04-02
Hi TimmyK.

I've seen some dvd drives that haven't had the region set yet.

Be careful, because you are only allowed to change the region code 5 times, then it locks.

Your region should be region 1 to play north american dvds.

Click system> administration> synaptic package manager.

Searh for

```
regionset
```

and install.


Are you getting any error messages, when you try to play the dvd?

---

### Post by TimmyK. on 2011-04-02
No error notice. And I've already got regionset. How do I use it?

---

### Post by hansdown on 2011-04-02
Do you have

```
libdvdcss2
```

installed?

Does anything happen when you play a disk?

---

### Post by TimmyK. on 2011-04-02
Yes, I have it. And when I put in a DVD it will not play, I open VLC, and when I click play on the DVD, nothing happens.

Still, I'd like to know, how do I use regionset?

---

### Post by jmszr on 2011-04-02
TimmyK,

To use regionset put a CD/DVD in your player and then enter "regionset" (no quote marks) in the terminal. This link explains better than I could: [http://linvdr.org/projects/regionset/](http://linvdr.org/projects/regionset/) .

Also, VLC doesn't much care about region codes with RPC-1 and some RPC-2 players. I don't know about legalities, though. This .pdf explains: [http://www.macos.utah.edu/documentation/multimedia/foreign_dvd_playback/region_free_playback/mainColumnParagraphs/00/document/20041117-region_free.pdf](http://www.macos.utah.edu/documentation/multimedia/foreign_dvd_playback/region_free_playback/mainColumnParagraphs/00/document/20041117-region_free.pdf)

Hope that helps.

---

### Post by TimmyK. on 2011-04-02
Thanks, I got it. Just one last thing: when I hit regioncode in the terminal, it asked me to confirm, hit the number, and then it said:
```
New mask: 0xFFFFFFFE, correct? [y/n]:
```
What do I do?

---

### Post by jmszr on 2011-04-02
TimmyK,

Enter "y", according to what I've read, that will do it.

---

### Post by TimmyK. on 2011-04-02
OK, I hit yes, and it told me the code had been set successfully. However, still the same problem.

---

### Post by jmszr on 2011-04-03
TimmyK,

I saw that you had "libdvdcss2" installed but I'm not clear as to whether you have "libdvdread4" installed also. If not, it needs to be installed.

SMPlayer plays a lot of formats out-of-the-box. Definitely give that a try.

---

### Post by bingmicrosoft on 2011-04-03
hey man [URL="https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"]try here 
[/URL]

---

### Post by TimmyK. on 2011-04-03
Hi, yes, I have libdvdread4. SMPlayer did not work.

I realized on VLC I had "No DVD menus" disabled, so I enabled it, and VLC gave me this notice:
```
Playback failure:
DVDRead could not read block 4.
```

---

### Post by TimmyK. on 2011-04-05
Any ideas what might be the problem here?

---

### Post by SeijiSensei on 2011-04-05
Maybe it's this: [http://www.gossamer-threads.com/lists/mythtv/users/442817](http://www.gossamer-threads.com/lists/mythtv/users/442817)

---

