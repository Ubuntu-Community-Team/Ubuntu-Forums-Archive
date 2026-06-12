---
title: "login screen freeze for 12.04"
date: 2012-04-19
forum: General Help
---

### Post by fillenullepart on 2012-04-19
hi,

i ran the upgrade from 11.10 to 12.04 today - everything seemed to go well, but on restart, the machine freezes at the login screen - the mouse is operative until the screen is fully loaded, after which it freezes in place, and the cursor, even if in the password field, is froze. i've tried waiting a few seconds, even minutes, but the machine is completely frozen.

have restarted many times.  nothing works.

does anyone else have experience with this problem?  is there a way to rollback to 11.10?  is there a way to allow auto-login to bypass the startup screen if i go into the system as root, via console, and hack something?

i should have known better.  i don't know what i was thinking.

---

### Post by raja.genupula on 2012-04-19
HI Welcome to Forums :)

* 12.04 is still in the BETA , its not released officially .  
* There is no possibility to downgrade to Ubuntu 11.10 , so the only choice you have with you is Reinstallation of 11.10 .


So now try this , Press ctrl+alt+f1 after freeze . it will take you to CLI . login there with your username and password ..

then type this 
```
sudo stop lightdm
sudo start lightdm
```

if takes you too GUI ,no problem other wise do this 
```
ubuntu-bug lightdm 

```

let us know what you got .

---

### Post by fillenullepart on 2012-04-19
will try, but previous attempts to press ctrl alt f1 at the login screen have no effect.  nothing happens.  it's like there's no input possible once the screen freezes.  but, will try again anyway.

---

### Post by fillenullepart on 2012-04-19
got to terminal screen before login screen loaded - followed instructions, second command starts gui again, still frozen.

:/

---

### Post by raja.genupula on 2012-04-19
ok use third command to report the BUG , BTW what kind of VGA drivers are you got ?

---

### Post by fillenullepart on 2012-04-19
is there a command line configuration utility that i can use to set auto-login to true so i can bypass the login screen?

and, if i reinstall 11.10, what happens to all existing data and partitions? i have two and a half years worth of data on this machine and don't want to lose it if i don't have to.

---

### Post by HiImTye on 2012-04-19
start it again but move its output into a file so you can see if it tells you whats wrong, i.e.
```
stop lightdm
/etc/init.d/lightdm start > out.txt
```
and then post the output of out.txt here within code tags (hightlight it and then click on the '#' above the text entry box)
to read the file use
```
cat out.txt
```
or
```
less out.txt
```

---

### Post by fillenullepart on 2012-04-19
think video is nvidia, but not sure, and don' t know how to find out.  :/

---

### Post by fillenullepart on 2012-04-19
> **HiImTye said:**
> start it again but move its output into a file so you can see if it tells you whats wrong, i.e.
```
stop lightdm
/etc/init.d/lightdm start > out.txt
```
and then post the output of out.txt here within code tags (hightlight it and then click on the '#' above the text entry box)
to read the file use
```
cat out.txt
```
or
```
less out.txt
```

can't post it here because i can't get into the gui, hence, no browser - am using someone else's computer to access the forum.  do you know of a way i can change the configuration from a command line so that i can set autologin to true and bypass the login screen?

---

### Post by HiImTye on 2012-04-19
```
sudo nano /etc/lightdm/lightdm.conf
```
enter your username after the '='
```
autologin=
```

---

### Post by fillenullepart on 2012-04-19
> **HiImTye said:**
> ```
sudo nano /etc/lightdm/lightdm.conf
```
enter your username after the '='
```
autologin=
```

ok, bypassed login screen - mouse fine for about 3 seconds, then frozen again.

i guess i am just luckless.

does anyone have a link to the ISO download for 11.10?

---

### Post by HiImTye on 2012-04-19
[www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest]("http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest")
thats the 32 bit download

---

### Post by fillenullepart on 2012-04-19
> **HiImTye said:**
> [www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest]("http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest")
thats the 32 bit download

and ... do you know how to burn an ISO in windows 7?

---

### Post by HiImTye on 2012-04-19
the Ubuntu page gives these instructions:
> Right-click on an ISO image and choose 'Open with > Windows Disc Image Burner'.
Select a disk burner (drive) and choose 'Burn'. If you check 'Verify  disc after burning', it will confirm that the ISO image has been burned  correctly.

---

### Post by fillenullepart on 2012-04-19
> **HiImTye said:**
> the Ubuntu page gives these instructions:

thank you so much for your help.

---

### Post by HiImTye on 2012-04-19
no problem :)
sorry that I couldn't fix your 12.04 install

---

### Post by fillenullepart on 2012-04-19
> **HiImTye said:**
> no problem :)
sorry that I couldn't fix your 12.04 install

it's okay, thanks for trying. maybe i will have better luck when the final release comes ... but, next time, i think i'll check the forums before i blindly install.

the whole reason i wanted to upgrade was to try and get around the cpu overheat issue in 11.10 - it's always running way too hot and i can't figure out how to cool it down.

maybe if i can get 11 reinstalled, i'll come back and ask...

---

### Post by fillenullepart on 2012-04-19
and, just for the record, rolling back to 11 has been a nightmare as well - no touchpad support once install completed, no wireless capabilities, just a big mess.

never again.

---

