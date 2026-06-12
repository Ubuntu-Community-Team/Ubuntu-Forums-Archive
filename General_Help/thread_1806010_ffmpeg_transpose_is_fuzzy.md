---
title: "ffmpeg transpose is fuzzy"
date: 2011-07-17
forum: General Help
---

### Post by goneskiing on 2011-07-17
if I take video from my phone horizontally, I need to rotate the video before editing in kdenlive

I tried:
ffmpeg myvideo.3gp -vf "transpose=2" myvideo_rotated.mp4

this comes out correctly rotated but a little fuzzy

I had to change from 3gp to mp4 since it gave error that 3gp could not be output at rotated format

could this be cleared up by specifying input or output size or aspect ratio ?

---

### Post by FakeOutdoorsman on 2011-07-17
It's probably fuzzy because you're using the default settings which automatically use a low bitrate for the output file. A lossless intermediate file would be a good choice here:
```
ffmpeg -i input.3gp -vcodec huffyuv -vf transpose=2 -acodec copy output.mkv
```
Lossless files can be huge, but you will mostly avoid introducing additional quality loss, and these files are usually temporary when you need to re-encode for the editor.

---

### Post by goneskiing on 2011-07-17
> **FakeOutdoorsman said:**
> It's probably fuzzy because you're using the default settings which automatically use a low bitrate for the output file. A lossless intermediate file would be a good choice here:
```
ffmpeg -i input.3gp -vcodec huffyuv -vf transpose=2 -acodec copy output.mkv
```
Lossless files can be huge, but you will mostly avoid introducing additional quality loss, and these files are usually temporary when you need to re-encode for the editor.

thks for info but it came out in grayscale (very clear though)

also do you then convert before going into editor (kdenlive for me) 
if so, do you simply ffmpeg temp.mkv roated.???  do you suggest.avi or .mp4 ?

---

### Post by FakeOutdoorsman on 2011-07-18
> **goneskiing said:**
> thks for info but it came out in grayscale (very clear though)
That shouldn't happen. What player(s) is it grayscale? Or is it just grayscale in Kdenlive? You can try another output container:
```
ffmpeg -i input.3gp -vcodec huffyuv -vf transpose=2 -acodec pcm_s16le output.avi
```
or another encoder:
```
ffmpeg -i input.3gp -vcodec ffv1 -vf transpose=2 -acodec copy output.mkv
```

> **goneskiing said:**
> also do you then convert before going into editor (kdenlive for me)
No. You want to convert as few times as possible. The only reasons to convert in this case are if Kdenlive won't accept your original video and/or Kdenlive won't rotate a video. I'm not sure if any of these assumptions are true, however.

---

### Post by goneskiing on 2011-07-19
> **FakeOutdoorsman said:**
> That shouldn't happen. What player(s) is it grayscale? Or is it just grayscale in Kdenlive? You can try another output container:
```
ffmpeg -i input.3gp -vcodec huffyuv -vf transpose=2 -acodec pcm_s16le output.avi
```
or another encoder:
```
ffmpeg -i input.3gp -vcodec ffv1 -vf transpose=2 -acodec copy output.mkv
```


No. You want to convert as few times as possible. The only reasons to convert in this case are if Kdenlive won't accept your original video and/or Kdenlive won't rotate a video. I'm not sure if any of these assumptions are true, however.


kdenlive accepts the original videos just fine - I didn't see anyway for it to rotate the entire video but if anyone knows if it does I'd like to hear how (yes, keeping things to a minimum is good).

---

