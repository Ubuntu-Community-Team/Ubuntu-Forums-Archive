---
title: "A Little Contribution - PSP Conversion Script"
date: 2011-01-04
forum: General Help
---

### Post by gerowen on 2011-01-04
I thought I would make a little contribution to the community.  I recently bought my wife a PSP.  She's pregnant and likes video games, but she hurts if she has to sit up for long periods of time, so I got her a PSP since she can link it with the PS3 and read comics, play games, etc.  Well one of the first issues we ran into was that none of the programs in the repositories (Arista, Transmaggadon or something, Handbrake no longer has a preset and neither does WinFF, and OGMRIP will only take input from DVDs.) that have PSP presets worked.  They would convert the video sure, but the PSP wouldn't play them.  She has a God of War edition PSP 3000.  So I wrote a little script for her to convert videos and they seem to work just fine on her PSP.  I've attached the script to this post so feel free to take it.  Just make it executable, double click it and click "Run from Terminal".  I just threw this together in about 20 minutes so if you want release notes open the file in a text editor, I threw comments in there so when I go back to edit it and upgrade it when she starts bugging me for new features I don't forget what does what.  I named it AnyPSP because it just popped into my head and a quick Google search on the name didn't turn anything up.

Edit: Features she's already asked for that I'll see about working into it.
1) Playing a sound when it's done along with the popup message, or at least an option to do so.
2) A "pretty" desktop icon.

On top of that I'll probably throw in some things like error checking (you don't have the codecs necessary, etc.)

---

### Post by gerowen on 2011-01-04
For those of you who prefer to write your own stuff, or are in a command line only environment, here's the workhorse of the script that actually does the conversion.

```

ffmpeg -i "sourcevideo" -f psp -r 29.97 -b 768k -ar 24000 -ab 64k -s 320x240 "destinationvideo"
```

---

### Post by gerowen on 2011-01-04
Just ran into an issue.  The current command arguments work fine as long as the video does not have more than 2 audio channels.  This probably shouldn't affect you unless you're trying to put an HD digital copy of a BluRay movie on your PSP like I am, :p

I'll have to revisit the command's arguments when I'm more awake in the morning and see if I can fix this.

---

