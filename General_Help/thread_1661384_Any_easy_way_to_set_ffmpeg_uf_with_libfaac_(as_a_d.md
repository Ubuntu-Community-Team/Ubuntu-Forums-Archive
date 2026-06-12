---
title: "Any easy way to set ffmpeg uf with libfaac (as a dependency)?"
date: 2011-01-06
forum: General Help
---

### Post by Zilioum on 2011-01-06
I'm currently writing a small wrapper program to unbox/box mkv files into mp4. Often the mkv have dts sound, so I need to convert it to aac. This works well on my own pc's where I compiled ffmpeg from source with libfaac support.
At some point in the future I would like to release this little program as a PPA, and for this I want the setup process to be as easy as possible. ffmpeg would be a dependency, but the version in the repositories comes without libfaac. I know that I always could tell users to build ffmpeg from source as I did, but that's not really user friendly. 
Is there an easier way to add aac support to ffmpeg?

---

