---
title: "any idea how to make conky transparent ?"
date: 2011-02-08
forum: General Help
---

### Post by rvchari on 2011-02-08
i tried searching for options to add conky class to make it look semi transparent, i could not find it, any idea how do i get into this ?

---

### Post by Habitual on 2011-02-08
[http://ubuntuforums.org/showthread.php?t=281865"]The conky Super-Thread](") or [Search that Super-Thread for the word 'transparent']("http://ubuntuforums.org/search.php?searchid=79281381")

but check these values in your conkyrc
```
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by rvchari on 2011-02-08
thank you buddy...
got that solved...
another problem i ve been facing since i installed conky, weather forecast doesnt seem to function !!! i tried everything as mentioned, every time it says no internet connection !!!

---

### Post by Habitual on 2011-02-08
a/the conky 'weather forecast', or some other applet?

---

### Post by rvchari on 2011-02-08
solved this atlast.
i had conkyForecast, everything.
everytime i checked the rc file i found everything ok.
i had my location at Mumbai, India which did not work out. it needed the code number. i found that out, replaced it and conky restarted on its own, set itself right !!!

thanks buddy...

i ll mark this thread as solved now

---

### Post by Habitual on 2011-02-08
Glad it worked out.

---

### Post by mr_luksom on 2011-03-08
I'm trying to do the same thing.

I have the following in my .conkyrc, however I get a solid black background...

Are there any other settings I should be looking out for?

```


own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

own_window_argb_visual yes
own_window_argb_value 100


```

---

### Post by stinkeye on 2011-03-09
From **man conky**...> own_window_argb_visual 
Boolean, use ARGB visual? ARGB can be used for real transparency, note that a composite manager is required for real transparency. This option **will not work as desired** (in most cases) **in conjunction with 'own_window_type override**'.

Change 
```
own_window_type override
```
to
```
own_window_type normal
```

---

