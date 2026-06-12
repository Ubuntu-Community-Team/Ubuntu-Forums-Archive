---
title: "How to Burn 1080p DVDs"
date: 2011-10-30
forum: General Help
---

### Post by jflesher on 2011-10-30
I created a 1080p video in Blender, now to burn it to DVD, but all the tools I normally use to burn DVDs, like DeVeDe, only go up to 720p, which may mean that no one as updated these apps since the 1080p format came out. 

What application can burn DVD's in 1080p format:

---

### Post by mjuhasz on 2011-10-30
The DVD-VIDEO specification does not contain 1080p videos therefore you can't burn a dvd disk that you can play on your dvd player from a 1080p source.
You can burn it as a data dvd and play it on pc or you can burn a blu-ray disk (use tsmuxer to create the file structure or iso) that you can play on BD players.

These are the supported dvd-video resolutions:

PAL Video:

720 x 576 pixels MPEG2 (Called Full-D1)
704 x 576 pixels MPEG2
352 x 576 pixels MPEG2 (Called Half-D1, same as the CVD Standard)
352 x 288 pixels MPEG2
352 x 288 pixels MPEG1 (Same as the VCD Standard)
25 fps
16:9 Anamorphic (only supported by 720x576)

NTSC Video:

720 x 480 pixels MPEG2 (Called Full-D1)
704 x 480 pixels MPEG2
352 x 480 pixels MPEG2 (Called Half-D1, same as the CVD Standard) 
352 x 240 pixels MPEG2
352 x 240 pixels MPEG1 (Same as the VCD Standard) 
29,97 fps
23,976 fps with 3:2 pulldown = 29,97 playback fps (NTSC Film, this is only supported by MPEG2 video)
16:9 Anamorphic (only supported by 720x480)

---

### Post by jflesher on 2011-10-30
Thanks, I guess I should have said Blu-ray, DVD is no longer a term applicable to 1080, its like asking about CD video formats to burn a 720p; my bad, but great reply, thanks for the info.

I did download tsMuxeR and will give it a shot, the app looks great, but now the real question is what format to burn the Blu-ray at, or more to the point, 
what settings to use for Blender to make the original video, at present I took a preset of HDV NTSC 1080p, with a frame rate of 29.97, 
currently blender doesn't have an encoding preset for Blu-ray, 
so I took H264 format, AC3 bit rate set to 384, 48k audio files; but this produces an AVI file, that TsMuxeR will not use as an input format, 
so I tried mkv encoding, this will take hours to render, so in the mean time, this question really isn't about blender, that question would be better asked on a blender forum, 
but in general about the format that works best for making 1080p or 720p Blu-ray and DVD's, this changes all the time, and currently the information out there all seems to center around a software package, more than a standard.

I used Handbrake to convert the AVI into an m4v format, You Tube converted it fine, and I used 30 fps, instead of 29.97; which at the time made sense to me, but not for burning Blu-ray I'm sure, so now its time to render in a format that will work for both.

Thanks

---

