---
title: "remote desktop to Windows"
date: 2006-03-20
forum: General Help
---

### Post by chicoselfs on 2006-03-20
Hi, i have my laptop with ubuntu but my desktop is with windows because of games and also JR. Media center for my music organization, i tried to use remote desktop in ubuntu to access Windows, but i have a problem, the keyboard don't work and it give me errors playing sound and image is in 8 bits, i configured my keyboard to PT and to 24 bits Image quality and to play sounds in remote computer but it still don't works, can someone help me? I tried also with Kubuntu but same results, i tried also put XP in my laptop and it worked great. Please help me i want to get free of windows on my laptop

---

### Post by MetalMusicAddict on 2006-03-20
Install A VNC server on your XP box. I used RealVNC. Some people also like TightVNC. Then with Ubuntu I can show you pretty easy how to do it.

---

### Post by chicoselfs on 2006-03-20
Ok already instaled ThightVNC now what do i have to do? Thanks in advance and for the replay :)

---

### Post by Adrian on 2006-03-20
[QUOTE=chicoselfs]Hi, i have my laptop with ubuntu but my desktop is with windows because of games and also JR. Media center for my music organization, i tried to use remote desktop in ubuntu to access Windows, but i have a problem, the keyboard don't work and it give me errors playing sound and image is in 8 bits, i configured my keyboard to PT and to 24 bits Image quality and to play sounds in remote computer but it still don't works, can someone help me? I tried also with Kubuntu but same results, i tried also put XP in my laptop and it worked great. Please help me i want to get free of windows on my laptop[/QUOTE]

Try this from a terminal:

```

rdesktop -f -a 24 -k pt 192.168.0.1

```

...and of course, change *192.168.0.1* to the IP of the remote machine (it was just used as an example).

This will launch rdesktop in fullscreen mode (because of the -f option). To exit full screen mode, press **ctrl-alt-enter**.

---

### Post by chicoselfs on 2006-03-21
Hi, it works know and thank you for your help but i still have a problem with sound, it won't play any sounds, i wan't to play sounds in the remote computer not the one with ubuntu, and the wallpaper of the remote don't show up, any clue?

---

### Post by Adrian on 2006-03-21
[QUOTE=chicoselfs]Hi, it works know and thank you for your help but i still have a problem with sound, it won't play any sounds, i wan't to play sounds in the remote computer not the one with ubuntu, and the wallpaper of the remote don't show up, any clue?[/QUOTE]

I have the same problem. I'm afraid that it cannot be solved using rdesktop, until a new version comes out. The Windows remote desktop client has an option for disabling sound redirection. rdesktop doesn't support that option yet, so the server always tries to send the sound to the remote machine.

Sometimes you can find ways to play sounds anyway. For instance, if you leave a winamp playlist on repeat, you can switch songs remotely. You can also pause the songs. However, if you stop the playlist and restarts it, the server will start sending the sound over the network.

---

### Post by chicoselfs on 2006-03-21
[QUOTE=Adrian]I have the same problem. I'm afraid that it cannot be solved using rdesktop, until a new version comes out. The Windows remote desktop client has an option for disabling sound redirection. rdesktop doesn't support that option yet, so the server always tries to send the sound to the remote machine.

Sometimes you can find ways to play sounds anyway. For instance, if you leave a winamp playlist on repeat, you can switch songs remotely. You can also pause the songs. However, if you stop the playlist and restarts it, the server will start sending the sound over the network.[/QUOTE]


Thanks, i was thinking that something was wrong with my computer, thank you for your answer, and other users as well

---

### Post by stokker on 2008-01-13
to get audio playback on remote computer  :  rdesktop -r sound:remote 192.168.0.xxx 

( see [http://vertito.blogspot.com/2007/09/rdesktop-remote-desktop-howto.html](http://vertito.blogspot.com/2007/09/rdesktop-remote-desktop-howto.html) )

---

