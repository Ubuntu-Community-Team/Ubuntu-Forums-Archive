---
title: "How do I disable video Thumbnails?"
date: 2010-01-10
forum: General Help
---

### Post by UnusedUserNameHere on 2010-01-10
I have Ubuntu 9.10, and writing video files to a mounted disk is slow. The reason is every time the buffer is flushed to disk, Ubuntu starts making a new video thumbnail for the file.

If I skip the first block that has the RIFF data, then Ubuntu doesn't realize it's a video, and the write speed is about doubled. Then I can write the RIFF data at the end of the transfer (in the appropriate place in the file).

I have tried setting an exclusive flock on the file while writing; however, that does not prevent Ubuntu from reading the file while it's being written and generating thumbnails.

---

### Post by spiderbatdad on 2010-01-10
In File Management Preferences you can select "show thumbnails" "never."

---

