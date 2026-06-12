---
title: "Launch some programs at the boot (in specific places)"
date: 2010-11-11
forum: General Help
---

### Post by Gewdgame on 2010-11-11
Hello.

First, I'd like to apologize for my weak english.
My wish is to launch some programs (chromium, pidgin and xchat on the first virtual desktop and the terminal, the file manager and geany on the second one). I also wish them to have the same size and place than they've had the last time I used them (just to keep them always at the same place).
My researches haven't been successful for the moment cause the only idea I found was lxsession-edit which doesn't do exactly what I want...

Has someone ever succeeded to do what I want?

Thanks a lot.

PS: I use lubuntu, but I guess it's quite the same with ubuntu (and mayby xubuntu)

---

### Post by Foxheadz on 2010-11-11
Well you can go to System>prefrences>startup applications and there you can go to the options tab and select remember open application on log out so pretty much what ever you have open should open when you log out/restart your computer

---

### Post by Gewdgame on 2010-11-11
Thanks for a so quick answer but in preferences I don't have "startup applications" :/

---

### Post by Foxheadz on 2010-11-11
Ah well im not that familiar with lubuntu so if you dont have it then i dont know what to do

---

### Post by bioterror on 2010-11-12
Ahhh, I just noticed this tab open and I remembered we had a discussion over the IRC.

Well here's more information about launching applications:


> 
~$ cat /home/lubuntu-user/.config/autostart/conky.desktop

[Desktop Entry]
Name=Conky
Comment=blaeh!@#%
Exec=conky
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;

~$ 


And then for the position:

```

~$ nano -w /home/lubuntu-user/.config/openbox/lubuntu-rc.xml

```

And add to the Applications section:

```

<application name="urxvt">
      <decor>yes</decor>
      <focus>yes</focus>
      <position>
        <x>-5</x>
        <y>5</y>
      </position>
      <layer>below</layer>
      <desktop>1</desktop>
    </application>

```

---

### Post by Gewdgame on 2010-11-12
OK, thanks ;)
Tell me if what I'm writting is ok (don't wanna make something crash)

```
~$ cat /home/lubuntu-user/.config/autostart/chromium.desktop
```

```
[Desktop Entry]
Name=Chromium
Comment=blaeh!@#%
Exec=chromium
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;
```

```
~$ cat /home/lubuntu-user/.config/autostart/pidgin.desktop

```
```
[Desktop Entry]
Name=Pidgin
Comment=blaeh!@#%
Exec=pidgin
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;

```
[HTML]~$ cat /home/lubuntu-user/.config/autostart/xchat.desktop[/HTML]

```
[Desktop Entry]
Name=Xchat
Comment=blaeh!@#%
Exec=xchat
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;
```

```
~$ cat /home/lubuntu-user/.config/autostart/conky.desktop
```

```
[Desktop Entry]
Name=Conky
Comment=blaeh!@#%
Exec=conky
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;
```

```
~$ cat /home/lubuntu-user/.config/autostart/geany.desktop
```

```
[Desktop Entry]
Name=Geany
Comment=blaeh!@#%
Exec=geany
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;
```

I cannot find the "Exec" for the terminal (apparently it isn't "terminal") and for the file manager :s

And then


```
~$ nano -w /home/lubuntu-user/.config/openbox/lubuntu-rc.xml
```

```
<application name="Geany">
      <decor>yes</decor>
      <focus>yes</focus>
      <position>
        <x>-5</x>
        <y>5</y>
      </position>
      <layer>below</layer>
      <desktop>2</desktop>
    </application>
```

I'll have to try to find the correct x and y :) But is it the same file for all the applications (for the location) ?

Thanks a lot

---

