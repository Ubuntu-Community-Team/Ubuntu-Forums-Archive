---
title: "Split HD FLAC using Cue"
date: 2010-09-09
forum: General Help
---

### Post by jamesisin on 2010-09-09
Normally I use shnsplit to break an album length FLAC into track lengths:

[http://www.soundunreason.com/InkWell/?p=980](http://www.soundunreason.com/InkWell/?p=980)

However, if I attempt to do so on an HD FLAC (24x96 rather than 16x44) I get this message:

> shnsplit: error: m:ss.ff format can only be used with CD-quality files


A little help?

---

### Post by jamesisin on 2010-09-09
Anybody?

---

### Post by jamesisin on 2010-09-10
Am I the only person using high-definition FLAC files on Ubuntu?

---

### Post by jamesisin on 2010-09-11
[tap tap tap]  Is this thing on?

---

### Post by jamesisin on 2010-09-11
Hello?

---

### Post by jamesisin on 2010-09-12
Bummer.

---

### Post by qyot27 on 2010-09-15
It can be done, just not with that program combination - I tried with just about every iteration of options I could think of with shntool, and it failed every single time.

It also requires more steps and doing FLAC->PCM->FLAC (which shouldn't matter, as FLAC is lossless, but the underlying principle of it means it takes longer than a simple split).

1) Use mkvmerge (from the MKVToolNix package) to put the FLAC in Matroska, using the CUE file for the chapter information.  Optionally, you could use *flac -d* first and then give mkvmerge a PCM Wave and CUE instead.  It might be cleaner this way in Step 4.

2) Use MediaInfo to get the chapter times.

3) Use mkvmerge again (either on the .mka created in Step 1, or the original files), telling it to split on the timecodes you got from MediaInfo.  Leave out the entry for 00:00:00.000, you don't need that one.

4) Use ffmpeg to decode (in the case of FLAC .mka files, *-acodec pcm_s24le*) or mkvextract to extract (*mkvextract tracks track[1|2|3|4|...].mka 1:track[1|2|3|4|...].wav*) (for PCM .mka files) the individual tracks to PCM Wave files.

5) Use flac to compress the individual tracks back to FLAC.

6) Tag as necessary.




As an aside, it's possible to open/split a 24-96 FLAC into individual tracks using foobar2000 under Windows (albeit through a FLAC->FLAC conversion, again not a simple split), and I've seen recommendations to use it in Wine for the ability to split stuff.  Unfortunately, I couldn't seem to get Wine to recognize the installer properly, due to NSIS errors.  Therefore, I couldn't test it on Ubuntu.

---

### Post by jamesisin on 2010-09-17
Sheet.

Step seven: pistol whip the yahoo who made the long flac instead of making short ones.

Ok.  This will take some doing, but I'll get working on it probably tomorrow or maybe over the weekend.

Thanks for your efforts here.  This is a lot of information.

---

### Post by cascade9 on 2010-09-17
> **qyot27 said:**
> As an aside, it's possible to open/split a 24-96 FLAC into individual tracks using foobar2000 under Windows (albeit through a FLAC->FLAC conversion, again not a simple split), and I've seen recommendations to use it in Wine for the ability to split stuff.  Unfortunately, I couldn't seem to get Wine to recognize the installer properly, due to NSIS errors.  Therefore, I couldn't test it on Ubuntu.

Possibly thats a WINE/foobar version problem. You could try an earlier version of foobar, I've had no problems with my quite old 0.9.4 version. Mind you, I've never tried doing any conversions with it, I just use it for playing files, tag editing and replaygain scanning. 

Well, used, I hosed my install with WINE + FB2K, when I get the horrid mess of computers here sorted out I'll reinstall.

*Edit- had seen this thread before, I hadnt even thought to using FB2K fro splitting. Liek most things, it seems obvious now you've said it. BTW, great info ;)

---

### Post by Ranko Kohime on 2010-09-17
> **jamesisin said:**
> Step seven: pistol whip the yahoo who made the long flac instead of making short ones.
I don't download those kinds of files, for that specific reason.  :)

---

### Post by qyot27 on 2010-09-17
> **cascade9 said:**
> Possibly thats a WINE/foobar version problem. You could try an earlier version of foobar, I've had no problems with my quite old 0.9.4 version. Mind you, I've never tried doing any conversions with it, I just use it for playing files, tag editing and replaygain scanning.
Yeah, the version difference is probably the culprit.  I could also wait for Wine to update again, as I'm sure something like this is often quickly resolved (considering NSIS's development is based at Sourceforge).  Or you could always install it to a USB stick under Windows by choosing the Portable option, and then use that.  I don't know if the Converter works in Portable mode, though.


What would be nicer/more novel, is the ability to mount CUE+[WAV/FLAC/TTA/WV/APE/etc.] files and have them get read as a device, regardless of bit depth and frequency.  Then it'd just be a matter of getting Rhythmbox or other tools to accept such a device giving them audio at higher resolutions than CD-standard 2ch/16bit/44.1kHz PCM streams, along with being able to convert to X destination format, without downsampling.



To further comment on my previous instructions, mkvmerge's GUI has the option to display the used command line.  I mention this because I usually find it easier to use the GUI for mkvmerge if I have to do more complex stuff like that, at least long enough to copy the necessary commands.  Then you can just adapt the command as necessary.  The options for using a CUE file for the chapter info and the split functions are on the Global tab.
```
flac -d test24-96.flac
mkvmerge -o "test24-96.mka"  "--forced-track" "0:no" "--compression" "0:none" "-a" "0" "-D" "-S" "-T" "--no-global-tags" "--no-chapters" "test24-96.wav" "--track-order" "0:0" "--chapters" "testwav.cue"
mediainfo "test24-96.mka"
```
Resulting chapter times (they're so short because I created this example file out of 30-second previews):
```
00:00:29.800
00:00:59.653
00:01:29.453
00:01:59.240
00:02:29.093
00:02:58.946
00:03:28.746
00:03:58.600
00:04:28.453
00:04:58.253
```
Plug these timecodes into mkvmerge to do the splitting, then extract the splitted tracks, and compress to FLAC (extraction and FLAC compression treated as a single file for simplicity - there's probably a way to easily wildcard this step, or just do it the simplest way and duplicate the steps for the # of distinct files, changing the input and output names accordingly).
```
mkvmerge -o "test24-96 (1).mka"  "--forced-track" "0:no" "--compression" "0:none" "-a" "0" "-D" "-S" "-T" "--no-global-tags" "--no-chapters" "test24-96.wav" "--track-order" "0:0" "--split" "timecodes:00:00:29.800,00:00:59.653,00:01:29.453,00:01:59.240,00:02:29.093,00:02:58.946,00:03:28.746,00:03:58.600,00:04:28.453,00:04:58.253" "--chapters" "testwav.cue"
mkvextract tracks "test24-96 (1)-001.mka" 1:track1.wav
flac -8 track1.wav
```
Note: flac will probably complain about the fact that the file has a legacy Wave header even though the bit depth is 24.  This is because Wave files above 16bits and/or 2 Channels are supposed to have WAVEFORMATEXTENSIBLE headers.  Apparently mkvextract doesn't write these yet (or I haven't found the option to force it to).  For simple 24-bit Stereo files, this is a non-issue, as flac can encode them fine despite the warning.  If you've got 5.1 Channels, though, this likely requires a slightly amended method, because the header stores the channel ordering information.  In such a case, you can run it through wavi (a Windows app; you'll need Wine) to write a correct header for it.  You can also do this to the Stereo files if you just don't like flac complaining, even though it's not absolutely necessary.
```
wine wavi -x track1.wav track1-fix.wav
flac -8 track1-fix.wav
```

wavi's download page:
[http://sourceforge.net/projects/wavi-avi2wav/files/](http://sourceforge.net/projects/wavi-avi2wav/files/)

As you might notice, wavi's help uses Windows' system parameter notation - /X, /M, etc. - for the options, but it also accepts these in normal (-x, -m) forms too.

---

### Post by jamesisin on 2010-10-05
I have written a script for streamlining this splitting process (it also works on APE files):

[http://jamesisin.com/a_high-tech_blech/index.php/2010/09/conquer-giant-ape-and-giant-flac/](http://jamesisin.com/a_high-tech_blech/index.php/2010/09/conquer-giant-ape-and-giant-flac/)

---

### Post by heavynetol on 2012-01-04
Here is the solution this works for me:
```

cuebreakpoints $MYFILE.cue | sed s/$/0/ | shnsplit -o flac $MYFILE.flac

```Try it.  Bye >:[

---

### Post by jamesisin on 2012-01-04
heavynetol - cuebreakpoints is now superfluous.  Take a look at my script:

[http://jamesisin.com/a_high-tech_blech/index.php/2010/09/conquer-giant-ape-and-giant-flac/](http://jamesisin.com/a_high-tech_blech/index.php/2010/09/conquer-giant-ape-and-giant-flac/)

---

### Post by cruiseoveride on 2012-04-03
heavynetol's solution worked perfectly for me. Thanks.

---

### Post by ariel on 2012-12-08
The simple solution by heavynetol worked for me too.

here is some more detailed explanation of why shntool misbehaves:

[http://www.linuxquestions.org/questions/linux-software-2/shnsplit-error-m-ss-ff-format-can-only-be-used-with-cd-quality-files-solution-913764/](http://www.linuxquestions.org/questions/linux-software-2/shnsplit-error-m-ss-ff-format-can-only-be-used-with-cd-quality-files-solution-913764/)

---

