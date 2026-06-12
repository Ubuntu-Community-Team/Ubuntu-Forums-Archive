---
title: "hddtemp permissions issue in 10.04"
date: 2010-05-20
forum: General Help
---

### Post by 0nelove on 2010-05-20
[SIZE="4"]**UPDATE: SOLVED by reinstalling 10.04 from scratch.  Some combination of the manual/synaptic installation/reinstallation of hddtemp must have made hddtemp un-reconfigurable. [/conjecture&guessing] ... anyway, probably a unique, unreproducible issue.  BIG thanks to stinkeye and everyone else here for the efforts to help!!!**[/SIZE]

```
$ hddtemp -v
hddtemp version 0.3-beta15

```

Issue is that hddtemp can seemingly never be called, except by root.

```
sudo hddtemp /dev/sda
/dev/sda: WDC WD6400AAKS-22A7B0                   &#65533;: 52°C

```
ok fine, but this won't work in conky or applets (nor will netcat yield results properly: odd intermittently blank/incorrect results)

so, to allow direct call of hddtemp,
```
sudo dpkg-reconfigure hddtemp
```
answered yes to the questions.  however, /usr/sbin/hddtemp still shows:
```
-rwsr-xr-x 1 root root 31928 2008-11-06 06:56 /usr/sbin/hddtemp
```
and, predictably:
```
$ hddtemp /dev/sda
/dev/sda: open: Permission denied

```

same result with:
```
$ sudo chmod u+s /usr/sbin/hddtemp
```
which does set the "sticky bit" (I think it's called):
```
$ ls -l /usr/sbin/hddtemp
-rwsr-sr-x 1 root root 31928 2008-11-06 06:56 /usr/sbin/hddtemp

```

same result again, even after sticky bit enabled:
```
$ hddtemp /dev/sda
/dev/sda: open: Permission denied

```

added myself to disk group also.

Installed both from repositories and also by compiling directly - same result.  Thanks for looking!

---

### Post by randwyck on 2010-05-24
So, is there a solution to problem with hddtemp?
Conky doesn't show hdd temperatures unless I manually start it from terminal at startup.

---

### Post by 0nelove on 2010-05-25
> **randwyck said:**
> So, is there a solution to problem with hddtemp?
Conky doesn't show hdd temperatures unless I manually start it from terminal at startup.

Yeah, I guess just subscribe to this thread and hope somebody smarter has the same problem - haha.

---

### Post by randwyck on 2010-05-26
> **0nelove said:**
> Yeah, I guess just subscribe to this thread and hope somebody smarter has the same problem - haha.Doubt it. I guess that's just another thread without answers.

---

### Post by stinkeye on 2010-05-26
> **randwyck said:**
> So, is there a solution to problem with hddtemp?
Conky doesn't show hdd temperatures unless I manually start it from terminal at startup.
You need to change the permissions of hddtemp because you cant run sudo commands from conky.
```
sudo chmod u+s /usr/sbin/hddtemp
```

Test with
```
hddtemp /dev/sda
```

To output just the temperature use the cut command
```
hddtemp /dev/sda | cut -c[COLOR="DarkRed"]34-37[/COLOR]
```


To use with conky
```
${execi 10 hddtemp /dev/sda | cut -c[COLOR="DarkRed"]34-37[/COLOR]}
```(checks temp every 10 secs)
[COLOR="#8b0000"]Adjust the cut command to your output by counting the characters.[/COLOR]


*****My output for [B]*ls -l /usr/sbin/hddtemp*** gives***[/B]
```
-rwsr-[COLOR="Magenta"]x[/COLOR]r-x 1 root root 31928 2008-11-06 23:56 /usr/sbin/hddtemp
```

---

### Post by 0nelove on 2010-05-26
> **stinkeye said:**
> You need to change the permissions of hddtemp because you cant run sudo commands from conky.
```
sudo chmod u+s /usr/sbin/hddtemp
```

....

*****My output for [B]*ls -l /usr/sbin/hddtemp*** gives***[/B]
```
-rwsr-[COLOR="Magenta"]x[/COLOR]r-x 1 root root 31928 2008-11-06 23:56 /usr/sbin/hddtemp
```

Thanks stinkeye, the magenta "[COLOR="Magenta"]x[/COLOR]" is different in my setup.  When I sudo chmod u+s /usr/sbin/hddtemp as indicated here (and elsewhere treating this issue), the result is:
> $ ls -l /usr/sbin/hddtemp
-rwsr-[COLOR="Lime"]s[/COLOR]r-x 1 root root 31928 2008-11-06 06:56 /usr/sbin/hddtemp

off for a permission tutorial.  will return when I figure out how to turn that [COLOR="Lime"]s[/COLOR] to an [COLOR="Magenta"]x[/COLOR].  THANKS STINKEYE - u rok!  :KS
...
EDIT: for some reason, hddtemp resists sudo chmod - permissions stay the same.  hmm...  still checking...
EDIT2: oddly, my permissions look the same as the fellow in this mint linux thread: [http://forums.linuxmint.com/viewtopic.php?f=90&p=212142&st=0&sk=t&sd=a](http://forums.linuxmint.com/viewtopic.php?f=90&p=212142&st=0&sk=t&sd=a)  The difference being that those settings permit him to perform a non-root execution of hddtemp.  Still checking...
EDIT3: is it relevant that the hddtemp daemon is running?  Would that cause hddtemp to refuse a chmod command modifying it's permissions?  I'm stuck again.  :(

---

### Post by 0nelove on 2010-05-26
sorry to self-bump, but I was able to kill the daemon (ps aux | grep hddtemp)(kill ...)(perhaps this was unnecessary, because I used a different chmod command, using 0755 instead of letters)

then, I was able to:
> $ sudo chmod 0755 /usr/sbin/hddtemp
...
$ ls -l /usr/sbin/hddtemp
-rwxr-[COLOR="Magenta"]x[/COLOR]r-x 1 root root 31928 2008-11-06 06:56 /usr/sbin/hddtemp


So, I replaced both "[COLOR="Lime"]s[/COLOR]" permissions with "[COLOR="Magenta"]x[/COLOR]"s

But, alas:
> $ hddtemp /dev/sda
/dev/sda: **Permission denied**


Did I miss something obvious?  feel like I've been thru this 50 times.  Can't figure out why, if rx permission is given to:
 owner (root): -[COLOR="Red"]rwx[/COLOR]r-xr-x 1 root root 31928 2008-11-06 06:56 /usr/sbin/hddtemp;
group (root): -rwx[COLOR="Red"]r-x[/COLOR]r-x 1 root root 31928 2008-11-06 06:56 /usr/sbin/hddtemp; and 
everyone: -rwxr-x[COLOR="Red"]r-x[/COLOR] 1 root root 31928 2008-11-06 06:56 /usr/sbin/hddtemp

...then why is permission denied?

nothing here:
[http://savannah.nongnu.org/bugs/?group=hddtemp](http://savannah.nongnu.org/bugs/?group=hddtemp)

---

### Post by stinkeye on 2010-05-26
I don't know much about permissions but this is what advanced permissions for /usr/sbin/hddtemp shows me.
You can view advanced permissions in nautilus by setting in gconf-editor
/apps/nautilus/preferences/show_advanced_permissions.

Perhaps you could open /usr/sbin/hddtemp in Nautilus as administrator
and make permissions the same.

---

### Post by 0nelove on 2010-05-26
thanks stinkeye - I did take a look by gksudo into nautilus.  I think our permissions are the same...

---

### Post by dcstar on 2010-05-27
> **0nelove said:**
> ```
$ hddtemp -v
hddtemp version 0.3-beta15

```

Issue is that hddtemp can seemingly never be called, except by root.
........

Rubbish, just set the SUID choice:
```
sudo dpkg-reconfigure hddtemp
```

---

### Post by stinkeye on 2010-05-27
> **dcstar said:**
> Rubbish, just set the SUID choice:
```
sudo dpkg-reconfigure hddtemp
```

He said he had already ran **sudo dpkg-reconfigure hddtemp** and answered yes to all the questions.

---

### Post by 0nelove on 2010-05-27
> **stinkeye said:**
> He said he had already ran **sudo dpkg-reconfigure hddtemp** and answered yes to all the questions.

yes, confirmed.  I've been through that dialog several times and answered yes (the first question is the main one for SUID).  

Thanks for looking in tho, dcstar.  If you have the time, take a look thru the first post (above) and let me know if you see anything obvious that I've overlooked.  It has to be something obvious or else other people would have had this problem too...

Thanks a million to all who read thru this far.

---

### Post by randwyck on 2010-06-01
> **stinkeye said:**
> You need to change the permissions of hddtemp because you cant run sudo commands from conky.
```
sudo chmod u+s /usr/sbin/hddtemp
```

Test with
```
hddtemp /dev/sda
```Thanks, I did that, but it didn't help. I still have to manually launch conky if I want to see hdd temperatures. If I make a custom application launcher or place conky to Startup Applications, I get this:
[IMG]http://images17.fotki.com/v524/photos/1/1213475/5870520/conky-vi.png[/IMG]

If I launch it from terminal, on the other hand, I get correct results.
The relevant part of .conkyrc:
```
${color orange}TEMPS ${hr 2}$color
Q8400@${freq}MHz: ${font :size=9:bold}${alignr}${execi 10 sensors coretemp-isa-0000 | grep '+' | cut -b15-16}°C  ${alignr}${execi 10 sensors coretemp-isa-0001 | grep '+' | cut -b15-16}°C  ${alignr}${execi 10 sensors coretemp-isa-0002 | grep '+' | cut -b15-16}°C  ${alignr}${execi 10 sensors coretemp-isa-0003 | grep '+' | cut -b15-16}°C$font
9800GT: ${font :size=9:bold}          ${execi 60 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'}°C${font}
HD103UJ:         ${font :size=9:bold}${execi 10 netcat localhost 7634 | cut -b89-90}°C$font ${alignr}ST3320:       ${font :size=9:bold}${execi 10 netcat localhost 7634 | cut -b58-59}°C$font
WD10EADS:     ${font :size=9:bold}${execi 10 netcat localhost 7634 | cut -b31-32}°C$font
```

---

### Post by stinkeye on 2010-06-01
> **randwyck said:**
> Thanks, I did that, but it didn't help. I still have to manually launch conky if I want to see hdd temperatures. If I make a custom application launcher or place conky to Startup Applications, I get this:
[IMG]http://images17.fotki.com/v524/photos/1/1213475/5870520/conky-vi.png[/IMG]

If I launch it from terminal, on the other hand, I get correct results.
The relevant part of .conkyrc:
```
${color orange}TEMPS ${hr 2}$color
Q8400@${freq}MHz: ${font :size=9:bold}${alignr}${execi 10 sensors coretemp-isa-0000 | grep '+' | cut -b15-16}°C  ${alignr}${execi 10 sensors coretemp-isa-0001 | grep '+' | cut -b15-16}°C  ${alignr}${execi 10 sensors coretemp-isa-0002 | grep '+' | cut -b15-16}°C  ${alignr}${execi 10 sensors coretemp-isa-0003 | grep '+' | cut -b15-16}°C$font
9800GT: ${font :size=9:bold}          ${execi 60 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'}°C${font}
HD103UJ:         ${font :size=9:bold}${execi 10 netcat localhost 7634 | cut -b89-90}°C$font ${alignr}ST3320:       ${font :size=9:bold}${execi 10 netcat localhost 7634 | cut -b58-59}°C$font
WD10EADS:     ${font :size=9:bold}${execi 10 netcat localhost 7634 | cut -b31-32}°C$font
```

Your using ```
netcat localhost 7634
```
To get your hd temps.

In terminal run 
```
hddtemp -n /dev/sda
```

Does that give you a numerical output.


If so, try it in your conky with...
```
${execi 10 hddtemp -n /dev/sda}
```

---

### Post by randwyck on 2010-06-01
> **stinkeye said:**
> ```
${execi 10 hddtemp -n /dev/sda}
```Oh, thank you. That works now.
Sorry I was inattentive.
Could you please explain why netcat was giving such odd results?

---

### Post by 0nelove on 2010-06-01
> **randwyck said:**
> 
Could you please explain why netcat was giving such odd results?

Glad this thread was able to help you.  In the first post above, you can see that we are both experiencing blank (or intermittently incorrect) results from netcat.  Nobody has suggested any answer yet.

I'll keep monitoring here for some additional insight as to why this is - maybe you should subscribe to this thread also and see if anybody has any solutions.  

-OP

---

### Post by randwyck on 2010-06-01
> **0nelove said:**
> Glad this thread was able to help you.  In the first post above, you can see that we are both experiencing blank (or intermittently incorrect) results from netcat.  Nobody has suggested any answer yet.Well, why use netcat then? I didn't know about the alternative, but now I'm happy with my conky setup.
Didn't check how it will behave after rebooting though.

---

### Post by 0nelove on 2010-06-01
> **randwyck said:**
> Well, why use netcat then?

Netcat is apparently more wasteful of resources than simply querying hddtemp itself.  The attempt at netcat was in an effort to make monitoring possible.  Calling hddtemp directly is what I'm still hoping to achieve (or, to use netcat if direct invocation is not possible).

I hope everything continues to work for you.  Best.

---

### Post by stinkeye on 2010-06-01
There's a tutorial here on how to use netcat in conky but as it says at the top of the post hddtemp has a built in variable in conky now.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=1649045&postcount=1[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=1649045&postcount=1")

---

### Post by 0nelove on 2010-06-01
Stinkeye, dude, you are so awesome throwing out the helpful bits.  I think I've scoured the web pretty well for information on this issue.  It's just some really weird permissions issue that I just can't figure out.  I'm going to try hddtemp on some other machines and see if I can duplicate my failure (or perhaps stumble into a success).  Thanks again for looking in!

---

### Post by stinkeye on 2010-06-02
Ok, good luck.
Here's something that might help you.

From my System monitor showing All processes.

---

### Post by 0nelove on 2010-06-15
resolved by fresh install (not because of this niggling issue, but rather because of a bad case of xorg-fuxxoritis).

---

