---
title: "Change .wav to .ogg"
date: 2010-09-03
forum: General Help
---

### Post by measekite on 2010-09-03
I am using K3b.  I would like to change FROM the ,wav format to .ogg.  Does this require special software or can K3b do it.

Anybody know of a cookbook approach?

---

### Post by MooPi on 2010-09-03
Not what you wanted.

---

### Post by cj.surrusco on 2010-09-03
I don't understand exactly what you're asking, but I use the Gnome SoundConverter to encode audio. It works great for me, and it does support .ogg.

---

### Post by andrew.46 on 2010-09-04
Hi measekite,

> **measekite said:**
> I am using K3b.  I would like to change FROM the ,wav format to .ogg.  Does this require special software or can K3b do it.

The very simplest tool to do this is oggenc, part of the vorbis-tools package:

```
sudo apt-get install vorbis-tools
```

Typical syntax would be:

```

oggenc -q 6 input.wav -o output.ogg

```

k3b is perhaps not the best tool for such a job.

Andrew

---

### Post by howefield on 2010-09-04
> **measekite said:**
> I am using K3b.  I would like to change FROM the ,wav format to .ogg.  Does this require special software or can K3b do it.

If you are asking how to rip a CD to .ogg, K3B will do this easily enough if you have the correct plugins installed, (which I think are part of the standard K3B install).

After you select the tracks for ripping and press the Start Ripping button, what options do you have in the drop down FileType field ? 

Although I'd use oggconvert for the task.

> Anybody know of a cookbook approach?

Not unless you want to bake a cake, in which case, I'd recommend a Madeira.

---

### Post by AlphaLexman on 2010-09-04
> **measekite said:**
> I am using K3b.  I would like to change FROM the ,wav format to .ogg.  Does this require special software or can K3b do it.
If you mean can k3b rip a cd to ogg format, then yes it can and no it does not require special software, although it require the correct plugin which is installed by default.

To check for the plugin, click -> Settings -> Configure K3b... -> Plugins 
Scroll down and see if the 'K3b Ogg Vorbis Encoder' is checkmarked, click the wrench icon at the right to adjust the settings of the encoder, bit rate, etc.

To rip / record in ogg, click -> Tools, -> Rip Audio CD... -> Start Ripping (another window will pop-up) -> then select 'Ogg-Vorbis' from the Filetype dropdown menu, and click _S_tart Ripping

Good Luck!

EDIT: Oops I was too slow, sorry for the double info.

---

### Post by measekite on 2010-09-04
> **measekite said:**
> I am using K3b.  I would like to change FROM the ,wav format to .ogg.  Does this require special software or can K3b do it.

Anybody know of a cookbook approach?


Thanks to all of you for the multiple ways to get the job done.  I installed oggconvert from Synaptic and found the menu item in sound and video.  The only thing I was not sure of is the number (quality level) where the default is 3.  I did it twice, once at 3 and the other all of the way up.  The file size is larger on the higher number but I could not hear much if any difference in quality.

As for Vorbis Tool I already had them installed but could not find a menu item so I did not know how to use them.  If someone could point me in the right direction that would be very helpful.

---

### Post by AlphaLexman on 2010-09-04
Many different encoders have 'default' values for quality encoding, usually these values are based on a 1-10 scale or a 1-8 scale, with the higher value being more quality.

As a general rule, I take the highest quality value [8 or 10] divide it in half, and add 1. This usually gives a good balance between compression and audio quality.

---

### Post by andrew.46 on 2010-09-04
Hi measekite,

> **measekite said:**
> As for Vorbis Tool I already had them installed but could not find a menu item so I did not know how to use them.  If someone could point me in the right direction that would be very helpful.

The [vorbis-tools package]("http://packages.ubuntu.com/lucid/vorbis-tools") is a small collection of commandline tools, therefore there will be no menu item to consult. Details of the various tools (oggenc, ogg123, vorbiscomment, ogginfo and a few others) can be seen in their respective man pages.

Andrew

---

### Post by measekite on 2010-09-05
> **andrew.46 said:**
> Hi measekite,



The [vorbis-tools package]("http://packages.ubuntu.com/lucid/vorbis-tools") is a small collection of commandline tools, therefore there will be no menu item to consult. Details of the various tools (oggenc, ogg123, vorbiscomment, ogginfo and a few others) can be seen in their respective man pages.

Andrew

Thanks, took a look based on your link but failed to find the documentation on how to issue the commands and arguments.  Do you have a link for documentation.

---

### Post by andrew.46 on 2010-09-05
Hi measekite,

> **measekite said:**
> Thanks, took a look based on your link but failed to find the documentation on how to issue the commands and arguments.  Do you have a link for documentation.

Basic usage can usually be found by using the *--help* option, for example:

```

andrew@skamandros~$ **[COLOR="Red"]oggenc --help[/COLOR]**
oggenc from vorbis-tools 1.2.0 
(c) 2000-2005 Michael Smith <msmith@xiph.org>

Usage: oggenc [options] inputfile [...]

OPTIONS:
 General:
 -Q, --quiet          Produce no output to stderr
 -h, --help           Print this help text
 -v, --version        Print the version number
 -k, --skeleton       Adds an Ogg Skeleton bitstream
 -r, --raw            Raw mode. Input files are read directly as PCM data
 -B, --raw-bits=n     Set bits/sample for raw input. Default is 16
 -C, --raw-chan=n     Set number of channels for raw input. Default is 2
 -R, --raw-rate=n     Set samples/sec for raw input. Default is 44100
 --raw-endianness     1 for bigendian, 0 for little (defaults to 0)
 -b, --bitrate        Choose a nominal bitrate to encode at. Attempt
                      to encode at a bitrate averaging this. Takes an
                      argument in kbps. By default, this produces a VBR
                      encoding, equivalent to using -q or --quality.
                      See the --managed option to use a managed bitrate
                      targetting the selected bitrate.
 --managed            Enable the bitrate management engine. This will allow
                      much greater control over the precise bitrate(s) used,
                      but encoding will be much slower. Don't use it unless
                      you have a strong need for detailed control over
                      bitrate, such as for streaming.
 -m, --min-bitrate    Specify a minimum bitrate (in kbps). Useful for
                      encoding for a fixed-size channel. Using this will
                      automatically enable managed bitrate mode (see
                      --managed).
 -M, --max-bitrate    Specify a maximum bitrate in kbps. Useful for
                      streaming applications. Using this will automatically
                      enable managed bitrate mode (see --managed).
 --advanced-encode-option option=value
                      Sets an advanced encoder option to the given value.
                      The valid options (and their values) are documented
                      in the man page supplied with this program. They are
                      for advanced users only, and should be used with
                      caution.
 -q, --quality        Specify quality, between -1 (very low) and 10 (very
                      high), instead of specifying a particular bitrate.
                      This is the normal mode of operation.
                      Fractional qualities (e.g. 2.75) are permitted
                      The default quality level is 3.
 --resample n         Resample input data to sampling rate n (Hz)
 --downmix            Downmix stereo to mono. Only allowed on stereo
                      input.
 -s, --serial         Specify a serial number for the stream. If encoding
                      multiple files, this will be incremented for each
                      stream after the first.
 --discard-comments   Prevents comments in FLAC and Ogg FLAC files from
                      being copied to the output Ogg Vorbis file.

 Naming:
 -o, --output=fn      Write file to fn (only valid in single-file mode)
 -n, --names=string   Produce filenames as this string, with %a, %t, %l,
                      %n, %d replaced by artist, title, album, track number,
                      and date, respectively (see below for specifying these).
                      %% gives a literal %.
 -X, --name-remove=s  Remove the specified characters from parameters to the
                      -n format string. Useful to ensure legal filenames.
 -P, --name-replace=s Replace characters removed by --name-remove with the
                      characters specified. If this string is shorter than the
                      --name-remove list or is not specified, the extra
                      characters are just removed.
                      Default settings for the above two arguments are platform
                      specific.
 -c, --comment=c      Add the given string as an extra comment. This may be
                      used multiple times. The argument should be in the
                      format "tag=value".
 -d, --date           Date for track (usually date of performance)
 -N, --tracknum       Track number for this track
 -t, --title          Title for this track
 -l, --album          Name of album
 -a, --artist         Name of artist
 -G, --genre          Genre of track
                      If multiple input files are given, then multiple
                      instances of the previous five arguments will be used,
                      in the order they are given. If fewer titles are
                      specified than files, OggEnc will print a warning, and
                      reuse the final one for the remaining files. If fewer
                      track numbers are given, the remaining files will be
                      unnumbered. For the others, the final tag will be reused
                      for all others without warning (so you can specify a date
                      once, for example, and have it used for all the files)

INPUT FILES:
 OggEnc input files must currently be 24, 16, or 8 bit PCM WAV, AIFF, or AIFF/C
 files, 32 bit IEEE floating point WAV, and optionally FLAC or Ogg FLAC. Files
  may be mono or stereo (or more channels) and any sample rate.
 Alternatively, the --raw option may be used to use a raw PCM data file, which
 must be 16 bit stereo little-endian PCM ('headerless wav'), unless additional
 parameters for raw mode are specified.
 You can specify taking the file from stdin by using - as the input filename.
 In this mode, output is to stdout unless an output filename is specified
 with -o

```

More detailed instructions can be seen in the man pages, for example:

```
man oggenc
```

will reveal the above information + more detail. Follow the same for the rest of the vorbis-tools package.

Andrew

---

