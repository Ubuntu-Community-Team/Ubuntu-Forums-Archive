---
title: "vlc as background process"
date: 2010-04-09
forum: General Help
---

### Post by Esthellin on 2010-04-09
Before anyone asks, I have already looked on the VLC forums with no luck at all. I thought it would be easier to post here as most people seem to reply to these forums rather than VLC forums :P.


I am trying to run everything from the one shell but can't because of vlc not being able to be put as a background process but still be playing the music.
I want to be able to start vlc from the command line with a command line interface (such as ncurses). Then to put vlc in the background (with the music still playing) then start using w3m for example. But then to be able to suspend that process, foreground vlc, and pause the song or change to the next one.
I have gotten cvlc to be backgrounded and still music (cvlc music &) but nvlc doesn't like this. It can't play and be suspended at the same time.

Any ways around this?

Also, I do not want to use screen as all the other programs I use (nano, finch, w3m) do not work properly under screen (the shortcut keys stuff up), so I would prefer not to hear any solutions involving screen, unless they can tell me how to get all the keys to work correctly (as these programs need to use the Ctrl and Esc key for functions and the screen program doesn't allow these to be used)

---

### Post by mcduck on 2010-04-09
This might not be the answer you were looking for, since it doesn't tell you how to fix the VLC problem (sorry about that :)).

...but, have you considered using MPD instead of VLC? It's *designed* to run in the background, and ncmpc is excellent ncurses-based client. Using those instead of VLC would avoid the whole problem, as you could simply close the client if you need to, and MPD itself would still continue playing the music in the background..

---

### Post by Esthellin on 2010-04-09
> **mcduck said:**
> This might not be the answer you were looking for, since it doesn't tell you how to fix the VLC problem (sorry about that :)).

...but, have you considered using MPD instead of VLC? It's *designed* to run in the background, and ncmpc is excellent ncurses-based client. Using those instead of VLC would avoid the whole problem, as you could simply close the client if you need to, and MPD itself would still continue playing the music in the background..

I have had a look via aptitude at these programs. But these programs won't be able to play all my AAC (.mp4) music files that I have.
Also, I would like to play video files with the player (obviously the video output wouldn't be command line based) where the player is a command line program. That is why I have been using vlc so much; it plays almost ANYTHING :P (I have lots of different video type files)

Would I be able to extend MPD somehow to play m4a files or video?

EDIT: A few people suggested mplayer to me so I checked it out. It did the same thing as VLC and stopped when Ctrl-Z was pressed to suspend it.

EDIT: I am looking to find a way to watch videos without X. Is this possible?

---

### Post by mcduck on 2010-04-09
> **Esthellin said:**
> I have had a look via aptitude at these programs. But these porograms won't be able to play all my AAC (.mp4) music files that I have.
Also, I would like to play video files with the player (obviously the video output wouldn't be command line based) where the player is a command line program. That is why I have been using vlc so much; it plays almost ANYTHING :P (I have lots of different video type files)

Would I be able to extend MPD somehow to play m4a files or video?
It does support AAC, but definitely not video. So if playing video with the same app is requirement then VLC and MPlayer are the best options.

> 
Decoder Plugins: AudioFile, libfaad (aac and mp4), ffmpeg, FLAC, fluidsynth, libmad and libmpg123 (mp3), Musepack, OggFlac, OggTremor, OggVorbis, WavPack, libsidplay, libsndfile, wildmidi

Output Plugins: ALSA, FIFO, JACK, OSS, OSX, libao, PulseAudio, Media MVP, Shoutcast/MP3, Shoutcast/Ogg Vorbis

Metadata: APEv2, id3v1, id3v2, MP4, Vorbis

Mixers: ALSA, OSS, Software Mixing

Protocols: TCP, IPv6, and Unix Domain Sockets


---

### Post by Esthellin on 2010-04-09
> **mcduck said:**
> It does support AAC, but definitely not video. So if playing video with the same app is requirement then VLC and MPlayer are the best options.

See above about the MPlayer problem :P. Neither it nor VLC lets me suspend it without pausing first (which is pointless)

---

### Post by mcduck on 2010-04-09
> **Esthellin said:**
> See above about the MPlayer problem :P. Neither it nor VLC lets me suspend it without pausing first (which is pointless)
So you are sending it to background with Ctrl-Z? I don't think any player will keep on playing that way, as it effectively pauses the execution of the program.

If you want the program to continue running in the background, you need to use the "bg" command. Of course in your situation you'd need to do that from another terminal (although first using Ctrl-Z to get out of nvlc and then using bg to send it to run in background might work, I've never tried doing such thing and probably it will just stay paused even after the bg command)

---

### Post by Esthellin on 2010-04-10
I ended up using the following commands:

screen -d -m nvlc -LZ musicFolder/ 2>/dev/null
to start the vlc by itself and
screen -R
to access it if I want to change the song. This is working for now until I can find a different solution :)

---

