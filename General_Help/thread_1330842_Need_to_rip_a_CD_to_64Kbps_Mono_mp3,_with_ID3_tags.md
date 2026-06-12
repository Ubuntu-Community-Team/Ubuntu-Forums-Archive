---
title: "Need to rip a CD to 64Kbps Mono mp3, with ID3 tags"
date: 2009-11-18
forum: General Help
---

### Post by mjpatey on 2009-11-18
OK, this has been a long journey, and I hope to bring it to a happy end here in the forums!  As the subject says, I'm trying to rip from CD and encode to 64 Kbps Mono mp3 with ID3 tags created by me, all in one job.

I've tried a few options out there, and the closest I've come to success is RubyRipper, which actually did finally make my files perfectly... but it did not behave as expected when creating the output file.  I told it to output to a particular folder, and it would rip, then tell me the output folder I specified already exists, giving me the option to overwrite the folder or automatically rename it.  Automatically renaming worked, but now I have a gazillion needless folders.

The LAME options I use when converting to mp3 (and they do work) are as follows:

```
lame -a -m m -q 0 -b 64 --cbr
```...I've played with ABCDE (wonderful as a command-line tool, but I'd like a GUI for all the manual ID3 tagging I'll be doing) and I can't get SoundJuicer to successfully make an mp3 with the options that I need.  If you have any idea how to get the gstreamer pipeline in SoundJuicer working for me instead of against me, I'd love to give that another try!  But for now I'm out of ideas.  Anyone?

Thanks in advance for any light you can shed!

-Mark

---

### Post by dcstar on 2009-11-18
> **mjpatey said:**
> OK, this has been a long journey, and I hope to bring it to a happy end here in the forums!  As the subject says, I'm trying to rip from CD and encode to 64 Kbps Mono mp3 with ID3 tags created by me, all in one job.

I've tried a few options out there, and the closest I've come to success is RubyRipper, which actually did finally make my files perfectly... but it did not behave as expected when creating the output file.  I told it to output to a particular folder, and it would rip, then tell me the output folder I specified already exists, giving me the option to overwrite the folder or automatically rename it.  Automatically renaming worked, but now I have a gazillion needless folders.

The LAME options I use when converting to mp3 (and they do work) are as follows:

```
lame -a -m m -q 0 -b 64 --cbr
```...I've played with ABCDE (wonderful as a command-line tool, but I'd like a GUI for all the manual ID3 tagging I'll be doing) and I can't get SoundJuicer to successfully make an mp3 with the options that I need.  If you have any idea how to get the gstreamer pipeline in SoundJuicer working for me instead of against me, I'd love to give that another try!  But for now I'm out of ideas.  Anyone?

Thanks in advance for any light you can shed!

-Mark

Try grip.

---

