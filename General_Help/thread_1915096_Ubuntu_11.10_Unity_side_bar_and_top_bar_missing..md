---
title: "Ubuntu 11.10 Unity side bar and top bar missing."
date: 2012-01-25
forum: General Help
---

### Post by pkhamidar2com on 2012-01-25
Hello, i dont know how this happened, im relatively new to Ubuntu so im not good at using it. 

I was using compiz so that my side bar would pop up faster because i didnt like waiting for so long. then i was messing around with some other stuff, i saw this cube thing and that looked interesting, but then decided i didnt want it. When i clicked on it, two popups appeared, i was ignorant and didnt read them, and clicked no to both of them... 

This was while i was updating. Then i realized that my bars were missing. 

the side bar where the application and start button was missing. 

Also at the top where the file, open, help, and the start button sound thing. Well the left side where the file, open, help, go was all there, but the right side where the sound, music, and on off button thing was missing. 

Also the colour of the bar at the top was a matt grey, as in there was no gradient like normal, it was just a plain colour, flat. 

I restarted and nothing changed. I dont really know what is wrong. Dont really know what to do either. 

What should i do? How do i restore it back to how it was?

---

### Post by BC59 on 2012-01-25
To reset Unity:
```
unity --reset
```
try this as well:
```
sudo apt-get install --reinstall unity
```
If not working reset Compiz:
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```
sometimes after running you may still need to run this command again
```
compiz --replace & disown
```

---

### Post by pkhamidar2com on 2012-01-25
ok thank you, but i dont know how to get terminal up. (sorry, ubernoob at ubuntu here!)

i cant seem to get terminal up, i dont know the short cut. I tried to get terminal up before to see if i could do anything, which i probably wouldn't have done much. but couldnt.

---

### Post by BC59 on 2012-01-25
Sorry for that, I was not clear.
Press CTRL+ALT+T. Then copy and paste each command. To paste on terminal press SHIFT+CTRL+V. Press Enter and put your password. When you write your password it's not visible. Enter again and wait. Takes long to execute these commands.

---

### Post by BC59 on 2012-01-25
In any case from the CompizConfig Settings Manager you have to check if the Unity Plugin is checked. Sometimes after all this changes is getting unchecked and you don't have Unity.

If you don't have access to this application you can open it through terminal->run

```
ccsm
```

Sometimes when you check it, appear errors, just answer yes to fix them.

---

### Post by pkhamidar2com on 2012-01-26
hey thanks for that, it really saved my Ubuntu :)

Im really enjoying Ubuntu :)

I don't know if there is a way to add a reputation to someone on this forum but if there was i would rep you  :)

---

