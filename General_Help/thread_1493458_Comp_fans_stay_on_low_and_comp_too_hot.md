---
title: "Comp fans stay on low and comp too hot"
date: 2010-05-25
forum: General Help
---

### Post by MasterShihoChief on 2010-05-25
I have noticed a really bad problem on here that i never had on windows 7 even with overclocking. 

It seems the fans stay on and are basically idling or are at minimum speed and the computer and graphics cores are just idling at 99c which is really dangerous, but not critical yet since this is an alienware laptop and the technician did say its temperature rating is above that. 

The problem is I need to get the multiple fans in the case to start up and cranking like they do to keep the system really cool in windows 7. Any ideas guys, I kinda wanna get this fixed ASAP as i dont want to constantly be running at this temperature.

cheers,
Mastershihochief

---

### Post by MasterShihoChief on 2010-05-26
bump before my comp melts >_<

---

### Post by MasterShihoChief on 2010-05-27
bump for great justice

---

### Post by MasterShihoChief on 2010-05-28
bump

---

### Post by MasterShihoChief on 2010-05-28
bump plz

---

### Post by PGScooter on 2010-05-28
That sounds frustrating. I wish I could help :(.

At least I can bump for ya!

---

### Post by vandorjw on 2010-05-28
Hey there,
I do not have an alien ware laptop, so i don't know what is out there for it or why it would even do this.

First thing I would do is try and rule out a bad install.
Grab a Live-CD of the latest version of ubuntu and just start launching videos, launch gimp and make it render some stuff,just to get your CPU cranked up.

If the fans turn on as they should, something went wrong during the install.
If they do not, we have a problem.

--------------------------------------
2nd~~> How do you know your temperature is at 99Celcius? what temperature monitor did you install? Are you 100% certain its accurate? To check this, run it, then restart...but instead of going into Windows or Ubuntu, go into your BIOS. 
if the temperature is in 90 Celcius range, I guess its accurate.

-----------------
3rd~~> I have dell inspiron running Ubuntu 10.04. The fan barely ever turns on. (and yes that is right, there is only 1 single fan in this system and a giant copper pipe that transfers the heat across this machine) (insert angry face here)
However, the temperature never goes above 30 Celsius. (I have taken the screw driver to my machine, and completely took it apart, reapplied the thermal grease), and dusted it.

If your laptop is older, I highly suggest you do this also. If you are incapable, ask a friend you trust, or get a professional, and ask if you can watch :)

--------------------------------

4th --> What Model is it? and what Video Card is in it?

---

### Post by MasterShihoChief on 2010-05-28
i clean out the fans every weekend, i have take mine apart every three months to reapply thermal paste, its all clean and works fine in windows 7. This is an Alienware Area 51 M17x Gen1 with 2 500gb hdds in raid 0 (i know i know i image nightly) 2 8600m gt's in sli and a c2d 2.2ghz. In windows 7 it idles at 70c according to speedfan even while the gpus are overclocked by quite a bit. If i push my computer to maximum with oc in windows 7 it gets to 90-100c but thats ok, the fans are blasting and everything. In ubuntu, even the live cd, i never hear the fans speed up to what they do in windows 7 and it idles pretty high. The temperature might have been wrong as it was just the AHCI value. The monitor in ubuntu cannot find any temperature readings for anything else, but I know there is a problem when im getting blisters if i go anywhere near the exhaust and i can barely hear the fans.

---

### Post by vandorjw on 2010-05-29
I cannot help you, and it seems to me that others here cannot either.

What I suggest is to continue using windows, and run Ubuntu in a virtual Machine, OR try a different distribution. (But part of me doubts that it is ubuntu that is the problem)

Also, Alien-Ware is now owned by dell. Post it in the Dell subsection.

Hopefully someone there will be able to help you.:P

Best of Luck.

Oo...one thing I thought of is booting with acpi off.
and have BIOS manage the fans and temperatures.

---

### Post by MasterShihoChief on 2010-05-29
well that acpi temperature is accurate its does fluctuate. i took the comp outside in the freezing cold weather while it was raining, and the temp went down(obviously due to the cold air being circulated through the system), took it back inside and temp went right back up to 100c. I tried reinstalling lm-sensors with no luck at all. I tried dellfand but it only showed 1 fan and it was wierd, showed a fan with only .9v running in mode -1 (is there even a -1 mode lol). It seems ubuntu can't detect the fans or the sensors at all. As for disabling acpi in bios, thats not gonna happen seeing as how its a locked bios and that option doesnt even exist. I guess for now I will go back to windows 7 where at least that os can run the fans and my comp wont turn into a melted mess. Can a mod move this thread to the dell section as he suggested to see if i can get help there?

---

### Post by dino99 on 2010-05-29
[http://www.google.com/search?as_q=fan%2Bspeed%2Bubuntu&hl=fr&tbo=p&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=fan%2Bspeed%2Bubuntu&hl=fr&tbo=p&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by MasterShihoChief on 2010-05-29
ive done that, i dont come to the forums for help unless i cant find help for the issue with google. There is nothing in your google search that i havent done that worked.

---

### Post by MasterShihoChief on 2010-06-06
bump

---

### Post by MasterShihoChief on 2010-06-09
bump....

---

### Post by Mark Phelps on 2010-06-09
If you search the forums, you'll find lots of other posts from folks about their machines overheating with 10.04 as well -- and, like in your case, there were no "miracle cures".

If you want to keep running your machine at 100C and burn up a good (and probably, expensive!) machine -- that is your choice. But, continuing to bump this thread on a daily basis is not going to solve that problem.

You appear to be unwilling to face the unfortunate fact that, in the case of your machine, it will NOT work well with Ubuntu 10.04.

Sorry, but it looks like Win7 is the best way for you to go.  At least, it won't destroy your machine by burning it up!

---

