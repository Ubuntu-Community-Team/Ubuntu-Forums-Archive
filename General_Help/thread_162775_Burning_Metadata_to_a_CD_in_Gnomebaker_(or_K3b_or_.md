---
title: "Burning Metadata to a CD in Gnomebaker (or K3b or anything)"
date: 2006-04-19
forum: General Help
---

### Post by Third Thoughts on 2006-04-19
Alright so I'm trying to burn an audio CD, but I want it to have the track information on the CD so that when someone else goes to rip it, or play it on their computer it won't just say Track1, Track2, etc. So far I haven't figured out how to do this. I've tried both Gnomebaker and K3b. Gnomebaker doesn't seem to have any options relating to metadata. K3b has an option called Write CD-text, which I enabled, but it didn't do anything useful. Anyone know how to do this?

~Andrew S.

---

### Post by dcstar on 2006-04-20
[QUOTE=Third Thoughts]Alright so I'm trying to burn an audio CD, but I want it to have the track information on the CD so that when someone else goes to rip it, or play it on their computer it won't just say Track1, Track2, etc. So far I haven't figured out how to do this. I've tried both Gnomebaker and K3b. Gnomebaker doesn't seem to have any options relating to metadata. K3b has an option called Write CD-text, which I enabled, but it didn't do anything useful. Anyone know how to do this?

~Andrew S.[/QUOTE]
When did Audio CDs ever have this in them?, as far as I know this data is not part of the CD standard, so it will not be possible to do it.

The whole reason things like CDDB exist is because CDs do not have this information in them.

---

### Post by Third Thoughts on 2006-04-21
[QUOTE=dcstar]When did Audio CDs ever have this in them?, as far as I know this data is not part of the CD standard, so it will not be possible to do it.

The whole reason things like CDDB exist is because CDs do not have this information in them.[/QUOTE]

Yeah, oops my bad. I just did some research on CDDB and I had a mistaken notion that it allowed rippers to identify individual tracks. So what was confusing me is that Sound Juicer could figure out track information on my store bought CDs but not on my burned CDs. I thought this meant there was some peice of information on the CD that it was reading and that if I configured my burning software correctly I could embed the information on my burned CDs. But a quick Wikipedia look up of CDDB cleared that up for me. Thanks for helping me remedy my confusion. 

~Andrew S.

---

### Post by maubp on 2006-06-29
[QUOTE=dcstar]When did Audio CDs ever have this in them?, as far as I know this data is not part of the CD standard, so it will not be possible to do it.[/QUOTE]
It is an optional part of the "Red Book" CD standard.

Some CDs come with CD-Text, which some modern CD-Players will display (especially jukeboxes and things by Sony).  Some computer programs will display it (most don't).

And some computer programs like k3b will burn it - which is great :)

---

### Post by newlinux on 2006-07-14
> **dcstar said:**
> When did Audio CDs ever have this in them?, as far as I know this data is not part of the CD standard, so it will not be possible to do it.

The whole reason things like CDDB exist is because CDs do not have this information in them.

Many audio CDs have had them for years. Many new cars come equipped to read CD-text. I've been burning CD-text discs for years because my car decks and cd software use the info. I don't do it so mucb now because I play MP3s in my car and at home and use the ID3 tags. CDDB is great, but when you make mixed CDs or your're using them without an Internet connection it's useful to have CD-text.

So K3B can write CD-text? Any Gnome specific apps write CD-text?

---

### Post by newlinux on 2006-07-16
> **Third Thoughts said:**
> ... Gnomebaker doesn't seem to have any options relating to metadata. K3b has an option called Write CD-text, which I enabled, but it didn't do anything useful. Anyone know how to do this?

~Andrew S.

I was able to write with CD-Text using K3B. Make sure you are using an app (or device) that can read CD-Text to test to see if it was written. Most don't.

---

### Post by Hal58 on 2006-07-22
I have been making CD-Text CDs for several years now to store album/artist/title data for old vinyl I've captured.  I do this with 'cdrdao' in command-line mode with a manually-edited .TOC file.

Unfortunately, I have yet to find a player in Dapper that will display the data (although my Toyota Prius will, albeit only Album/Title instead of the Artist/Title I would prefer).

Here is a sample of the first part of one of my .toc files:

```
CD_DA
 
CD_TEXT {
  LANGUAGE_MAP {
    0: 9
  }
  LANGUAGE 0 {
    TITLE "Pearl Sisters Hits, KST-2"
    PERFORMER "Pearl Sisters"
    DISC_ID "KST-2 "                    // -- Exactly 6 characters added ?
  }
}
 
// Track 1
TRACK AUDIO
COPY
NO PRE_EMPHASIS
TWO_CHANNEL_AUDIO
ISRC "000000000000"
CD_TEXT {
  LANGUAGE 0 {
    TITLE "Shireo  (Hate To Cry)"
    PERFORMER "Pearl Sisters"
  }
}
FILE "Track01.wav" 0    // Length from file instead of indices
SILENCE 0:2:0           //-- added
                                                                                
// Track 2

```

I place the .toc file in the directory with the .wav files, then execute the following command from a root shell to keep latency problems under control (also with networking deactivated):

cdrdao write --device ATAPI:0,0,0 --driver generic-mmc-raw --speed 4 <toc>

The device name may need altering (/dev/hdc, 1,0,0 or something else), and the '<toc>' should be replaced with the actual name of your .toc file (the example above was named 'KST-2.toc').  Also, for reliable burning, I keep the burn speed to no more than 8, and usually 4 on CD-RWs, and (knock on wood) haven't made a coaster in over two years.

Does anyone know of a CD player in Dapper that will display CD-text data?

Hal
[http://home.att.net/~halbower/](http://home.att.net/~halbower/)

---

### Post by newlinux on 2006-07-22
> **Hal58 said:**
> 

Does anyone know of a CD player in Dapper that will display CD-text data?


I think mcdp might...

---

### Post by Hal58 on 2006-07-24
> **newlinux said:**
> I think mcdp might...

Not on an Athlon system with DVD-R/RW drive under Ubuntu 6.06 (Dapper).  Thanks for the pointer, though.  Nice little player.

Hal

---

