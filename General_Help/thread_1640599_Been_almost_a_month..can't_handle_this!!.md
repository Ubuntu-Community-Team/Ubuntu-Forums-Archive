---
title: "Been almost a month..can't handle this!!"
date: 2010-12-08
forum: General Help
---

### Post by abdusamed on 2010-12-08
arrgg....! this is what i'm experiencing right now and it's annoying has hell



[LIST=1]
[*]no flash video running, just 30+ tabs, firefox is consuming 78percent of dual core 2.4ghz!! WHAT'S THE PROBLEM? They are just bunch of webpagese displaying text, not some graphicy stylish html5 or page blasted with gif images!
[*]Compiz or metacity, same crappy firefox experience... what i'm typing right now is not even realtime!!! it's lagging!
[*]Mplayer apparently decodes videos with more cpu than tomtem!! like 40 percent for mplayers ..same vid on tomtem... 3 percent!!!
[*]I can't turn of compiz because when i do, after reboot, it truns back on!
[*]If I set my own setting in compiz, they revert back after reboot!
[*]also facing ```
pa_stream_writable_size() failed: Connection terminated
• Message: Error: pa_stream_writable_size() failed: Connection terminated 
```
[*]Geany crashes....I just don't use it now
[/LIST]
Anything is hsoudl try applying?

---

### Post by clhsharky on 2010-12-08
abdusamed

In terminal
```
top
```
Paste back so we can help more.

```
metacity --replace
```
Will turn off compiz.

Sharky

---

### Post by wet-willy on 2010-12-08
Operating systems nowadays load as much as possible in processor caches and ram memory as it's much faster than calling on the hard drive to send needed files.
> 30+ tabs, firefox is consuming 78percent of dual core 2.4ghz!!
All these tabs are held in memory, if your OS was using most of it before, now it's pushed back to slower forms of memory.
> it's lagging!
Gee!
I wonder why?
> same vid on tomtem... 3 percent!!!
Run command: **apt-get purge mplayer because I prefer Totem and don't want to make an *** of myself ranting in forums**.
> I can't turn of compiz because when i do, after reboot, it truns back on!
Install fusion icon.
> If I set my own setting in compiz, they revert back after reboot!
Try running the compiz settings manager GUI as sudo or root, might be a user restriction.

---

### Post by abdusamed on 2010-12-12
First... I'm using the VDPAU mplayer. When my option was set to video decoder maybe to 'vdpau', it was decoding a normal xvid movie at 60cpu which was just **** but when set to xv... cpu was back to normal decoding..10-8 cpu..much less then totem.

When I tried the metacity replace command in terminal, I read a interesting message ouput, 
```

Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_group"

```
I use ubuntu tweak and I remember deleting loads of configuration files to 'save space'. As u see, it bakc fired, now I think no more new configuration files are being made, anyway to fix this?

---

### Post by abdusamed on 2010-12-15
bump

---

### Post by cottfcfan on 2010-12-16
Make sure that fusion-icon is set to start at boot in startup applications.
Whatever you set it too whether compiz or metacity, should then remain as you set it when logging in/out or rebooting.

---

### Post by abdusamed on 2010-12-19
> **cottfcfan said:**
> Make sure that fusion-icon is set to start at boot in startup applications.
Whatever you set it too whether ***piz or metacity, should then remain as you set it when logging in/out or rebooting.

***piz does boot up but its setting are all changed to something close to default. Like..***piz doesn't seem to fully load everything... really weird. Forexample..the alt-tab doesn't work eventhough its selected on ***piz manager as 'on'. I have to uncheck and check to get it working. Same with desktop wall.. i don't get the transtion of the panel moving left to right. All i get is simpel wall change

One more thing..Kupher doesnt sometime work after suspend...no matter how many times i have to kill it and start it.. ***plete boot fixes it. But it's matter of time before it stops working

Just before i wrap this up...sometimes... xorg usage is sky rocketed because of docky..but sometimes its fine... I have already applied the lines and tweaks after googlign.... but still it's ***plete randomly. Like right now..it's working briliant.. ram is 3.5..but i am not experiencing any lag at all... everything is smooth as silk... I tbh don't feel like rebooting. Afraid it might turn back into its original form.. :'(

---

### Post by wet-willy on 2010-12-19
> **abdusamed said:**
> ***piz does boot up but its setting are all changed to something close to default. Like..***piz doesn't seem to fully load everything... really weird. Forexample..the alt-tab doesn't work eventhough its selected on ***piz manager as 'on'. I have to uncheck and check to get it working. Same with desktop wall.. i don't get the transtion of the panel moving left to right. All i get is simpel wall change

One more thing..Kupher doesnt sometime work after suspend...no matter how many times i have to kill it and start it.. ***plete boot fixes it. But it's matter of time before it stops working

Just before i wrap this up...sometimes... xorg usage is sky rocketed because of docky..but sometimes its fine... I have already applied the lines and tweaks after googlign.... but still it's ***plete randomly. Like right now..it's working briliant.. ram is 3.5..but i am not experiencing any lag at all... everything is smooth as silk... I tbh don't feel like rebooting. Afraid it might turn back into its original form.. :'(

I think you should stray from bitching about Ubuntu, I'll waver a ton of posts against your unstable hardwaere configuration which is more than likely the root cause of your lippin' like you're some kind of Linux super-geek trying to tell the Ubuntu community the operating system of "
your choice" is not performing as you "think" it should.

---

