---
title: "Xubuntu 11.04 sound problems.."
date: 2011-09-09
forum: General Help
---

### Post by sir.sargento on 2011-09-09
Hello all... Just did a fresh install of Xubuntu 11.04 and my sound is not working. Have not had this problem on any other of my ubuntu installations. I checked my sound settings to make sure the correct device was selected and wasn't muted etc... Is there something that may not have installed? This is driving me nuts so any help would be useful. 

Thanks, 
Tony

---

### Post by Bodsda on 2011-09-09
> **sir.sargento said:**
> Hello all... Just did a fresh install of Xubuntu 11.04 and my sound is not working. Have not had this problem on any other of my ubuntu installations. I checked my sound settings to make sure the correct device was selected and wasn't muted etc... Is there something that may not have installed? This is driving me nuts so any help would be useful. 
 
Thanks, 
Tony
 
Please run the following command in a terminal
```

alsamixer

```
That will load a CLI based audio management type screen, in the top left corner it tells you which key to press to get all options, I think it is F5. After doing that ensure all sliders are at 100%
 
Let me know if that works
 
Cheers,
Bodsda

---

### Post by sir.sargento on 2011-09-09
Hey Bodsda.. I tried running 'alsamixer' as suggested and double checked that all sliders were up. Unfortunately this did not fix my problem. Any other suggestions?

---

### Post by Bodsda on 2011-09-09
> **sir.sargento said:**
> Hey Bodsda.. I tried running 'alsamixer' as suggested and double checked that all sliders were up. Unfortunately this did not fix my problem. Any other suggestions?
 
Only one other thing springs to mind. When pulseaudio was first introduced, it was incorrectly configured and just plain didnt work for a lot of people. 
 
Try running this
```

killall pulseaudio

```
 
Run it more than once, until the command says that no process was found. Then launch a media player, any sound?
 
Bodsda

---

### Post by sir.sargento on 2011-09-09
I am sorry to say that it didn't work either. This is just so odd. Never had a problem with sound using any other ubuntu installations on this desktop.

---

### Post by Bodsda on 2011-09-09
> **sir.sargento said:**
> I am sorry to say that it didn't work either. This is just so odd. Never had a problem with sound using any other ubuntu installations on this desktop.
 
Hmm, the fact that alsamixer did show some sliders mean the card works. Oh.. actually, in alsamixer, one of the F<#> keys allows you to select a sound card can you try that and select a all the other cards (if any) and see if any of them have sliders not at 100%
 
Thanks,
Bodsda

---

### Post by sir.sargento on 2011-09-10
All the sliders were up on all cards :(

---

