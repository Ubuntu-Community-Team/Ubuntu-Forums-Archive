---
title: "MIDI file - no sound"
date: 2006-02-23
forum: General Help
---

### Post by madubuntuer on 2006-02-23
Why dont I get sound when playing midi files using tse3play. I told it to use oss but I still dont get any sound. But wav works fine. tse3play as least appears to be able to play it but playmidi says playback device not found. 
I have checked the permissions of /dev/midi and it's rwx for everyone. It cant be problems with /dev/dsp cos thats what vlc uses. Vlc plays wav and other stuff fine.

is this what i have to do [http://linux-sound.org/quick-toots/4-sequencers_and_softsynths/quick-toot-midisynth_howto.html](http://linux-sound.org/quick-toots/4-sequencers_and_softsynths/quick-toot-midisynth_howto.html)
but I'm unable to load the modules it mensions because it cant find them. /dev/sequencer has rw permissons for everyone

---

### Post by dcstar on 2006-02-24
[QUOTE=madubuntuer]Why dont I get sound when playing midi files using tse3play. I told it to use oss but I still dont get any sound. But wav works fine. tse3play as least appears to be able to play it but playmidi says playback device not found.
I have checked the permissions of /dev/midi and it's rwx for everyone. It cant be problems with /dev/dsp cos thats what vlc uses. Vlc plays wav and other stuff fine.

is this what i have to do [http://linux-sound.org/quick-toots/4-sequencers_and_softsynths/quick-toot-midisynth_howto.html](http://linux-sound.org/quick-toots/4-sequencers_and_softsynths/quick-toot-midisynth_howto.html)
but I'm unable to load the modules it mentions because it cant find them. /dev/sequencer has rw permissons for everyone[/QUOTE]
"timidity" plays midi stuff fine on my system, give it a try.

---

### Post by madubuntuer on 2006-02-24
thats just it it doesn't work
i get this error
timidity: error while loading shared libraries: libOSSlib.so: cannot open shared object file: Error 40

---

