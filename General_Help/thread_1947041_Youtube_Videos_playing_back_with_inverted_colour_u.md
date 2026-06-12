---
title: "Youtube Videos playing back with inverted colour under firefox!"
date: 2012-03-26
forum: General Help
---

### Post by vinpor on 2012-03-26
Hi please help me.

My youtube videos are now all playing back with inverted colours in firefox. People's skins are blue!

Under chromium the vids playback fine. And the strange thing is under firefox whenever i play a youtube vid with an ad before the main vid the colours in the ad are normal but when the main vid starts the colours are all inverted.

I have tried reinstalling flash player, i have tried reverting to an older version of flash, i have tried reinstalling firefox, i have even tried deleting the firefox folder from my home folder to restore settings.

Nothing seems to fix it.

Has anyone had this problem before? please help!

I am running ubuntu 11.10 x64 & firefox 11

---

### Post by K-Jtan on 2012-03-28
Sorry probably not what you want to hear ...

I started experiencing this same problem for the last 2 hours (I just pass from Flash 11.1 to 11.2).
I am running ubuntu 11.10 32bits & firefox 11.0 (current release version).

If I found a solution I'll let you know

---

### Post by K-Jtan on 2012-03-28
Oh I forgot about that, YouTube is trying to convert it's site using HTML5 (instead of flash).

I tested out and it works fine. No more smurfs ;)

So to activate the HTML5 on YouTube just go to this address : [https://www.youtube.com/html5](https://www.youtube.com/html5)
Then at the bottom look for the "Join the HTML5 Trial" link. Click it and enjoy. You will now be using HTML5 for listening to your videos.

Note: the you can still use the http protocol instead of the https protocol. https will secure the connection between you and YouTube.

---

### Post by Le@ndro on 2012-03-28
Awesome!!! Thanks a lot and GOOD BYE Flash (and smurfs)!

EDIT: Sadly most of youtube has ads, and ads are still not compatible with the HTML5 player :(

---

### Post by xyzzyman on 2012-03-29
Known issue, happening with me also: [https://bugbase.adobe.com/index.cfm?event=bug&id=3109467](https://bugbase.adobe.com/index.cfm?event=bug&id=3109467)

Best off rolling back to 11.1 for now: 
64bit [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260791](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260791)

32bit [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260792](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.63-0oneiric1/+build/3260792)

---

### Post by pickarooney on 2012-03-30
This is happening me with videos viewed directly on Youtube but not in embedded YT videos from other sites. I tried activating the HTML5 test and it worked for one video but then everything went back to smurf mode. My firefox plugin is 11.1 r102 (the problem also occurs in Chromium) 

I'm looking for a working 32-bit package for Maverick if anyone can link me up.

---

### Post by vinpor on 2012-03-31
I tried the HTML5 thing also and also worked for one of my vids anad the others are back to normal.

if anyone finds a solution please let us know.

also now my vids have started playing in inverted colours in chromium. when previously it was only under firefox

---

### Post by vinpor on 2012-03-31
just to let you guys know that i just rolled back my flash-plugin from 11.2 to 11.1

it fixed inverted colour issue under chrome but firefox is still the same.

---

### Post by Trackieman on 2012-03-31
Right click on the video you are watching, click settings. On the Display tab, untick Enable hardware acceleration.
This worked for me running Ubuntu 10.04, Firefox 11, Flash 11.2.202.228
Hopefully Adobe will fix it soon.

---

### Post by r-senior on 2012-03-31
Disabling the hardware acceleration worked for me (but I did need to refresh the page after doing so).

---

### Post by sdowney717 on 2012-03-31
you must full screen the video to make changes to flash preferences.
and might need to click several itmes

---

### Post by anto27373 on 2012-04-01
> **sdowney717 said:**
> you must full screen the video to make changes to flash preferences.
and might need to click several itmes

thx , worked for me

---

### Post by Le@ndro on 2012-04-02
> **anto27373 said:**
> [QUOTE=sdowney717;11808025]you must full screen the video to make changes to flash preferences.
and might need to click several itmesthx , worked for me[/QUOTE]

Same here, THANKS!

---

### Post by troudobus on 2012-04-06
> **Trackieman said:**
> Right click on the video you are watching, click settings. On the Display tab, untick Enable hardware acceleration.
This worked for me running Ubuntu 10.04, Firefox 11, Flash 11.2.202.228
Hopefully Adobe will fix it soon.
thx

---

### Post by SvenBuntu on 2012-04-19
The proposed solution fixed the issue but is absolutely crap that it has to be made! This should not happen to a stable release. Is it flash or nvidia causing this?

---

### Post by HiImTye on 2012-04-20
its a known issue with Adobe but they have no plans of fixing it as flash is now abandonware to them so for now until other flash players catch up, disabling hardware acceleration is the only option (aside from switching to players that are farther behind)

---

### Post by cmcginty on 2012-05-11
> **sdowney717 said:**
> you must full screen the video to make changes to flash preferences.
and might need to click several itmes

 
yes, the setting can ONLY BE CHANGED IN FULL SCREEN MODE. Thanks for the tip.

---

### Post by nkv1 on 2012-05-23
> **K-Jtan said:**
> Oh I forgot about that, YouTube is trying to convert it's site using HTML5 (instead of flash).

I tested out and it works fine. No more smurfs ;)

So to activate the HTML5 on YouTube just go to this address : [https://www.youtube.com/html5](https://www.youtube.com/html5)
Then at the bottom look for the "Join the HTML5 Trial" link. Click it and enjoy. You will now be using HTML5 for listening to your videos.

Note: the you can still use the http protocol instead of the https protocol. https will secure the connection between you and YouTube.

this worked for me too, since inverted colors are on chrome too

---

### Post by JeremiahVI on 2012-06-19
> **Trackieman said:**
> Right click on the video you are watching, click settings. On the Display tab, untick Enable hardware acceleration.
This worked for me running Ubuntu 10.04, Firefox 11, Flash 11.2.202.228
Hopefully Adobe will fix it soon.


this solution worked for me, thanks !

---

### Post by mjabirk on 2012-07-04
> **Trackieman said:**
> Right click on the video you are watching, click settings. On the Display tab, untick Enable hardware acceleration.
This worked for me running Ubuntu 10.04, Firefox 11, Flash 11.2.202.228
Hopefully Adobe will fix it soon.

Thanks. This fixed my issue.:popcorn:

---

### Post by cyb3rkn19ht on 2012-09-18
Disabling hardware acceleration worked for me as well.
Thanks!

---

### Post by Notasoddingclue on 2012-10-11
I too had this problem and was thinking of rolling back Ubuntu to use 10 instead of 12.  I asked on another forum about this problem and one member provided me with a link to this thread.  It worked.  Not only less Smurfs seen but I can see green grass and not something out of a bad Sci Fi movie.

I think someone somewhere is owed more than a beer.:KS

I wonder if this was the problem I encountered yesterday when Ubuntu crashed my PC a few times yesterday and this morning?  

For now, top banana to the person who figured it out.

---

### Post by tjwilli on 2012-10-20
Thanks for the fullscreen tip. I couldn't unclick hardware acceleration otherwise. 
Works fine now. (Now will this stop the crashing when in Yahoo mail while Shockwave is enabled also? - We'll see.)

---

### Post by tjwilli on 2012-10-20
> **tjwilli said:**
> Thanks for the fullscreen tip. I couldn't unclick hardware acceleration otherwise. 
Works fine now. (Now will this stop the crashing when in Yahoo mail while Shockwave is enabled also? - We'll see.)

Yahoo still crashes when shockwave is enabled.

---

### Post by pqwoerituytrueiwoq on 2012-10-20
The blue people bug is worked around with nvidia 310.14 (xorg edgers ppa)

---

