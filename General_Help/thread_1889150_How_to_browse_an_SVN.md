---
title: "How to browse an SVN?"
date: 2011-11-30
forum: General Help
---

### Post by ron999 on 2011-11-30
Hi
I know it's possible to browse a _**git**_ online, like this here --> [http://git.videolan.org/?p=ffmpeg.git]("http://git.videolan.org/?p=ffmpeg.git")
And I can browse it on my hard drive using a program such as **gitg**.
But is it possible to view an _**SVN**_ such as mPlayer's?

---

### Post by andrew.46 on 2011-12-01
I believe it has not been possible to browse the MPlayer svn repository via the web for a while. There was a DOS attack and a debacle with the hosting server, not sure which put an end to browsing the repository. A less than satisfactory solution is to save part or all of the logs offline. Save the last 200 changes:

```

svn log svn://svn.mplayerhq.hu/mplayer/trunk -l 200 > mplayer_log

```

for example. Leave off the *-l 200 *to save the entire log :).

---

