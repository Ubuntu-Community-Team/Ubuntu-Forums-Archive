---
title: "amixer Volume Control: Unable to find simple control 'Master'"
date: 2011-12-12
forum: General Help
---

### Post by hypertyper on 2011-12-12
I'm trying to create custom shortcuts to change the volume. I can use amixer to change the 'Mic' volume but when I try to change the master I get "Unable to find simple control 'Master'". 

The sound is working and I can change it via the menu but I'm really keen on keyboard shortcuts. I tried aumix as well which didn't work.

When I enter "amixer scontrols" I only have 'Mic' on the list, no master. 

Any ideas?

I'm running 11.10 with onboard sound. 

Thanks


edit: Found a solution by trial and error. If anybody can tell me how I could have actually found this out I'd be grateful.

I had always tried 'amixer sset Master 5+'. Trying to list devices I never found anything other than mic. Now I played around with the -c 0,1,2 command and found that this works for my master:
```
amixer -c 2 sset Master 5+
```

Is there any way of finding out that my master was under c 2?

---

### Post by mp19uy on 2012-06-15
I don't know if you already solved your problem, but I'm having right now exactly the same problem and I found this: [http://www.soyfacus.com.ar/2012/01/subir-o-bajar-el-volumen-desde-consola.html](http://www.soyfacus.com.ar/2012/01/subir-o-bajar-el-volumen-desde-consola.html)

I don't know if you know Spanish (to read the article from the link) but isn't important anyways, I'll translate the "useful" part:

If you have the following error: *amixer: Unable to find simple control 'Master',0*, it is because the "Master" control doesn't exists, at least with this name, on your system.
You'll need to execute: *amixer scontrols* in order to know how your "Master" is named.

And now, you just simply replace Master, with the name the command amixer scontrols has given you.

Here are some useful commands (also, from the link I posted above):

To increase the volume (for example 10%): amixer sset Master 10%+ 
To decrease the volum (for example 5%):  amixer sset Master 5%- 
To mute:                   amixer sset Master mute 
To unmute:                amixer sset Master unmute 
To toggle mute:        amixer sset Master toggle 

(where the Master word changes depending what returns you the command amixer scontrols)

---

