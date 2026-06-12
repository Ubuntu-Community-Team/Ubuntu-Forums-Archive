---
title: "DVD Write Error"
date: 2006-03-16
forum: General Help
---

### Post by antonmills on 2006-03-16
Hey all, I'm fairly new to linux and have come accross a problem when writing DVD's so I thought it's best to come ask the experts before giving up and going back to windows.

When writing a DVD I could only ever get it to write to 20%ish and then it would fail. the images were on average 4-4.2G and all fit on to a single layer dvd-r.
Having doing some research on here I noticed some others having similar problems and followed their route and enabled DMA on my drive.

Now it writes an image to the drive but im receiving write errors:

> anton@prescott:/www$ growisofs -dvd-compat -Z /dev/hdc=Image.iso
Executing 'builtin_dd if=Image.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 12.3x1385KBps.
   1605632/4645341184 ( 0.0%) @0.0x, remaining 144:36
:-? the LUN appears to be stuck writing LBA=310h, retry in 47ms
   1605632/4645341184 ( 0.0%) @0.0x, remaining 337:25
   1605632/4645341184 ( 0.0%) @0.0x, remaining 482:01
:-? the LUN appears to be stuck writing LBA=310h, retry in 47ms
   1605632/4645341184 ( 0.0%) @0.0x, remaining 626:38
:-? the LUN appears to be stuck writing LBA=310h, retry in 47ms
   1605632/4645341184 ( 0.0%) @0.0x, remaining 819:26
   1605632/4645341184 ( 0.0%) @0.0x, remaining 964:03
:-? the LUN appears to be stuck writing LBA=310h, retry in 47ms
   1605632/4645341184 ( 0.0%) @0.0x, remaining 1108:39
:-? the LUN appears to be stuck writing LBA=310h, retry in 47ms
   1605632/4645341184 ( 0.0%) @0.0x, remaining 1301:28
   1605632/4645341184 ( 0.0%) @0.0x, remaining 1446:04

It got over that but stumbles upon more errors (note that that the LBA's all end with 310!):

> the LUN appears to be stuck writing LBA=30310h, retry in 47ms
 404258816/4645341184 ( 8.7%) @0.0x, remaining 18:42
 404258816/4645341184 ( 8.7%) @0.0x, remaining 19:14
:-? the LUN appears to be stuck writing LBA=30310h, retry in 47ms
 404258816/4645341184 ( 8.7%) @0.0x, remaining 19:45
:-? the LUN appears to be stuck writing LBA=30310h, retry in 47ms
 404258816/4645341184 ( 8.7%) @0.0x, remaining 20:27
 404258816/4645341184 ( 8.7%) @0.0x, remaining 20:58
:-? the LUN appears to be stuck writing LBA=30310h, retry in 47ms
 404258816/4645341184 ( 8.7%) @0.0x, remaining 21:30

The disc has written and I can read it but in places in the movie it skips and I'm wondering if it's this write error that keeps happening. I hate to say this but the process was perfect on windows, just wish I could get this sorted on linux.

I've thought this could be bad media or bad images but its a consistant error, any advice?

Thanks in advance for all/any replies!
antonmills.

---

### Post by antonmills on 2006-03-16
anyone? bump.

---

### Post by dpaint4 on 2006-03-16
Wow. All I can say is that I have the same issue on my new HP laptop but I was blaming all their new weird technology like 'lightscribe' and stuff. I just figured I had a stupid drive.

But all that stuff you've done to work on it is way over my head. I'll hang out with you and see what people say, if anyone else has been through this.

Sometimes dosen't it just make yout want to find a nice square laptop with no media keys, no weird card readers built in and no **feature-packed** burners.

If someone would market a completely featureless notebook, that'd be the one I'd buy. :D Just because of stuff like this.

---

### Post by antonmills on 2006-03-16
Try enabling your dma, if its not already. I followed this guide:
[http://doc.gwos.org/index.php/DMA]("http://doc.gwos.org/index.php/DMA")

my only difference was the dvd-r was /dev/hdc. Enabling this stopped me making complete coasters (failed burns) now it just seems to have retry errors on LBA's ending with 310h?!? Bizarre.

Also post your output from a failed write, the community here seem quite helpful from the posts I read. GUI Burning software doesn't give much feedback so it might be best to use a commandline tool like cdrecord or growisofs.

Im a complete newbie too, your not alone :)

---

### Post by dpaint4 on 2006-03-17
[QUOTE=antonmills]Try enabling your dma, if its not already. I followed this guide:
[http://doc.gwos.org/index.php/DMA]("http://doc.gwos.org/index.php/DMA")

my only difference was the dvd-r was /dev/hdc. Enabling this stopped me making complete coasters (failed burns) now it just seems to have retry errors on LBA's ending with 310h?!? Bizarre.

Also post your output from a failed write, the community here seem quite helpful from the posts I read. GUI Burning software doesn't give much feedback so it might be best to use a commandline tool like cdrecord or growisofs.

Im a complete newbie too, your not alone :)[/QUOTE]


Thanks a lot. I'll try this tonight.

---

### Post by bluevoodoo1 on 2006-03-17
You could also try a different brand of disc (or even type). My burner is supposed to burn DVD+Rs, so I bought some cheap TDK DVD+Rs, but I couldn't them working. Bought some Verbatim DVD-Rs and they worked fine. You might also consider burning at a slower speed. For me 2x works great, I've burned at 4x and 16x and got coasters. So anything more than 2x seems like a risk for a "coaster."

---

### Post by dpaint4 on 2006-03-17
Nope. THat tutorial completely fixed the issue as far as I can tell. Additionally I used to get an error durring boot that the drive was 'unsupported media' or something, with a few strange numbers after it. I now no longer get that message, so I think, despite having no clue what I just did, it was the right thing.

Thanks a lot. I was going to just live with this, but now it seems I don't have to. (A recurring theme in my adoption of Ubuntu, which is nice.)

---

### Post by taurus on 2006-03-17
[QUOTE=bluevoodoo1]You could also try a different brand of disc (or even type). My burner is supposed to burn DVD+Rs, so I bought some cheap TDK DVD+Rs, but I couldn't them working. Bought some Verbatim DVD-Rs and they worked fine. You might also consider burning at a slower speed. For me 2x works great, I've burned at 4x and 16x and got coasters. So anything more than 2x seems like a risk for a "coaster."[/QUOTE]
I guess you probably got a bad batch of TDK DVD+Rs because I got 50 of them from CompUSA and both Sony and NEC DVD burners write fine (30 so far) even at 16x.

---

### Post by bluevoodoo1 on 2006-03-17
[QUOTE=taurus]I guess you probably got a bad batch of TDK DVD+Rs because I got 50 of them from CompUSA and both Sony and NEC DVD burners write fine (30 so far) even at 16x.[/QUOTE]

Perhaps. I got 100 pack from CompUSA and not 1 has worked. Maybe I'll give them another shot...

---

### Post by taurus on 2006-03-17
I guess that's up to you although Verbatim is a little more expensive than TDK!

---

### Post by bluevoodoo1 on 2006-03-17
[QUOTE=taurus]I guess that's up to you although Verbatim is a little more expensive than TDK![/QUOTE]

That is very true. I'll check out some cheaper DVD-Rs because I think it's a matter of +R or -R. (with +R not working)

---

