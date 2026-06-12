---
title: "Using ffmpeg to convert .MTS to .MOV"
date: 2011-05-22
forum: General Help
---

### Post by jakupl on 2011-05-22
I'm trying to convert a .MTS video file to .mov, and I need to use ffmpeg, because I want it to be scriptable.

I managed to convert the file to .avi using this command:

```
ffmpeg -i INPUT.MTS  -vcodec libxvid -b 18000k -acodec libmp3lame -deinterlace -ab 192k -s 1280x720 -r 50 OUTPUT.avi
```

Any suggestions?

Thanks :)

---

### Post by kd7swh on 2011-05-22
Try something like:

```
ffmpeg -i [input.mts] -vcodec dnxhd -acodec pcm_s16be [output.mov]
```

Edit:

hmmmm...

If you want the input and output to be scriptable you could just set them as $VARs in a shell script:

```
ffmpeg -i [$1] -vcodec dnxhd -acodec pcm_s16be [$2]
```

That maybe enough.

---

### Post by jakupl on 2011-05-22
> **kd7swh said:**
> Try something like:

```
ffmpeg -i [input.mts] -vcodec dnxhd -acodec pcm_s16be [output.mov]
```

Edit:

hmmmm...

If you want the input and output to be scriptable you could just set them as $VARs in a shell script:

```
ffmpeg -i [$1] -vcodec dnxhd -acodec pcm_s16be [$2]
```

That maybe enough.

Thanks :)
That gives me this error:

```
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by jakupl on 2011-05-22
Ok I think I figured it out.

```
ffmpeg -i INPUT.MTS -sameq -deinterlace OUTPUT.mov
```

And during the process, I figured out that this is a better way of doing the avi files:

```
ffmpeg -i INPUT.MTS  -vcodec libxvid -acodec libmp3lame -deinterlace -ab 192k -sameq OUTPUT.avi
```

---

