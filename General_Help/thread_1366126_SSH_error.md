---
title: "SSH error"
date: 2009-12-28
forum: General Help
---

### Post by endoglastic on 2009-12-28
I have x11 forwarding on both client and server forwarded. When i type this in, i get this output and it doesnt open it in a gedit application.
 
root@sam-server2:~# gedit /hlds/cstrike/addons/amxmodx/configs/users.ini &
[1] 5429
Xlib: extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib: extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib: extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib: extension "Generic Event Extension" missing on display "localhost:10.0".
 
then after i press enter
 
[1]+ Done gedit /hlds2/cstrike/addons/amxmodx/configs/users.ini
 
 
it seems like its opened up but its not displaying it. Can anyone help, it was working earlier and then something happend i think on client side and then i unistalled xming and reinstalled it and it still doesnt work, anyone know why or any help in fixing it? (Using ubuntu 9.10 desktop edition w/ gnome)

---

### Post by iponeverything on 2009-12-28
```
"localhost:10.0".
```

When you ssh to server side do: 

```
ssh -X user@host
```

Or if the client and server are on the same host and you like the hash prompt, I would invoke bash with sudo.

---

### Post by endoglastic on 2009-12-28
Well i am a noobie and i dont really see why i should use that if i am using putty? Also i type gedit at my linux box at my house. I have one here and one at my bros house. The gedit works here but not there, we have the same configuration settings. Its weird when i do this inside of putty for fun it gives me this: ( and then is seems after i type it as his house, the gedit wont work at mine again (thats what it seemed like), I did this yesterday, and then this morning gedit work at my house again.) And today i did it again and it works fine at my house and no matter what i do in the terminal at his from here it still wont work there)
 
```
 
root@Sam-linux-server:~# ssh -X root@xxxxxxxx
The authenticity of host xxxxxxxxx(xxxxxxxxxxx)' can't be established.
RSA key fingerprint is fa:ff:af:e2:0a:3a:fc:a8:ad:6a:8a:4c:57:fd:db:4a.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added xxxxxxxxx(RSA) to the list of known hosts.
root@xxxxxxxxx password:
Linux Sam-linux-server 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Mon Dec 28 10:32:01 2009 from xxxxxxxxxx
root@Sam-linux-server:~# gedit
Xlib:  extension "Generic Event Extension" missing on display "localhost:11.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:11.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:11.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:11.0".
root@Sam-linux-server:~# X11 connection rejected because of wrong authentication.
 

```

---

### Post by iponeverything on 2009-12-28
putty?

Are you going to from windows to Linux?

I don't know how to break this to you, but Windows does not support the X11 protocol out of the box.

---

### Post by endoglastic on 2009-12-29
Here is what im doing. I am using windows vista with putty and xming. X11 forwarding does work. Except it does not work on my linux box at my bro's house, but it works at mine. The gedit pops up at my house and when i do the same thing with my bros ip, it does not pop up. I even get those errors when i connect to mine but it pops up for mine but not his. Both of these houses have the same configuration files because i set both of them up the same way.

---

### Post by iponeverything on 2009-12-29
> **endoglastic said:**
> Here is what im doing. I am using windows vista with putty and xming. X11 forwarding does work. Except it does not work on my linux box at my bro's house, but it works at mine. The gedit pops up at my house and when i do the same thing with my bros ip, it does not pop up. I even get those errors when i connect to mine but it pops up for mine but not his. Both of these houses have the same configuration files because i set both of them up the same way.

Ok, so you can account for the xming configuration on your bro's box. How about dozens of other mysterious happenings on a windows machine?

See if there is anything in the event logs or if xming generating a log.

---

### Post by Project PWNED on 2009-12-29
I would install VNC, connect in with a VNC client and do what you need to do.

```
root@sam-server2:~# gedit /hlds/cstrike/addons/amxmodx/configs/users.ini &
``` 

Are you trying to edit the file and put it in background (with the &)?

---

### Post by endoglastic on 2009-12-29
> **Project PWNED said:**
> I would install VNC, connect in with a VNC client and do what you need to do.
 
```
root@sam-server2:~# gedit /hlds/cstrike/addons/amxmodx/configs/users.ini &
``` 
 
Are you trying to edit the file and put it in background (with the &)?
 
My brother told me to put the "&" because it creates it in a serparate window so thats why that is there. Yes i am trying to edit the file also which its done great at my house, but he windows doesn't seem to pop up when i ssh my bros with x11 and use the same command.

---

### Post by endoglastic on 2009-12-29
> **iponeverything said:**
> Ok, so you can account for the xming configuration on your bro's box. How about dozens of other mysterious happenings on a windows machine?
 
See if there is anything in the event logs or if xming generating a log.
 
xming configuration? all that needs to be done to my knowledge is make sure forwardx11 is forward in the config files for ssh. I think that is what you mean right?
 
And about the mysterious happenings on windows i really do not know where you are getting at? Because it does work on my external ip, but not his, and we both have the same config files because i created them.

---

### Post by Project PWNED on 2009-12-29
nano /hlds/cstrike/addons/amxmodx/configs/users.ini

Ctrl+O to save
Ctrl+X to exit

---

### Post by endoglastic on 2009-12-29
> **Project PWNED said:**
> nano /hlds/cstrike/addons/amxmodx/configs/users.ini
 
Ctrl+O to save
Ctrl+X to exit
 
Ok i am doing this and it wants to me save it as a different name, i hit ctrl+o, type in users.ini, and then it asks DO YOU WANT TO CHANGE TO DIFFERENT NAME, then type "n", then it just keeps going back to, WHAT DO YOU WANT TO SAVE THE FILE AS. Oh and is this the same thing as pico, it looks like it.

---

### Post by Project PWNED on 2009-12-29
ctrl + o, then hit enter, and ctrl + x to exit

---

### Post by endoglastic on 2009-12-29
Ok thanks that worked well, but i like it, but i prefer gedit more, do you know why it would not show up on my bros, but show up on mine, even though we have the same config for ssh. I connect to his and mine from my laptop using our external ips.

---

### Post by markp1989 on 2009-12-29
> **iponeverything said:**
> ```
"localhost:10.0".
```

When you ssh to server side do: 

```
ssh -X user@host
```

Or if the client and server are on the same host and you like the hash prompt, I would invoke bash with sudo.


is there any way to have sound forwarded over ssh along with x?

thanks mark

---

### Post by Project PWNED on 2009-12-29
I'm just a command line, kinda guy

---

### Post by iponeverything on 2009-12-29
> **markp1989 said:**
> is there any way to have sound forwarded over ssh along with x?

thanks mark

Unfortunately not. You can fire up Rhythmbox have it display remotely, but the music will still be pumped out of the local sound card.

---

### Post by endoglastic on 2010-01-02
[SOLVED] For some reason it works, i think it was because we had a port taken up that it needed to be used such as port 30, this could be by it would not pop up, but those errors are still there when it pops up because i think of some authorization thing, but yeah it works now so thanks for replies.

---

### Post by Nixblicker on 2010-01-21
Hey,

for the redirecting sound issue i would suggest using pulseaudio.
Stumbled upon it a couple of days, but must admit i haven't had time to play around with it yet. 
But it sounds really promising...
For more info, read [this]("http://ubuntuforums.org/archive/index.php/t-925659.html") or [that]("http://linuxundich.de/en/2009/02/sounds-mit-pulseaudio-umleiten/").

Hope it helps,

Cheers 
Nix

---

