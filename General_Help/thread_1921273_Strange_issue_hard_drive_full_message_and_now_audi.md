---
title: "Strange issue hard drive full message and now audio/video playback is choppy."
date: 2012-02-06
forum: General Help
---

### Post by lotsofish on 2012-02-06
I was using Brasero to watch some video I have stored on a network hard drive. When the video finished, I got an error message stating that Brasero wasn't able to run a SQL statement due to the hard drive being full. The hard drive is definitely not full, and the results I got from Disk Usage Analyzer were pretty weird. It showed that I had a 488.2GB hd (correct 500gb - swap and small extended partition), used 449gb and had 0 free. The graphs only showed the 38gb that I had used.

After rebooting the machine, the hard drive space is showing again at norrmal values (488.2gb capacity, 38.8gb used, 449.4gb available) but a new problem has started. Video playback is so choppy I can't watch it, and audio files will have these glitches in them where the audio repeats a second or two every 20-30 seconds. I have another OS installed in Virtualbox, and it's been slower to use it. 

I have run fsck on startup and it doesn't look like there are any errors. Disk Utility shows that S.M.A.R.T reports the HD as good. I've done a data read benchmark and am getting 66.6 mb/s read rates. 

Is my HD going bad, even though the numbers look ok? What other tests should I perform?

---

### Post by lotsofish on 2012-02-06
Well... I ran through some of the tests the bios has built in (hard drive, memory) and found no errors. After rebooting again, the problem with laggy video and audio seems to have gone away.

---

