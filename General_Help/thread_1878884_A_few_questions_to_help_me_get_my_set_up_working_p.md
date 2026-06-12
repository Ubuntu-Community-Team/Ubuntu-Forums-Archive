---
title: "A few questions to help me get my set up working properly"
date: 2011-11-10
forum: General Help
---

### Post by TheothersideoftheForce on 2011-11-10
Hello forums,

I'll start by saying I am in no ways a pro, but I am familiar with how to tweak things through terminal. With that said I have been using Ubuntu off and on since 8.xx and have always like the freedom  Ubuntu give me, so i set out to build a pc from the ground up and finally finished it a few days ago.

My first question is, in my terminal window I do not have the usual user name i get something like this, willd@willd-MS-7933-"somethiing"-"something"-DMI-error-Stop:~$. Like I said I'm familiar with the terminal and that obviously does not look right to me, any idea what it is?

Second, I am using an ATI Radeon 5750HD with a dual monitor set up and I feel like its not running as smoothly as it should. the images tend to get choppy sometimes, and scrolling does not look fluid at all. i have the xinerama switched on and also have anti-tear on. not sure why the images look so choppy considering when the ati catalyst drivers were not installed i had no issues and also was able to get the big desktop set up nicely where as now i have two screens that i can crossover. any ideas? help? 

finally, i have been noticing that the internet takes a long time to load pages, I was using firefox but switched over to chrome and still having the same loading issues on certain websites. the whole desktop also seems to bog down when multi-tasking which is odd because I bought an AMD Phenom II x2 for the mutil-tasking. I realize there could be some drivers or settings i am over looking, i am just asking for an extra set of eyes to throw some ideas at me why i am encountering these issues.

I thank all and any who take a look and can offer any advice!
Thanks!
-Will

---

### Post by johanneslandin on 2011-11-10
1. What is your hostname?

[INDENT][/INDENT][FONT="Courier New"]gksu gedit /etc/hostname[/FONT]

---

### Post by Mark Phelps on 2011-11-10
I also have an ATI HD setup with dual screens, and find that the new display setup in 11.10 works find with dual screens.  Unless you really need something that xinerama provides, you should consider disabling it.  

I don't do 3D acceleration, but I find that I get much the same performance with the open source drivers in 11.10 that I did with the restricted drivers in previous Ubuntu versions.

But, you can install the restricted drivers if you want more options.  Just don't use the default ones, they don't work well.  Use the latest (11.10) ones downloaded from the AMD website.

---

### Post by TheothersideoftheForce on 2011-11-10
> **Mark Phelps said:**
> I also have an ATI HD setup with dual screens, and find that the new display setup in 11.10 works find with dual screens.  Unless you really need something that xinerama provides, you should consider disabling it.  

I don't do 3D acceleration, but I find that I get much the same performance with the open source drivers in 11.10 that I did with the restricted drivers in previous Ubuntu versions.

But, you can install the restricted drivers if you want more options.  Just don't use the default ones, they don't work well.  Use the latest (11.10) ones downloaded from the AMD website.

I originally tried dling and installing the catalyst drivers from the amd website, when it finished installing there was an error i cannot remember what it said. also i cannot get the dual monitors to work as a big desktop or the way it is now when xinerama is not activated all i get is a big desktop but screen two is just white and the mouse is an "X".
to the first poster i am not at my ubuntu computer currently, when i get home i will look that up and report back.
thanks for the help thus far!!

---

### Post by TheothersideoftheForce on 2011-11-11
just an update for the two posters, i did a fresh reinstall of ubuntu 11.10 and it is working out very well. issue #1 has been resolved, and issue #3 has also been resolved... #2 is still a work in progress but it seems to be ok for now
thank you everyone who helped out i appreciate all for looking!

---

