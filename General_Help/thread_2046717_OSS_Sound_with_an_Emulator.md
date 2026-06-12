---
title: "OSS Sound with an Emulator"
date: 2012-08-23
forum: General Help
---

### Post by Kodeine on 2012-08-23
Salutations!

so I'm trying to get the sound to work with an emulator. The sound plugin is set to use OSS however upon starting a game up I get this in terminal.```
SPU: open("/dev/dsp", O_WRONLY): No such file or directory
SPU: AudioDevice Disabled.
 * Open spu[0]
```

I've asked on the emulation software's forum but no one seems to know. Is this a problem with OSS or the audio plugin?

---

### Post by kostkon on 2012-08-23
OSS has been removed from the kernel. OSS is no more.

Try running the emulator with padsp, i.e.
```
padsp emulator_executable
```

Which emulator is it?

---

### Post by Kodeine on 2012-08-26
> **kostkon said:**
> OSS has been removed from the kernel. OSS is no more.

Try running the emulator with padsp, i.e.
```
padsp emulator_executable
```

Which emulator is it?

Ah I wasn't aware of it's removal. I used your padsp command it that works fine. Thanks!

---

