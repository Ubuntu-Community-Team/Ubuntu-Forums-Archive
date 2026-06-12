---
title: "compiz problem"
date: 2011-04-29
forum: General Help
---

### Post by irakla7777777 on 2011-04-29
hello.
i heve installed ubuntu 11.04 32bit .
i have problem with compiz, when i type "compiz --replace" , if i enabled desktop cube , windows borders disappeared .
a cannot fix it .
please help me

---

### Post by irakla7777777 on 2011-04-30
anybody knows how to fix it ?

---

### Post by garvinrick4 on 2011-04-30
This is only link I have seen by mc4man:

[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)

---

### Post by JheregJAB on 2011-04-30
try turning on the "window decorations" and move window and resize window plugins in ccsm... that'll get you a start.

unfortunately, at this point you'll have to turn everything on manually, as Ubuntu didn't do a very good job on keeping compiz working across this upgrade. Good luck.

---

### Post by sikander3786 on 2011-04-30
```
unity --reset
```

This command should restore the default Unity/Compiz settings for you.

Or please take a look at this one.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by irakla7777777 on 2011-05-02
I tried these all but the problem is not solved.
i found that when i reset compiz to defaults , export profile and 
change wall to rotete and cube it works :) ::

1). find s0_active_plugins =  and replace ;wall; to cube ;cube;rotate; like that 
s0_active_plugins = core;bailer;detection;composite;opengl;decor;mousepoll;vpswitch;regex;animation;snap;expo;move;compiztoolbox;place;grid;imgpng;gnomecompat;cube;rotate;ezoom;workarounds;staticswitcher;resize;fade;scale;session;

2). find s0_hsize = 2 and s0_vsize = 2 , repace it 
s0_hsize = 4
s0_vsize = 1 .

then import profile file .

it works :D .

then if  change something in compiz manager windows border disappared.

it is same when i replace emerald   "emerald --replace" .

i install ubuntu 11.04 at home and at my office.
problem is same .

nobody knows solution ? .
can anyone help me to fix it ?

---

### Post by Densdoor on 2011-05-02
I would think nothing is wrong with your Compiz. The upgrade didn't save your previous settings as someone already stated.

Go to System/ Preferences/ Compiz Configuration Manager

Then start checking away Effetcs- Window Decoration 
Then- Window Management resize, placement etc... (What you wish)

-Dennis

---

### Post by irakla7777777 on 2011-05-02
yes, you are right.
when i enable some plugin , windows decoration , windows resizer and meny more disabled itself.


then i enable this again and works good.

but when i try to replace emerald (command in windows decoration "emerald --replace ") , borders disappeared .

---

### Post by Densdoor on 2011-05-02
I know not a lot but I know Compiz Fusion basically makes you have to set all the windows properites to your preference which means Windows Decoration, Windows move, Windows resize.

I personally do not know what Emerald is etc.... (new)

-Dennis

---

### Post by oliv54 on 2011-05-02
I'm not sure (I've got another problem myself), but compiz seems to be far more stable in 11.04 with this option: CCSM > Preferences > Backend > Choose "Flat-file".

---

