---
title: "Audio stopped working, multiple errors."
date: 2012-09-23
forum: General Help
---

### Post by Drew012 on 2012-09-23
My sound stopped working recently seemingly out of nowhere. Here is what I get when I run:

Input: ```
lspci | grep -i audio
```

Output: ```
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)

```

When I try to reinstall a bunch of the pulseaudio files using synaptic package manager, I get this error:
```
(Reading database ... 
dpkg: warning: files list file for package `ttf-umefont' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-droid' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'pulseaudio' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

```

I do not know what the ttf* files are, apparently some font file? I do know they are constantly causing dpkg to cause make errors every time it is invoked. This is a problem because I cannot use synaptic without getting these errors apparently.

One other thing to mention is my sound (logitech computer speakers) do work, however, they are randomly glitchy. Also, the build in linux music player rhythmbox has a toolbar at the top near the time. The volume bar on this is stuck at mute. Also when I go in to the sound settings on that same toolbar none of my input/output audio devices show up! Yet they still work I just cannot control them. I actually might be able to live with it but there is one problem. I use two output devices that I need to switch between (wireless headphones and speakers.) It is stuck on speakers right now, I cant see that it is defaulted on speakers but I know it is because they work and my headphones dont.

Any ideas?
12.04

---

