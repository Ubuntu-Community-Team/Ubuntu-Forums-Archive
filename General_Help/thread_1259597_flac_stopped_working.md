---
title: "flac stopped working"
date: 2009-09-06
forum: General Help
---

### Post by tacutu on 2009-09-06
hi.

I noticed today that flac stopped working. It doesn't want to decode anymore.

I tried to encode a wav file:
```
flac -V track01.wav -o test.flac
```
and everything went fine. However, when I tried to decode the flac file, I got this:
```
flac -d test.flac 

```
```
test.flac: 28% completetest.flac: *** Got error code 2:FLAC__STREAM_DECODER_ERROR_STATUS_FRAME_CRC_MISMATCH


test.flac: ERROR while decoding data
           state = FLAC__STREAM_DECODER_READ_FRAME

```

This happened with several freshly ripped wav files, on different hard disks (so possible bad sectors on the hdd are not the cause)

I tried to reinstall flac, but I got the same errors. THe only thing I could think of is that I got a memory upgrade recently, but I ran memtest and it seemed fine. Moreover, if the memory were faulty, I'd expect random errors with other programs, too, but that is not the case.

Any ideas? What could it be?

---

### Post by tacutu on 2009-09-06
i hate doing this but... bump!

---

### Post by mc4man on 2009-09-06
You've probably eliminated the prime cause (hdd), though there is that memory upgrade... 

Out of curiosity if you went```

flac -F  test.flac -o test-1.flac

```
And  then tried to decode test-1.flac

---

### Post by tacutu on 2009-09-07
> **mc4man said:**
> 

Out of curiosity if you went```

flac -F  test.flac -o test-1.flac

```
And  then tried to decode test-1.flac

This works. I succesfully decoded test-1.flac, but I'm not sure what this means.

Meanwhile, I ran a memtest for an hour and a half (2 passes) and had no problems.

Since I have 2 computers running Ubuntu 8.04, I tested them both and found out this:

a. flac encoded on bad computer -> CRC errors when decoded on good computer. 
b. flac encoded on good computer -> no errors when decoded on bad computer

so it seems to me that the problem on the bad computer is the encoding process --- although I used the -V switch.

---

### Post by tacutu on 2009-09-07
oh, crap! I put in the old memory modules and everything works juuust fine.

---

### Post by mc4man on 2009-09-07
What happens if you take a .wav from good and encode on bad without -V ? Will it decode (without -F

Also  if you take that flac successfully decoded to .wav on bad (with the -F) and again encode on bad, will it decode (without -F

(( there is assumption that playback of the 'bad' flacs is ok ...?

edit, missed your post,, so it was the memory

---

