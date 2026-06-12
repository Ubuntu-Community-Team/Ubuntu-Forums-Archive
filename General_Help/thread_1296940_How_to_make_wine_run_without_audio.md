---
title: "How to make wine run without audio?"
date: 2009-10-21
forum: General Help
---

### Post by ansiktsburk on 2009-10-21
How can I make wine run without any audio, ever! I don't want wine to even think about using audio.

I  have yet not found any setting for comopletly removing sound from wine.   running winecfg just shows me a list of sound drivers that makes no sense. OSS, etc.  Where is the big panic button to remove all kind of audio?

---

### Post by bobtfish on 2009-10-21
In wine config window: "Select a sound driver by checking the box of the desired driver. **Disable sound by not selecting a driver**. etc..."

Chris

---

### Post by ansiktsburk on 2009-10-21
Running winecfg tells me:

[ ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8139494")ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: File or directory does not exist
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: File or directory does not exist
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: File or directory does not exist

I check nothing.

running

wine .wine/drive_c/program/foo.exe

says:

ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed:File or directory does not exist

That sounds (pun intended) to me like it is doing something with sound...

Then the program fails to run
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b8455b0 (thread 0009), starting debugger...                                                                                               
First chance exception: 0xc0000025 in 32-bit code (0x7bc3bb3e).  

Not sure if this has anything with sound to do, but wine is doing something with the sound. At least it seems that to me.
[ ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8139494")

---

