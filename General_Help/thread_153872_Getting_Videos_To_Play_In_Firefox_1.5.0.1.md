---
title: "Getting Videos To Play In Firefox 1.5.0.1"
date: 2006-04-01
forum: General Help
---

### Post by gurjit on 2006-04-01
I've gone through so may HowTo's related to this subject but none of them seem to work? If i want to be able to play lets say this movie.  {Its the X-Box 360's Unseen Commercial}

[http://media.putfile.com/Unseen-Xbox-360-Commercial]("http://media.putfile.com/Unseen-Xbox-360-Commercial")

Those of u who have got movies to play in Firfox will have one hell-of-a-laugh those of u who haven't; myself, will not be enjoing it so much :( .

I just want to know what is it EXACTLY that i need to see this video. Of course this is just an example, I want to be able to see as many video types as possibe in Firefox, but this is a good start.

Thanks Alot In Advance
Gurjit Bains

---

### Post by halitech on 2006-04-01
this seems like the best tutorial to follow to get things working. I think I did the Automatrix route when I reinstalled and everything has been working fine for me

[http://http://ubuntuforums.org/showthread.php?t=135364&highlight=firefox+movies+mplayer+plugin]("http://http://ubuntuforums.org/showthread.php?t=135364&highlight=firefox+movies+mplayer+plugin")

---

### Post by gurjit on 2006-04-01
That link goes to [http://www.microsoft.com/](http://www.microsoft.com/) ?

---

### Post by brandon moore on 2006-04-01
the link for the video works for me, but i can't see the video either.  the link for the tutorial takes me straight to microsoft.com

---

### Post by gurjit on 2006-04-01
[http://ubuntuforums.org/showthread.php?t=135364&highlight=firefox+movies+mplayer+plugin](http://ubuntuforums.org/showthread.php?t=135364&highlight=firefox+movies+mplayer+plugin)

Go To the link; I got EVERTHING to work now in Mozilla. DO EXACTLY AS THAT GUYS SAYS AND U"LL GET IT TO WORK. But the most important thing said is this: ( DO NOT FORGET THIS STEP)


I just upgraded to firefox-1.5.0.1 myself and ran into the same problem with plugins not working properly when installed from synaptic. So after a bit of tinkering I came up with this fix.
[B][I][COLOR="Red"]
First delete the plugins folder from /home/YOUR-PROFILE/.mozilla/
WARNING: if you have installed any plugins through firefox your will need to reinstall them from synaptic.
then make a link to the plugins folder at /usr/lib/mozilla/
finally move the link to /home/YOUR-PROFILE/.mozilla/
and name it plugins.
In a firefox window go to "about: plugins" and everything should be listed [/COLOR][/I][/B]
BY CHAOSCHANNEL


Trust me go there and if u do exactly what is said then u'll get it to work.
I Just Wanna Say A Big Thanks To dvarsam and chaoschannel i love u guys :p lol

---

