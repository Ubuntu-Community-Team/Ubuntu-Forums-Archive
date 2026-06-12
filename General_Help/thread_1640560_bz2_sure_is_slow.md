---
title: "bz2 sure is slow"
date: 2010-12-07
forum: General Help
---

### Post by sofasurfer on 2010-12-07
I compressed a directory containing many image files. The directory amounted to 5.3gig. Compressed with TAR using .tgz the compression took a couple minutes at most and compressed down to 4.3 gig. Compressed using .bz2 the compression took about 90 minutes and compressed down to 4.2 gig. Hardly worth the extra time.
Do these numbers look normal to you?

---

### Post by squaregoldfish on 2010-12-08
Image files typically don't compress well at all (they're usually already compressed), so it's no surprise that there's not much difference in size between the two outcomes. bzip uses a much more complex algorithm than gzip, which is why it takes longer to run. On files that are easily compressible you will see a marked improvement in compression from bzip, but it will take longer.

Basically you have to choose the right tool for the files you're compressing, and whether you want a trade-off of speed over compression. There's probably some good guidelines on this around the net, but I've simply learned by trial and error. I tend to use bzip for archiving where I won't need to decompress often, or for large data sets to be sent over the net where the transfer time outweighs the compression/decompression time.

Steve.

---

