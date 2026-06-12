---
title: "Blocksize ddrescue?"
date: 2010-05-04
forum: General Help
---

### Post by NorQue on 2010-05-04
Hey,

will be getting a crashed HDD on Thursday which I have to recover some files from, have already read through the [Data Recovery](https://help.ubuntu.com/community/DataRecovery) documentation and am quite confident that we'll manage to get at least some of that stuff back. There's only one question left I have about ddrescue: I assume it will be *slow*. Of course, it should be, since we want as much stuff back as possible, as reliable as possible.

*But:* I remember from using dd to image a drive the last time I could speed up the process tremendously by raising the blocksize to 4M, resulting in a lot more data being read and written at once. Is there a similar switch in ddrescue? I assume -b does not serve this purpose, since it says it's the "*hardware block size of input device [512]*" of the device? How does it know that the HDDs block size is 512 (I assume that's bytes), anyways? Is that always the case or could it be different? Could I raise the limit for the -c switch ("*hardware blocks to copy at a time [128]*)?

Thanks in Advance!

---

