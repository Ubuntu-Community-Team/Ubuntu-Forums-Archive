---
title: "video playback problems in firefox"
date: 2006-04-15
forum: General Help
---

### Post by klytu on 2006-04-15
I can't seem to play any type of embedded video in Firefox anymore. 

Example: if I try to play a video through BBC News Player, MPlayer plug-in begins buffering the video and then stops without playing anything. Same behaviour appears when attempting to playback any type of embedded video in Firefox. The behaviour doesn't appear to be type or site specific. 
This didn't always happen. I first noticed the behaviour after I removed totem-xine and replaced it with totem-gstreamer. (I did this because totem-xine wouldn't playback video smoothly from a shared networked drive, but totem-gstreamer would.) I really don't know whether this had anything to do with the situation, but this is when I noticed it. I noticed that when I would try to play back a Flash video in Firefox from this or that web site, the video would start to buffer and the stop without playing. Thinking this was a problem with Flash, I tried removing and reinstalling Flash, but the behaviour continued. Later I noticed the behaviour didn't just happen with Flash video but with all types of embedded video I tried.

I tried installing and using Automatix (I had noted several posts indicating this cured a number of video playback woes). I had Automatix update Firefox 1.0.7 to Firefox 1.5.0.1 with all plugins. The updated Firefox still showed the same behaviour, only now with the MPlayer plugin rather than whatever else was playing back video prior to the update. At this point, I remembered that the BBC News Player used to playback with no problems using RealPlayer but I couldn't figure out any easy way to get Firefox to associate most video playback with anything other than MPlayer. I then tried removing the MPlayer plugins and reinstalling Firefox 1.0.7. This got RealPlayer associated with BBC News Player again, but the same behaviour occurred with RealPlayer (buffer would appear to begin loading, but would then stop without playing anything). 
At the moment I am back to the point where I was after I first tried Automatix with one difference. (Firefox 1.5.0.1 with all plugins, MPlayer plugin tries to play just about all embedded video but stops without playing after buffering. The difference is I have removed totem-xine and reinstalled totem-gstreamer.) I found multiple threads and posts from others who had this problem, but all the ones I read through ended without the original poster indicating whether or not the problem was solved. At this point I don't appear to have any problems playing back video outside of Firefox. For example, I can playback DVDs, WMVs, SVCDs either from local or networked harddrives or from DVD drive with no problem. I just hope I haven't mucked things up beyond repair now. 

The above is not an exhaustive list of everything I tried since noticing the behaviour, but I think that's most of it. Any suggestions or comments appreciated!

---

### Post by PhoenixP3K on 2006-04-15
Well, embed videos as always been a huge problem, but in my case it's mostly because the websites update their streaming programs to be Windows Media Player compatible. 
I don't think it's a Firefox problem. Or perhaps it's an Mplayer problem...

Try using this procedure: 
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox)

The most important part might be to change the default video driver the plugin uses. This might be your problem. The link above indicates how to configure the plugin

---

### Post by klytu on 2006-04-15
[QUOTE=PhoenixP3K]Well, embed videos as always been a huge problem, but in my case it's mostly because the websites update their streaming programs to be Windows Media Player compatible. 
I don't think it's a Firefox problem. Or perhaps it's an Mplayer problem...

Try using this procedure: 
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox)

The most important part might be to change the default video driver the plugin uses. This might be your problem. The link above indicates how to configure the plugin[/QUOTE]

Thanks for the suggestion. I tried it but unfortunately no change. I didn't think this was an MPlayer problem because at one point today I noticed the same behaviour with RealPlayer when I tried to play back a video with BBC News Player. 

What's really frustrating is that I don't know exactly when this behaviour started happening. So it's difficult to figure out where to start looking. I know I have played back embedded video flawlessly with BBC News Player and RealPlayer before, so I tried to at least get to that point again but no luck.

---

### Post by klytu on 2006-04-29
The MediaPlayerConnectivity extension to Firefox helped quite a bit. I downloaded it from here:

[http://membres.lycos.fr/sethnakht/](http://membres.lycos.fr/sethnakht/)

I didn't find the use straightforward, but I was able to get a lot of embedded RealMedia, QuickTime, and WindowsMedia playback working reasonably well by using it. I configured RealMedia to playback with RealPlayer instead of MPlayer, selected "Show a direct URL link icon", and left other settings at defaults. I found I could play some of the most intractable embedded streams by clicking on the URL that the MediaPlayerConnectivity extension generated if playback didn't occur automatically.

Most macromedia flash playback was restored using Automatix, but there are still quite a few web sites with flash video that don't seem to play properly.

I still have no clue as to why the trouble ever came up and I never had to go through contortions like this before to playback embedded media in Firefox.

---

### Post by acmarfil31 on 2007-03-27
Hi, you can also use a firefox plugin to play embedded video.  You just need to specify which video player you have in your linux box (VLC, mplayer, etc., VLC works great for me).

Here's the link, [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by whiskybar on 2007-03-30
I don't know how old this thread actually is, but I have had exactly the same problem. It seems I have found a solution. In short, use x11 for video output in mplayer.

Try [http://www.eurosport.com/mclivevideo.shtml](http://www.eurosport.com/mclivevideo.shtml) for example. The embedded player appears, gets redirected several times, buffers the video and then says "Stopped". Okay. Here's what you do: right click the blank frame and go to Configure. Select Video Output: x11. Play the clip again and it should work.

I don't know if it matters but just in case: Firefox 2.0.0.3, mozilla-mplayer 3.31, mplayer from medibuntu, w32codecs from medibuntu.

HTH,
Jiri

---

### Post by ubu-for on 2007-04-01
> **whiskybar said:**
> It seems I have found a solution. In short, use x11 for video output in mplayer.

Try [http://www.eurosport.com/mclivevideo.shtml](http://www.eurosport.com/mclivevideo.shtml) for example. The embedded player appears, gets redirected several times, buffers the video and then says "Stopped". Okay. Here's what you do: right click the blank frame and go to Configure. Select Video Output: x11. Play the clip again and it should work.

Works great!

Thank you very much!

---

### Post by H.E. Pennypacker on 2007-04-14
> **whiskybar said:**
> Try [http://www.eurosport.com/mclivevideo.shtml](http://www.eurosport.com/mclivevideo.shtml) for example. The embedded player appears, gets redirected several times, buffers the video and then says "Stopped". Okay. Here's what you do: right click the blank frame and go to Configure. Select Video Output: x11. Play the clip again and it should work.

Jiri

That worked for me!

---

### Post by salviati on 2007-06-06
This worked for me too.  Thanks!

---

### Post by geezerone on 2007-06-06
Didn't for me :(

---

