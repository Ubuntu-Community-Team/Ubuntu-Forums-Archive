---
title: "Error Found in MPD Log: can't find alsa mixer control &quot;PCM&quot;"
date: 2010-04-28
forum: General Help
---

### Post by dannymichel on 2010-04-28
I found one error in my MPD log.
```
Apr 28 22:25 : can't find alsa mixer control "PCM"

```any ideas?

---

### Post by Nencio on 2010-07-02
I had the same message running mpd with Lucid.
I solved it by replacing 
```

audio_output {
        type            "alsa"
        name            "My ALSA Device"
}

```with
```

audio_output {        
        type    "pulse"
        name    "My MPD PulseAudio Output"
}

```in my ~/.mpdconfig file.

You can also check here for more info: 
[http://mpd.wikia.com/wiki/Configuration#Audio_Outputs](http://mpd.wikia.com/wiki/Configuration#Audio_Outputs)

---

