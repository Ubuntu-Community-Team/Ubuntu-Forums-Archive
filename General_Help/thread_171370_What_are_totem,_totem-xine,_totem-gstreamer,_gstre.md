---
title: "What are totem, totem-xine, totem-gstreamer, gstreamer, totem, and all that?"
date: 2006-05-06
forum: General Help
---

### Post by harisund on 2006-05-06
I am *really really* confused by the RestrictedFormats and FirefoxPlugins wiki pages.

Here is another observation I made. If I installed gstreamer it told me I will have to remove xine, if I installed xine, it said I would have to remove gstreamer. What sort of a pain is that? 

Is xine really better? In what way? 

If xine is better, why are there so many gstreamer* packages (gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg gstreamer0.8-mad). What is the point in installing them if I am going to install xine and remove gstreamer in the first place? The RestrictedFormats page doesn't talk about this at all. Do I need to install those packages, and still install xine and throw gstreamer? 

Ok, so I do install w32 codecs as mentioned. Do I assume xine/gstreamer/totem/totem-xine/totem-gstreamer automatically sees the w32codecs? Or do I have to, in some configuration file, clearly mention that? 

Also, I see a "totem-gstreamer-firefox-plugin" in the RestrictedFormats page. Do I assume there is a "totem-xine-firefox-plugin" in the repos? Which should I install? Does installing one automatically delete the other? 

Finally, there are a million installation instructions for RealPlayer. I understand choice is the cornerstone of Open Source, but when the user doesn't know what to do/ what works best, giving him so many options is really bad. What is the 'best' method? What should I follow exactly? (Take for example Java. There is a nice method for installing Java on the RestrictedFormats page and it works perfectly too. Why can't there be one like that for RealPlayer)

Please, I really need help in this aspect. This is the *only* thing that annoys me on Breezy, everything else has really been a 'breeze' !

---

### Post by pitkali on 2006-05-06
[QUOTE=harisund]Here is another observation I made. If I installed gstreamer it told me I will have to remove xine, if I installed xine, it said I would have to remove gstreamer. What sort of a pain is that? [/quote]
That **would** be mutually exclusive packages. Like totem-gstreamer and totem-xine. But totem-gstreamer is NOT gstreamer. It is version of a player that uses gstreamer to decode your video. Totem-xine is NOT xine. It is a version of totem, that will use libxine do decode your video. You can simply have one version of this same player at a time.

> Is xine really better? In what way? 
On my system gstreamer version is simply unable to smoothly decode most videos.

> If xine is better, why are there so many gstreamer* packages (gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg gstreamer0.8-mad). What is the point in installing them if I am going to install xine and remove gstreamer in the first place?
If using Gnome you don't actually want to uninstal gstreamer (again - not the same as totem-gstreamer, which I can't honestly recommend). You can have both libxine and gstreamer libraries with all the plugins (like the packages you mention in parens). Some gnome apps use them currently to encode and decode multimedia, e.g. rhythmbox and Sound Juicer AFAIR.

> Ok, so I do install w32 codecs as mentioned. Do I assume xine/gstreamer/totem/totem-xine/totem-gstreamer automatically sees the w32codecs? Or do I have to, in some configuration file, clearly mention that? 
They will be recognised automatically. Note: totem-gstreamer does not use them AFAIK.

> Also, I see a "totem-gstreamer-firefox-plugin" in the RestrictedFormats page. Do I assume there is a "totem-xine-firefox-plugin" in the repos? Which should I install? Does installing one automatically delete the other? 
Yes, I recomend the xine version. The other one will be automatically deleted.

Regards,

---

### Post by harisund on 2006-05-06
Yay! You are awesome !

Thanks.. 

The first barrier in my understanding was that totem was merely a 'front-end' to both the gstreamer and xine libraries. Once I got that cleared out (thanks to you again!)  everything else sort of started falling in place. 

I knew it ! Never once has a question of mine gone unanswered in these forums. Absolutely stunning I must say. 

Thanks again !

---

