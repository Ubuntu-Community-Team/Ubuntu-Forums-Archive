---
title: "Ubuntu 11.10 Unity/Compiz application windows missing frame"
date: 2012-02-27
forum: General Help
---

### Post by sirriffsalot on 2012-02-27
Greetings!

The terminal, opera and other windows do not have a frame of which I can left click to drag around, and of course they are also therefore missing a close, resize and minimize button. Compiz doesn't seem to have a way of solving this; in fact, if I change something in Compiz, such as Window Decorations, chances are good that Ubuntu freezes to such an extent that I cannot restart my computer in any other way than to hold the on button until it shuts off... 

Peculiarly enough, folder windows have framing around them as things should be, but the ones mentioned above do not.:-S Any ideas?

Cheers!

--> Leo

---

### Post by Frogs Hair on 2012-02-27
Install the Compiz Config Settings Manager if not already and make sure window decoration is activated .

---

### Post by sirriffsalot on 2012-02-27
In my previous post I wrote in some detail that I have already done that... :-)

---

### Post by JC Cheloven on 2012-02-27
Hi, not using unity/compiz (lxde here), and less worried as time passes, but I may offer some emergency workarounds:

Alt + click&drag everywhere in the window should move the window.

Alt + Space should popup a menu for maximize, restore, close, etc.

Hope this is of any help
JC

---

### Post by sirriffsalot on 2012-02-27
Thanks, fortunately I found my way to these temporary solutions earlier today, no telling what my computer would have looked like if I hadn't, haha! Cheers!

---

### Post by Disabled20240622 on 2012-02-27
Under the "Window decorations" plugin, is "Decoration windows" set to all?

How extensive are your mods to compiz? Does it work with the "Unity" plugin off? It can be extremely sensitive to changes or use of other plugins.

If you go into "Preferences" and save your config, then load defaults, does that work?

The above is all in CCSM.

---

### Post by sirriffsalot on 2012-02-28
Hey! I'm not quite sure what you mean by "set to all.&#8221; I am also slightly unsure how to respond correctly as to how extensive my compiz mods are &#8211; use baby-step language please!:)  If I disable Unity things get very unstable (in Ubuntu "Unity", although in the login selection for desktop environments it only says "Ubuntu", not "Ubuntu Unity") to the point where I have to restart my computer... The same is true for how to save my config in &#8220;Preferences&#8221;, and loading defaults means &#8220;Reset to defaults&#8221; I presume? 

The problem with disabling Unity is that if I do that in Compiz on Ubuntu (Unity), the panels I cannot maneouver around without disappears and I have no idea what to do from there, heh.. Right now I'm using 2d and disabled Unity and fortunately the sidebar and panels remained without complications...

One thing is for certain, though... Judging from the number of posts concerning issues within this relatively small field (Unity-Compiz), things are very unstable! Easy to say, I know, coming from someone who has hardly any clue how it works, but that's my take on it anyway.. 

After the mess I've made yesterday I prefer being very cautious as to how I configure things, haha. No more guesswork:) If you could be more spesific with your instructions I'll gladly follow them. Cheers!

&#8594; Leo

---

### Post by Frogs Hair on 2012-02-28
> **LeoTB said:**
> In my previous post I wrote in some detail that I have already done that... :-)

Sorry about that !  :oops:

Have you tried ? ```
unity --reset
```

---

### Post by stinkeye on 2012-02-28
You can reload window decorations, in the terminal with this...
```
gtk-window-decorator --replace & disown
```

---

### Post by sirriffsalot on 2012-02-28
"unity --reset" did not fix the framing issue, and furthermore disabled the wobbly window function for some reason + disabled the unity panel to the left once again. Tried it before and again just now with the same results... :-/ 

Are the Ubuntu developers aware of all the complications around with Compiz and Unity combined? Are they working at some solution(s)?

---

### Post by stinkeye on 2012-02-28
**unity --reset** will set compiz back to defaults where wobbly windows are disabled and the 
launcher is hidden until you move the mouse to the left edge of the screen.

---

### Post by sirriffsalot on 2012-02-28
Hey! In order to do reload decorations with that command I first had to have compiz-gnome installed, is the fact that I did not have this helpful in finding out why I have this frame problem?

I ran the command after having installed compiz-gnome and funnily enough it worked; to such an extent that the decorations I had previously configured to no avail appeared as well... It seems that compiz-gnome had something to do with this, why is it not included in the compiz package I wonder? 

Thanks for that one, appreciate all the help from everyone!

---

### Post by sirriffsalot on 2012-02-28
Haha, I tried **unity -reset** after the previous solution and now things got more straightened out in the way you said it would. Once again there clearly was a need for compiz-gnome for things to work out, or what do you think?

---

### Post by stinkeye on 2012-02-28
Not sure, but I think compiz-gnome is part of the default install.
Did you upgrade or clean install 11.10?
> compiz-gnome
This package contains files needed to integrate compiz with the GNOME desktop
environment.

---

### Post by sirriffsalot on 2012-02-28
No, when I tried your first suggestion with gke the terminal informed me of what I was missing, and I ran the "sudo apt-get" command it suggested. From there everything was downhill as previously mentioned. I didn't upgrade or reisntall to 11.10 at all, just added compiz-gnome to it.. Weird:) With that quote in mind, no wonder things got as messed up as they did! Cheers, once again :)

---

### Post by Tybear241083 on 2012-03-13
> **stinkeye said:**
> You can reload window decorations, in the terminal with this...
```
gtk-window-decorator --replace & disown
```

Thanks for this. I have been using unity --reset and it usually sorts out the issue but it then takes all of my applications and plonks them on the top left desktop which is annoying. I only have this issue on one of my Ubuntu machines.

I have now saved this command in my .bash_aliases file as fix_windows e.g.

```
fix_windows="gtk-window-decorator --replace & disown"
```


Now whenever my windows disappear I simply do a Ctrl+F2 and type fix_windows and I am done :) much better.

Thanks again.

---

### Post by BoogeyOfTheMan on 2012-05-17
> **stinkeye said:**
> You can reload window decorations, in the terminal with this...
```
gtk-window-decorator --replace & disown
```

I was having a similar problem, except I did it myself. Theres a little button on the top left of my menu bar, so I clicked it, and my window decorations disappeared. (I like to keep the min/max/close buttons on the right as thats how its been for years and what I'm used to)

Anyway, that command you provided fixed my issue, thanks.

---

