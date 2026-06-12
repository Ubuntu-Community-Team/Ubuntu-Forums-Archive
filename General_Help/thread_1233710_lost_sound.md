---
title: "lost sound"
date: 2009-08-07
forum: General Help
---

### Post by Kiriefotia on 2009-08-07
I was playing music with no poblem yesterday, now I have no sound
Found, that I have no sound when attempting to watch a youtube video.
So I played music and got "Unknown playback error"
All I have done which may have caused problems (im a linux newb) is

installed flash player to watch youtube videos and
uninstalled adobe flash plugin (i think it was called) for 2 reasons
for the one I just installed it said this old on needed to be removed and 2
It was listed under broken packages in synaptic

---

### Post by burmanabhay88 on 2009-08-07
there might still be broken packages.
to check. Goto System > Synaptic Package Manager. Right Hand Side click on broken dependencies. Fix them.
After that install some sound player, if it got removed in the process. I'd advice VLC.
Tell me if this works.

---

### Post by Kiriefotia on 2009-08-07
In Synaptic package Manger there is nothing on the right hand side?? You have to right click on a specific package and go to the dependencies tab. So, for now I still have no sound

Running Ubuntu 9.04

---

### Post by burmanabhay88 on 2009-08-07
my mistake. LEFT hand side. "Broken"

---

### Post by Kiriefotia on 2009-08-07
Well, there is nothing under the 'broken' tab

Is there a way to see the history, and see what was removed to reinstall it?

---

### Post by burmanabhay88 on 2009-08-07
none that I know of, but i'm not a pro. What does the Missing Recommends say????

---

### Post by TenPlus1 on 2009-08-07
Here's the latest version of Flash Player 10 for Ubuntu: 

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

Also, Movie Player has a pugin available that allows you to search and play YouTube videos without the need for flash :)

---

### Post by Kiriefotia on 2009-08-07
> **burmanabhay88 said:**
> none that I know of, but i'm not a pro. What does the Missing Recommends say????

Nothing

---

### Post by oomar on 2009-08-07
just covering all the bases here but go to System -> Preferences -> Sound and hit all the test buttons and see which ones work and which ones dont.

 oh and dont forget to check if its muted. lol sounds dumb but TRUST ME it can really be a problem. for a few months if you are really stubborn.... lol ;) 

to check if anything is muted go to terminal and type

```
alsamixer
```

click tab till the thing shows you on the tab saying ALL (right next to playback and capture)

now just scroll through them all using the arrow keys and anything with an "MM" or with a value of zero is muted. click M if it has "MM" and if its value is zero, simply raise it with the arrow keys.

---

### Post by Kiriefotia on 2009-08-07
none of the sound tests work, and nothing is muted

---

### Post by oomar on 2009-08-07
have you tried changing the settings for playback? mine is on auto detect but yours might not be fairing as well. just try each out and give it a test.

---

### Post by Kiriefotia on 2009-08-07
Did that too..

It would not be a setting if i was getting an error message would it?

---

### Post by oomar on 2009-08-07
? what? Im not sure i understand you...

---

### Post by Kiriefotia on 2009-08-07
I mean, if a setting was wrong, or it was muted. I would not recieve an error message when trying to play music. In my first post, when I try to play a song I get "Unknown playback error"

---

### Post by Kiriefotia on 2009-08-07
Amazing.

Some unnamed douchbag was dickin around near my computer and unplugged my speakers. They then plugged it back into the subwoofer slot.. Problem solved. Wow.

---

### Post by burmanabhay88 on 2009-08-07
> **Kiriefotia said:**
> Amazing.

Some unnamed douchbag was dickin around near my computer and unplugged my speakers. They then plugged it back into the subwoofer slot.. Problem solved. Wow.

ha ha. happens. in Xp, that would be the first thing I would have checked, but I guess with Ubuntu....:D

---

