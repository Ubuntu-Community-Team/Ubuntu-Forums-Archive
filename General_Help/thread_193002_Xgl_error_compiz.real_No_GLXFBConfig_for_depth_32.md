---
title: "Xgl error: compiz.real: No GLXFBConfig for depth 32"
date: 2006-06-09
forum: General Help
---

### Post by joshrobinson on 2006-06-09
i finally get xgl and compiz running on my 64bit dapper laptop, and it boots fine and all my effects work except i have no title bars at the top.. i think its due to this error

compiz.real: No GLXFBConfig for depth 32

i edited my xorg.conf and tried to change to 32bit and add its own resolution line for it but x wont start.. i also tried to reconfigure the xserver with the dpkg command but there is no 32bit option in there.. it says something about using 24 bit

i also have the kernel frame buffering on, because the error glxfbconfig i assumed the FB was frame buffer.. can someone please help me fix this error? i love xgl but i really need the title bar's 

thanks

oh yeah.. its an ati 200m express video card

---

### Post by firetux on 2006-06-09
You have to use the 24bit depth.

---

### Post by joshrobinson on 2006-06-09
[QUOTE=firetux]You have to use the 24bit depth.[/QUOTE]

yeah thats what its set at :-( (i tried changing to 32 with no luck)and for some reason the GLXFBConfig is looking for 32bit config file.. why?

---

### Post by firetux on 2006-06-09
[QUOTE=joshrobinson]yeah thats what its set at :-( and for some reason the GLXFBConfig is looking for 32bit config file.. why?[/QUOTE]
And you didn't have a 32bit section when the prolem occured? Weird.
What else could tell compiz to use 32bit depth?

---

### Post by joshrobinson on 2006-06-09
[QUOTE=firetux]And you didn't have a 32bit section when the prolem occured? Weird.
What else could tell compiz to use 32bit depth?[/QUOTE]

i have no clue.. thats why i attempted to run it on 32bit because it was complaining about it.. some people say its a mesa problem but i have 6.5.1 the newest i could find for amd64

---

### Post by joshrobinson on 2006-06-09
im going to work.. hopefully someone will replay for when i get home.. i want this fixed :-(

---

### Post by QUASAR_FREAK on 2006-06-09
May be you can submit the specs of your laptop, graphic card, etc.

---

### Post by joshrobinson on 2006-06-09
[QUOTE=QUASAR_FREAK]May be you can submit the specs of your laptop, graphic card, etc.[/QUOTE]

i already said its a 64bit laptop running 64bit dapper.. and i said the graphics card is an ati 200m express.. the processor speed and ram shouldnt matter.. but its a 1.8ghz with 1gb of ram

---

### Post by joshrobinson on 2006-06-10
someone please help :-(

---

### Post by QUASAR_FREAK on 2006-06-10
[quote=joshrobinson]i already said its a 64bit laptop running 64bit dapper.. and i said the graphics card is an ati 200m express.. the processor speed and ram shouldnt matter.. but its a 1.8ghz with 1gb of ram[/quote]

oh sorry i didn't see it ](*,)

I've an nvidia card so i can't help you but sure you'll have better luck posting this in compiz.net (the compiz forums)

---

### Post by joshrobinson on 2006-06-11
[QUOTE=QUASAR_FREAK]oh sorry i didn't see it ](*,)

I've an nvidia card so i can't help you but sure you'll have better luck posting this in compiz.net (the compiz forums)[/QUOTE]

i started a thread here and there at the same time.. and there is no responses on there.. at least someone here actually replied to me :(

---

### Post by QUASAR_FREAK on 2006-06-11
=/

---

### Post by firetux on 2006-06-11
[http://www.rage3d.com/board/showthread.php?p=1334361825](http://www.rage3d.com/board/showthread.php?p=1334361825)

Post #48, hope it helps, it appears to be a bug.

---

### Post by joshrobinson on 2006-06-11
[QUOTE=firetux][http://www.rage3d.com/board/showthread.php?p=1334361825](http://www.rage3d.com/board/showthread.php?p=1334361825)

Post #48, hope it helps, it appears to be a bug.[/QUOTE]

yeah ive seen that post, and that patch in my millions of hours of googling.. but i have no idea what to do with that patch, or how to apply it :-(

---

### Post by fadeh on 2006-06-15
Thanx to a friend of mine we have solved this problem:

1- download this patch: [http://www.rage3d.com/board/showthread](http://www.rage3d.com/board/showthread). … amp;page=2    -----> POST #48

2- from root: apt-get build-dep compiz-vanilla

3- from root: apt-get source compiz-vanilla

4- cd into the unpacked dir

5- patch p1 < compizPatch.patch

6- cd ..

7- from root: apt-get source -b compiz-vanilla

8- dpkg -i compiz-vanilla-(etc...).deb


I Hope developers can include this patch into next release.

Bye,

fadeh

---

### Post by koolatron on 2006-06-27
Fadeh!  THANK YOU!

I've been wrestling with compiz for the past two days straight.  Your patch worked like a charm.

I'm stll having fglrx issues, but they're isolated and I think I can live with them (that is, until next payday when I go out and splurge on a new video card!)

Again, THANKS!

(for those with this same problem - do the following:  Go to the above-mentioned post and cut-and paste the patch text into a text file named compizPatch.patch.  Follow Fadeh's instructions on fetching the source from apt, then move the patch file you created into the source directory and apply the patch using the `patch -p1 < compizPatch.patch` command.  Build the source and install the packages just like in the Fadeh's step-by-step)

---

### Post by joshrobinson on 2006-06-27
yeah it worked for me too.. he replied on the compiz forums and saw it there.. i just wish it worked for the regular compiz.. not vanilla.. because vanilla is missing plugins and i cant change the color of my drop shadows..

would be nice if someone could write this patch for quinnstorm source:-D

---

### Post by neikous on 2006-12-02
the link to that patch is no longer working. does anyone have the full link?

---

### Post by mbradlcu on 2007-05-17
I found this fix here: [http://www.linuxquestions.org/questions/showthread.php?t=493176](http://www.linuxquestions.org/questions/showthread.php?t=493176)
basically all you have to do is add the following to you're /etc/X11/xorg.conf in the nvidia device section:

Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "True"

I got the same error after using the nvidia-settings tool to update my xorg.conf,, after that I had the same error reported by the thread, adding those 2 lines fixed the problem.

have fun

---

### Post by Centx on 2007-06-28
> **mbradlcu said:**
> I found this fix here: [http://www.linuxquestions.org/questions/showthread.php?t=493176](http://www.linuxquestions.org/questions/showthread.php?t=493176)
basically all you have to do is add the following to you're /etc/X11/xorg.conf in the nvidia device section:

Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "True"

I got the same error after using the nvidia-settings tool to update my xorg.conf,, after that I had the same error reported by the thread, adding those 2 lines fixed the problem.

have fun

Thanks, Ive been looking for a solution to this for some time (using Compiz-Fusion), and you got it right on the spot. again, thanks :KS

---

