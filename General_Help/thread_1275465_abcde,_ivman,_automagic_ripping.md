---
title: "abcde, ivman, automagic ripping"
date: 2009-09-25
forum: General Help
---

### Post by TehSnarf on 2009-09-25
Alright, I've been attempting to set up a system of autoripping my cd's using ivman and abcde. I found the howto over at [sudocode.blogspot.com]("http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html"), but I seem to have ran in to an issue.

I've got ivman set up to run as my user, tehsnarf, with the group cdrom, and it seems to run fine. The action I have set up to execute when a cd is put in, is:
```

    <ivm:Match name="hal.volume.disc.type" value="cd_rom">
        <ivm:Match name="hal.volume.disc.has_audio" value="true">
            <ivm:Match name="hal.volume.disc.has_data" value="false">
                <ivm:Option name="exec" value="abcde -Nxo mp3 -c /etc/abcde.conf" />
            </ivm:Match>
        </ivm:Match>
    </ivm:Match>

```

abcde runs fine if I normally execute it with the above command, but when I run ivman via "sudo ivman -d --nofork", I get the error:
```

manager.c:1501 (main) Entering main loop.
mkdir: cannot create directory `//abcde.7d0a1a0c': Permission denied
abcde: Temp directory //abcde.7d0a1a0c could not be created.

```

... and I don't know why, or how to change the tmp directory. Any clues around this?

---

### Post by TehSnarf on 2009-09-25
Adding this to /etc/abcde.conf fixed it:
```
WAVOUTPUTDIR='/tmp'
```

---

