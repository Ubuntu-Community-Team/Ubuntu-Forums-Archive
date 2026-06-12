---
title: "Sound Juicer with 192 or 224 kbps mp3 format?"
date: 2009-08-05
forum: General Help
---

### Post by hihihi100 on 2009-08-05
Hi there:

Does any of u know if i can configure Sound Juicer to record at 192, maybe 224 kbps in mp3 format? Is there any package I should download?

If sound juicer cannot record at those "non standard" kbps, does any of u know of any application that allows it?

And, by the way, can I further compress a FLAC file? Being a lossless format, it consumes way too much space (my POV).

Cheers

---

### Post by fisheater on 2009-08-05
I faced the same problem, have a read of this. There is no radio button to click, but the workaround is fairly easy.

enjoy,

FE

[http://www.calebscreek.com/blog/index.php/2008/09/howto-enable-mp3-ripping-in-sound-juicer-2220/](http://www.calebscreek.com/blog/index.php/2008/09/howto-enable-mp3-ripping-in-sound-juicer-2220/)

Max quality: MP3 work around: audio/x-raw-int,rate=44100,channels=2 ! lame preset=insane ! id3v2mux

---

### Post by hihihi100 on 2009-08-08
Can't I configure it to just 224 kbps?

---

### Post by fisheater on 2009-08-08
I too am new to linux, and this seems like the way to do it.

Try preset=extreme and have a listen, it will be very close to what you are after.

FE

---

