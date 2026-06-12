---
title: "multimedia codec"
date: 2012-05-23
forum: General Help
---

### Post by shahrokh196 on 2012-05-23
> **lord gold said:**
> convert mp3 music files to 3gp (psp) using ubuntu on ps3. ?? anyone know where to start?

i cant install codec multimedia pleas help me

---

### Post by howefield on 2012-05-23
Post moved to own thread.

---

### Post by roelforg on 2012-05-23
```

sudo apt-get install libavcodec-53-extra

```
Pulls in the extra codecs for most apps including ffmpeg.
using ffmpeg to convert files is easy:
```

ffmpeg -i <name_of_input_file>.<file_extension> <name_of_target_file>.<extension_corresponding_with_the_desired_format>

```

---

### Post by polki@mac.com on 2012-05-24
Do you mean libavcodec-extra-53?

---

### Post by Colo2 on 2012-05-24
Isn't it the gstreamer plugins you need? - In the repos.

---

