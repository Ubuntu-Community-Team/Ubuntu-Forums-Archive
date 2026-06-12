---
title: "Auto screen backlight level  Ubuntu 11.10"
date: 2012-03-21
forum: General Help
---

### Post by essex lad on 2012-03-21
Is anyone able to tell me how to autorun at bootup the following
command:

**xbacklight -set 50**

as you can see, I am trying reduce the brightness of the laptop screen automatically at startup

This is a problem with all the linux distros that I have tried,

Surely developers can make the available Screen brightness adjustments stick until changed by the user,not just until the end of the session - or is this more difficult than I realise

I would appreciate any input

Thanks

---

### Post by HiImTye on 2012-03-21
go to 'Startup Applications' then click 'Add' give it a name, enter that into 'command' and away you go.

note you might want to give it a bit of a delay to make sure that it is run after more important things (such as the modules you need to invoke) the command would be something like:

```
sleep 15 && <your command>
```
change the '15' to any number of seconds you want

---

### Post by essex lad on 2012-03-21
> **HiImTye said:**
> go to 'Startup Applications' then click 'Add' give it a name, enter that into 'command' and away you go.

note you might want to give it a bit of a delay to make sure that it is run after more important things (such as the modules you need to invoke) the command would be something like:

```
sleep 15 && <your command>
```
change the '15' to any number of seconds you want
Wow-that simple !!
Thank you very much for the info - I still think that distros should not have this kind of problem - adjustments should stick until the user chooses to change it

---

