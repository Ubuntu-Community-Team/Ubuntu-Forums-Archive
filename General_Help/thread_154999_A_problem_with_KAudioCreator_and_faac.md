---
title: "A problem with KAudioCreator and faac"
date: 2006-04-04
forum: General Help
---

### Post by Baikonur on 2006-04-04
I'm trying to rip cd's with KAudioCreator, using faac as the encoder. The command line I use is ```
faac -o %o -b '320' -w --artist %{artist} --title %{title} --year %{year} --genre %{genre} --album --track %{number} %f
```

Every time I try to rip something, even a single track, it gives an error, that says: "Cannot encode several input files to one output file." 

Can anyone shed some light on the matter?

---

### Post by flebber on 2006-04-04
Any reason you are not using the GUI version it works well.

---

### Post by Baikonur on 2006-04-04
I am using the GUI, but it hasn't got faac preconfigured as an encoder, so i have had to configure the command line it uses myself, and i'm obviously doing it wrong.

---

### Post by trotski on 2006-04-04
Weird.   I think you're missing the %{albumtitle} for one thing.

One thing you could always try is doing a test run with as few options as possible.  Then keep adding more in order to see where the fault lies.

---

### Post by gingermark on 2006-04-04
[QUOTE=Baikonur]I'm trying to rip cd's with KAudioCreator, using faac as the encoder. The command line I use is ```
faac -o %o -b '320' -w --artist %{artist} --title %{title} --year %{year} --genre %{genre} --album --track %{number} %f
```

Every time I try to rip something, even a single track, it gives an error, that says: "Cannot encode several input files to one output file." 

Can anyone shed some light on the matter?[/QUOTE]

Typing 'faac --long-help' at the command line gives you the following:
```
Freeware Advanced Audio Coder
FAAC 1.24

Usage: faac [options] infiles ...

Quality-related options:
  -q <quality>  Set default variable bitrate (VBR) quantizer quality in percent
                (default: 100, averages at approx. 120 kbps VBR for a normal
                stereo input file with 16 bit and 44.1 kHz sample rate; max.
                value 500, min. 10).Set quantizer quality.
  -b <bitrate>  Set average bitrate (ABR) to approximately <bitrate> kbps.
  -c <freq>     Set the bandwidth in Hz (default: automatic, i.e. adapts
                maximum value to input sample rate).

Input/output options:
  - <stdin>     If you simply use a hyphen/minus sign instead of an input
                file name, FAAC can encode directly from stdin, thus enabling
                piping within other applications like foobar2000 (see example
                below). The same works for stdout as well, so FAAC can pipe its
                output to other apps such as mp4live (streaming live AAC
                content).
  -o X          Set output file to X (only for one input file)
  -P            Raw PCM input mode (default: off, i.e. expecting a WAV header;
                necessary for input files or bitstreams without a header; using
                only -P assumes the default values for -R, -B and -C in the
                input file).
  -R            Raw PCM input sample rate in Hz (default: 44100 Hz, max. 96 kHz)
  -B            Raw PCM input sample size (default: 16, also possible 8, 24, 32
                bit fixed or float input).
  -C            Raw PCM input channels (default: 2, max. 33 + 1 LFE).
  -X            Raw PCM swap input bytes (default: bigendian).
  -I <C[,LFE]>  Input multichannel configuration (default: 3,4 which means
                Center is third and LFE is fourth like in 5.1 WAV, so you only
                have to specify a different position of these two mono channels
                in your multichannel input files if they haven't been reordered
                already).
  -r            aw AAC output mode (i.e. without ADTS headers, needed when
                directly using the AAC bitstream in a MP4 container like e.g.
                mp4live does; -w uses this mode automatically).

MP4 specific options:
  -w            Wrap AAC data in MP4 container. (default for *.mp4 and *.m4a)
  --artist X    Set artist to X
  --writer X    Set writer to X
  --title X     Set title to X
  --genre X     Set genre to X
  --album X     Set album to X
  --compilation Set compilation
  --track X     Set track to X (number/total)
  --disc X      Set disc to X (number/total)
  --year X      Set year to X
  --cover-art X Read cover art from file X
                Supported image formats are gif, jpg, and png.
  --comment X   Set comment to X

Expert options:
  --no-tns      Disable TNS, temporal noise shaping, coding.
  --no-midside  Don't use mid/side coding.
  --mpeg-vers X AAC MPEG version, X can be 2 or 4.
  --obj-type X  AAC object type. (LC (Low Complexity, default), Main or LTP
                (Long Term Prediction)
  --shortctl X  Enforce block type (default: both; 1 = short only; 2 = long
                only).

Documentation:
  --license     Show the FAAC license.
  --help        Show this abbreviated help.
  --long-help   Show complete help.

  More tips can be found in the audiocoding.com Knowledge Base at
  <http://www.audiocoding.com/wiki/>
```

I have no experience with faac, but if I had to try and guess, I'd think that maybe the -o %o part is the problem, as you're looking to encode more than one file.

What happens if you remove that bit?

Otherwise, I got nothing, but maybe that help page can help you or others to figure it out if I'm wrong. Good luck! :p

---

### Post by Baikonur on 2006-04-04
Well, if I do as you suggest, the error changes into "Multiple input files not supported yet.", but as I mentioned earlier, the same error(s) comes even if I try  to rip a single track. But, thanks anyway for the effort.

---

### Post by Baikonur on 2006-04-04
Trotski, missed your post earlier, but whaddayaknow, adding the %{Albumtitle} actually fixed it :P Thanks!

---

### Post by wb34 on 2008-03-21
Does anyone know how to change the bitrate when ripping to AAC using FAAC in Kaudiocreator? when i change the "encoder priority" nothing seems to change

---

### Post by wb34 on 2008-03-21
Also, come to think of it, does anyone know how to rip to AAC in K3b, because it rips much faster than Kaudiocreator. the same command that worked for Kaudiocreator doesn't work for k3b.

---

