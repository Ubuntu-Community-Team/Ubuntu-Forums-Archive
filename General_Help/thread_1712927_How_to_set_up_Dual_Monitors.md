---
title: "How to set up Dual Monitors"
date: 2011-03-23
forum: General Help
---

### Post by WlaadDyaab on 2011-03-23
Hi

First of all I did do my research before I posted this thread

The closest I found and managed to understand was from this YouTube tutorial: [http://www.youtube.com/watch?v=g6EYc4bJ6JQ&feature=channel_video_title](http://www.youtube.com/watch?v=g6EYc4bJ6JQ&feature=channel_video_title)

The problem is that I don't have NVIDIA graphics card

These are my HP ProBook 4510s Laptop's specification: [http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/321957-321957-64295-3929941-3955552-3934828-3934829-3956011.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/321957-321957-64295-3929941-3955552-3934828-3934829-3956011.html)

And I think my built-in graphics card is Mobile Intel® 4500MHD

Did anyone Dual Monitor with this Laptop or knows how to Dual Monitor with it?

Thanks

---

### Post by HermanAB on 2011-03-23
Super simple really.  Just plug the second monitor in, then run Gnome with Compiz.

The days of fiddling with settings to make it work are long gone.

---

### Post by WlaadDyaab on 2011-03-23
> **HermanAB said:**
> Super simple really.  Just plug the second monitor in, then run Gnome with Compiz.

The days of fiddling with settings to make it work are long gone.

Oh OK thanks for saying that. I thought there were other programs involved

I opened Compiz and looked around for anything resembling two monitors but couldn't find any

How do I do the settings in Compiz for Dual Monitors?

---

### Post by WlaadDyaab on 2011-03-23
[SOLVED]

How I got Dual Monitoring to work for myself

Laptop: HP ProBook 4510s
Linux Distro: Ubuntu 10.10

The other computer monitor: Pro Lite 38a (Liyama)

Note: This monitor looks old and isn't the average thin and glossy design one you see in computer shops these days Lol. So I think any computer monitor should work in Dual Monitoring

How I got Ubuntu Desktop to appear on the other screen:

- I got the monitor
- Plugged it to the mains
- Got the monnitor's male VGA cable and inserted in to my Laptop (not all Laptops have VGA input. That's how it looks like [http://en.wikipedia.org/wiki/VGA_connector](http://en.wikipedia.org/wiki/VGA_connector))

On my Ubuntu Desktop:

- System > Preferences > Monitors
- Linux detected the other monitor and showed this: "Liyama North America 15"" on the other monitor (top-left corner of the screen). And "Laptop" on my Laptop (top-left corner of the screen)

[ATTACH]186910[/ATTACH]

Notice how my six workspaces expanded (horizontally. Or like a wide screen) rather than stay as they were; box shaped. Obviously that also means that screenshots with Dual Monitors change, or that's how it appears to me anyway

- On "Monitor Preferences" I left-clicked on the pink box "Liama North America 15"" (whilst still holding on the left button on the mouse) and moved it to the left side of "Laptop". Because my other monitor is on the left side of my Laptop
- Apply
- Keep This Configuration
- Close

When I never needed the other monitor I simply unplugged it's VGA connector. I don't know if that's the right way or not but I still think that if I shutdown my Laptop then unplugged the VGA connector, that would be better Lol

That's all I done and this process is working fine. I hope it also works fine for you :)

Normally I would do all that just for the fun of it and you're free to do it for the fun of it too Lol.

But just to help you think of reasons for using Dual Monitoring in situations other than gaming and video editing: this time the idea of Dual Monitoring came into my mind after I saw a tutorial in YouTube on Python programming. The text was small and I thought to myself that if I had one big screen (monitor) where I could download and watch the YouTube tutorial on one full screen, and a Python Shell and another Python windows both equally sharing half a screen, BUT on another monitor; that I can actually concentrate more on the tutorial and also at the same time not having to waste my time minimizing and maximising just to get a bit that I missed out from the tutorial

Have fun :)

---

