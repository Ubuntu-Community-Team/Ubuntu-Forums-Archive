---
title: "rythmbox song ratings"
date: 2006-02-07
forum: General Help
---

### Post by unclben on 2006-02-07
Does anybody know how rhythmbox weights the different ratings, in terms of how often it will (in shuffle mode) play songs based how highly they are rated?

I can't find the answer in the rhythmbox documentation, Google searching, or ubuntuforums searching...

---

### Post by Sutekh on 2006-02-07
For a while Rhythmbox used to rate songs higher the more I chose to play them.   Opposite to iTunes which played songs more if they rated more.

I think that was Rhythmbox 0.9.1. Rhythmbox 0.9.2 doesn't seem to want to do this anymore.

---

### Post by earobinson on 2006-02-07
if you run gconf-editor you can see that rhythmbox has 3 difernt shuffle modes and they are quickly decribed, you would have to check out the source or maybe doc for more info

---

### Post by doclivingston on 2006-02-08
[QUOTE=unclben]Does anybody know how rhythmbox weights the different ratings, in terms of how often it will (in shuffle mode) play songs based how highly they are rated?[/QUOTE]

It depends exactly what play order you are using:

If you have Shuffle turned on and Repeat turned of, then it is using the "shuffle" play order. This puts the tracks into a random order, and then plays though them - so they have equal weight, and it will never repeat a track until they have all been played.

If you have Shuffle and Repeat both turned on, then it will use the "random-by-age-and-rating" play order. This pick the next song at random when one finishes, with the weight (rating * (1 + log (seconds since last play)), treat an unrated song as 2.5. This can cause the same song to get played twice in a row, particularly if you are playing from a small number of tracks.


Rhythmbox actually has several other play orders that you can't currently get to from the user interface (you can set them with gconf-editor if you really want them): "random-by-rating", "random-by-age" and "random" (equal weights).

---

### Post by RAOF on 2006-02-08
[QUOTE=doclivingston]...
If you have Shuffle and Repeat both turned on, then it will use the "random-by-age-and-rating" play order. This pick the next song at random when one finishes, with the weight (rating * (1 + log (seconds since last play)), treat an unrated song as 2.5. This can cause the same song to get played twice in a row, particularly if you are playing from a small number of tracks.
...[/QUOTE]
Woah.  What sort of user-interface crack was the person who came up with that smoking?  Are there any other crazy tricks like that hidden in the (otherwise very good) rhythmbox ui?

---

### Post by doclivingston on 2006-02-08
[QUOTE=Sutekh]For a while Rhythmbox used to rate songs higher the more I chose to play them.   Opposite to iTunes which played songs more if they rated more.

I think that was Rhythmbox 0.9.1. Rhythmbox 0.9.2 doesn't seem to want to do this anymore.[/QUOTE]

Yes, RB used to do "auto-rating" when tracks you played would increase their rating slowly. However if you were using a play order which was based on rating (i.e. Shuffle and Repeat both on), this would lead to a nasty positive-feedback cycle.

Auto-rating got removed (in 0.9.1 iirc), since it had quite a few problems.

---

### Post by Sutekh on 2006-02-08
[QUOTE=RAOF]Woah.  What sort of user-interface crack was the person who came up with that smoking?  Are there any other crazy tricks like that hidden in the (otherwise very good) rhythmbox ui?[/QUOTE]
Actually after some thinking about it using a logarithmic scale isn't so insane.  Not wanting to go technical but log scales are good for 'squishing' axes. 

If you have a lot of files its quite possible that some may have been played within a couple of minutes ago up to a couple of weeks ago.

A couple of minutes ~= 300 seconds,   log(300)=2.477
A couple of weeks ~= 1209600 seconds, log(1209600)=6.082
(Assuming base 10 log)

Otherwise the weightings could get seriously out of hand.

---

### Post by doclivingston on 2006-02-08
[QUOTE=RAOF]Woah.  What sort of user-interface crack was the person who came up with that smoking?  Are there any other crazy tricks like that hidden in the (otherwise very good) rhythmbox ui?[/QUOTE]

Yes, it is complete crack. However I'm not sure what else they could do, if they were putting Shuffle and Repeat buttons in - as basically every other player had. What is the difference between Shuffle and Shuffle+Repeat in other players?

Hopefully this will be replaces by a menu sometime soon (for 0.9.4), so you can get to all the other play orders RB has, and the ones people have planned (repeat one, album-shuffle etc).

---

### Post by doclivingston on 2006-02-08
[QUOTE=Sutekh]Actually after some thinking about it using a logarithmic scale isn't so insane.  Not wanting to go technical but log scales are good for 'squishing' axes. 

If you have a lot of files its quite possible that some may have been played within a couple of minutes ago up to a couple of weeks ago.

A couple of minutes ~= 300 seconds,   log(300)=2.477
A couple of weeks ~= 1209600 seconds, log(1209600)=6.082
(Assuming base 10 log)

Otherwise the weightings could get seriously out of hand.[/QUOTE]

That's why it works that way: if you have several tracks that were last played at about the same time (and it wasn't really recently), then the probability is basically proportional to their rating.

Oh, and it's actually (rating * log (1 + time since last play))

---

### Post by RAOF on 2006-02-08
[QUOTE=doclivingston]Yes, it is complete crack. However I'm not sure what else they could do, if they were putting Shuffle and Repeat buttons in - as basically every other player had. What is the difference between Shuffle and Shuffle+Repeat in other players?

Hopefully this will be replaces by a menu sometime soon (for 0.9.4), so you can get to all the other play orders RB has, and the ones people have planned (repeat one, album-shuffle etc).[/QUOTE]
Well, there could be a preference for what type of shuffle the "shuffle button" does, shuffle could be a submenu, or it could be just completely hidden in a gconf setting.  I'm not sure what shuffle+repeat should be - for this reason I think they should probably be mutually exclusive.

But good to hear that it'll be replaced by something sane soon :)

---

### Post by Sutekh on 2006-02-08
[QUOTE=doclivingston]That's why it works that way: if you have several tracks that were last played at about the same time (and it wasn't really recently), then the probability is basically proportional to their rating.

Oh, and it's actually (rating * log (1 + time since last play))[/QUOTE]
Yeah actually that makes more sense than (1 + log(time since last played)).  
log(0) isn't a happy chappy.  How did you find this out?

[QUOTE=RAOF]Well, there could be a preference for what type of shuffle the "shuffle button" does, shuffle could be a submenu, or it could be just completely hidden in a gconf setting. I'm not sure what shuffle+repeat should be - for this reason I think they should probably be mutually exclusive.

But good to hear that it'll be replaced by something sane soon [/QUOTE]
I like the idea of a shuffle menu, I looked high and low for the gconf key and it was right in front of me.  

Perhaps Shuffle+Repeat should mean Shuffle+Repeat All??

---

### Post by doclivingston on 2006-02-08
> **Sutekh]Yeah actually that makes more sense than (1 + log(time since last played)).  
log(0) isn't a happy chappy.  How did you find this out?[/quote]

I'm Rhythmbox's current maintainer. So I've seen the source code a few times  said:**
> I like the idea of a shuffle menu, I looked high and low for the gconf key and it was right in front of me.  

Perhaps Shuffle+Repeat should mean Shuffle+Repeat All??

I'm not sure what you mean by "Shuffle+Repeat All".

0.9.3 has the shuffle and repeat buttons moved up to the toolbar, and  basically it will get replaced by a drop-down menu.

---

### Post by Sutekh on 2006-02-08
> **doclivingston]I'm Rhythmbox's current maintainer. So I've seen the source code a few times  said:**
> OK well that makes sense! :) 

[QUOTE=doclivingston]
I'm not sure what you mean by "Shuffle+Repeat All".

0.9.3 has the shuffle and repeat buttons moved up to the toolbar, and  basically it will get replaced by a drop-down menu.Yeah I wasn't sure myself.  I originally thought it would shuffle play until all songs were played once (assuming they had equal weightings).  Then repeat the shuffle process, but not neccessarily the order.  I *think* that's how iTunes does it.  I guess if it was shuffling with the 'time since last played' method, the second shuffle would probably be much like the first.

---

### Post by doclivingston on 2006-02-08
[QUOTE=Sutekh]Yeah I wasn't sure myself.  I originally thought it would shuffle play until all songs were played once (assuming they had equal weightings).  Then repeat the shuffle process, but not neccessarily the order.  I *think* that's how iTunes does it.[/quote]

That's what the "shuffle" play order (Shuffle on, Repeat off) does. Although in versions earlier than 0.9.3 it stops once finished rather than reshuffling and continuing

>  I guess if it was shuffling with the 'time since last played' method, the second shuffle would probably be much like the first.

What you get with Shuffle and Repeat on ("random-by-age-and-rating") doesn't shuffle the tracks, it picks the new song randomly based on the weightings after each song finished.

---

### Post by Sutekh on 2006-02-09
[QUOTE=doclivingston]That's what the "shuffle" play order (Shuffle on, Repeat off) does. Although in versions earlier than 0.9.3 it stops once finished rather than reshuffling and continuing[/QUOTE]Oh I see.  But this is changed with Rhythmbox 0.9.3?

[QUOTE=doclivingston]
What you get with Shuffle and Repeat on ("random-by-age-and-rating") doesn't shuffle the tracks, it picks the new song randomly based on the weightings after each song finished.[/QUOTE]I don't understand this bit, it doesn't shuffle but picks the new song randomly?  We must have differing definitions of shuffle?!



Also (now I know that your the RB maintainer!), I was trying to compile 0.9.3, and I don't understand this error at the end of ./configure
```
checking for RHYTHMBOX... configure: error: Package requirements ( gtk+-2.0 >= 2.5.4   libgnomeui-2.0  libglade-2.0  gnome-vfs-2.0 >= 2.7.4     gnome-vfs-module-2.0) were not met:

Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
I feel I should be able to work this one out, but I'm stumped.  #-o 

Perhaps I should ask this on the RB mailing list?

Poor unclben, I've completely hijacked his thread.  Sorry :-#

---

### Post by doclivingston on 2006-02-09
> **Sutekh]Oh I see.  But this is changed with Rhythmbox 0.9.3?

I don't understand this bit, it doesn't shuffle but picks the new song randomly?  We must have differing definitions of shuffle?![/quote]

Say you have 5 songs, A, B, C, D and E.

What shuffle does is choose a random order (say C, E, B, D, A) and play them **all** in that order. Versions earlier than 0.9.3 would then stop said:**
> checking for RHYTHMBOX... configure: error: Package requirements ( gtk+-2.0 >= 2.5.4   libgnomeui-2.0  libglade-2.0  gnome-vfs-2.0 >= 2.7.4     gnome-vfs-module-2.0) were not met:

Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

You need to install the libgnomeui development stuff, which is in the package "libgnomeui-dev". You can search for which package you need by entering "libgnomeui-2.0.pc" into the search-in-packages thing on packages.ubuntu.com

---

### Post by unclben on 2006-02-09
[QUOTE=doclivingston]It depends exactly what play order you are using:

If you have Shuffle turned on and Repeat turned of, then it is using the "shuffle" play order. This puts the tracks into a random order, and then plays though them - so they have equal weight, and it will never repeat a track until they have all been played.

If you have Shuffle and Repeat both turned on, then it will use the "random-by-age-and-rating" play order. This pick the next song at random when one finishes, with the weight (rating * (1 + log (seconds since last play)), treat an unrated song as 2.5. This can cause the same song to get played twice in a row, particularly if you are playing from a small number of tracks.


Rhythmbox actually has several other play orders that you can't currently get to from the user interface (you can set them with gconf-editor if you really want them): "random-by-rating", "random-by-age" and "random" (equal weights).[/QUOTE] Thank you for the excellent reply. That is exactly what I wanted to know.

---

### Post by Sutekh on 2006-02-10
> **doclivingston]Say you have 5 songs, A, B, C, D and E.

What shuffle does is choose a random order (say C, E, B, D, A) and play them **all** in that order. Versions earlier than 0.9.3 would then stop said:**
> 
Ok I see.  After thinking about it for a while I ended up with the same thing.  Thanks for explaining that.

[QUOTE=doclivingston]
You need to install the libgnomeui development stuff, which is in the package "libgnomeui-dev". You can search for which package you need by entering "libgnomeui-2.0.pc" into the search-in-packages thing on packages.ubuntu.com
Ah, I didn't realise that it was asking for the development packages.  I got them but now I get a different error
```
checking for TOTEM_PLPARSER... configure: error: totem playlist 
parsing library not found or too old

```
I looked up 'totem' in Synaptic and found **libtotem-plparser-dev** but it depends on **libtotem-plparser0-1.2.0-0ubuntu3** to be installed, however I have **1.2.1-0ubuntu1~breezy1** installed.  The older version -1.2.0- is available from the Ubuntu Packages web site, how can I install the older version?  Remove the newer one then install the older one?   Or is there another way?

---

