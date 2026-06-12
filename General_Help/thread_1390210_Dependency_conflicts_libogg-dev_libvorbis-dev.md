---
title: "Dependency conflicts libogg-dev libvorbis-dev"
date: 2010-01-25
forum: General Help
---

### Post by Probable on 2010-01-25
I'm using Karmic and I'm trying to install Ruby Gosu, but it requires libsdl-mixer1.2-dev. That package depends on libogg-dev and libvorbis-dev. I can't install libogg-dev or libvorbis-dev because they both depend in turn on packages that have newer installed versions and that I apparently can't roll back without killing a lot of other dependencies on my system. 

I.e. the latest version of libogg-dev is 1.1.4~dfsg-1 and requires libogg0 v1.1.4~dfsg-1 but libogg0 v1.1.4-1 is installed. 

The latest version of libvorbis-dev is 1.2.0.dfsg-6ubunto0.1 and depends on that version of libvorbis0a, libvorbisenc2, and libvorbisfile3, but version 1.2.3-1 of those packages is installed, and if I try to change to the prior version, I'm warned that a very long list of other packages will have to be removed, which I don't want to do.

So. Help?

---

### Post by johnaaronrose on 2012-01-30
I'm getting much the same problem with Lucid. Did you solve the problem?

---

