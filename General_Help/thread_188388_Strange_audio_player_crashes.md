---
title: "Strange audio player crashes"
date: 2006-06-04
forum: General Help
---

### Post by medisyn on 2006-06-04
Ok Just finshed an install of Dapper and its acutally pretty awesome, but I am having some issues.

1. Ok this one is wierd and I have little idea how to fix it. When I open amarok or listen or banshee they work fine for a while and then the whole program window will fade black (is this normal for a crashed program???) and the program will just crash (audio will continue to play until the song ends). Is this becuase the mp3's are on NTFS partitions? I notice it happens when I change songs quickly with the multimedia keys or when I do drastic changes to the playlists. Also Amarok is slow in changing songs...
2.Randomly came back to my computer and found the system was compleatly locked up. (screen was black and the sysem wasnt responding...) I am guessing this is becuase of an issue with the 3d screen saver, compiz and my 9500pro. I turned off the screen saver for now, I havnt had a complete system lock like that in a good while...
3. Is it still impossible to safely write to ntfs drives? becuase this really kills tasks between OS's.
I understand that 6.06 is very new and out the box it is the best distro I have ever used hands down. The new install method is very awesome! 
I got a network printer working very easly and my extrnal hard drive works perfectly. I installed it on a buddies computer but lack of sound card susport he ditched it (creative x-fi.). He is a heavy music listener so no mp3= not the OS for him.

---

### Post by medisyn on 2006-06-04
Ok just had Listen crash again on me so I opened XMMS, minimised it and then brought it back up and the main window is gone! Man what is going on here?! ](*,)

EDIT: Oh ok it just doesnt stay attached when maximised. Why does it behave like that?

---

### Post by medisyn on 2006-06-04
am i the only guy with these problems? (shameless bump...)

---

### Post by blackjack6.21.91 on 2006-06-04
No.  I've had the fade to black thing happen on me before while I was gaming.  But it doesn't happen very often.  I think it may be because of what my friend calls a "crappy algorithm": your computer becomes idle if you haven't used your mouse in "x mins", but you can tap on your keyboard all you'd like.

I don't know why XMMS is like that.  Try beep media player.

---

### Post by smsmith050 on 2006-06-04
I have had a similar crash. I left the computer idle with the terminal server client running. When I returned the screen was fading to black. I moved the mouse. The screen came back. I was unable to select anything with the mouse. The pointer still moved. It appeared that the terminal server client had taken the focus. The mouse and keyboard had only limited functionallity in the terminal server client window. I had to kill the x-server. ctrl-alt-Backspace. 

steve

---

### Post by medisyn on 2006-06-04
[QUOTE=blackjack6.21.91]No.  I've had the fade to black thing happen on me before while I was gaming.  But it doesn't happen very often.  I think it may be because of what my friend calls a "crappy algorithm": your computer becomes idle if you haven't used your mouse in "x mins", but you can tap on your keyboard all you'd like.

I don't know why XMMS is like that.  Try beep media player.[/QUOTE]
Ok but the fade to black is _just_ the listen/amarok window the crash happens so often ill just get a screen shot:
[http://img212.imageshack.us/img212/7958/screenshot1fd.png](http://img212.imageshack.us/img212/7958/screenshot1fd.png)
All it took for me to get it to crash is to hit the next key on my keyboard a few times and it locked up hardcore.
In windows I am a foobar2000 user and I cant stand to go back to a primitive winamp2 clone. I would like to be able to use at least listen. :KS

---

### Post by medisyn on 2006-06-04
I spend the past hour trying to figure out why its crashing and I am getting noware hahah. Am I the only guy who has ran into this problem?

---

### Post by RAOF on 2006-06-04
For your writting to NTFS needs:
[NTFS-FUSE](https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28ntfs%29)
Those NTFS drivers are **quite** safe - unlike the old drivers which regularly killed drives.  Although I don't remember any reports of filesystem corruption with them (and they're written with a "saftey first" philosopy), they're not heavily tested yet.  Hence the warning.

With compiz, it is ususal for unresponsive programs to slowly fade-to-black (or, more accurately, to grayscale).  I've got no ideas about the cause of that, though.  Does your ~/.xsession-errors contain any relevant error messages?  What happens if you run Banshee (for example) from the console & get it to crash like that?  Error messages are **really** useful ;)

---

### Post by medisyn on 2006-06-05
hey thanks for the NTFS link!
Anyways I am sorry I am kinda a noob but can you tell me where to find that error log and ill get it to crash again and post my findings. I have been using rhythmbox for a bit and its working without crashing... I see it has an OSD plugin to display what songs are playing but the link doesnt work ](*,)  to get it.

---

### Post by Ahzwon on 2006-06-28
[QUOTE=smsmith050]I have had a similar crash. I left the computer idle with the terminal server client running. When I returned the screen was fading to black. I moved the mouse. The screen came back. I was unable to select anything with the mouse. The pointer still moved. It appeared that the terminal server client had taken the focus. The mouse and keyboard had only limited functionallity in the terminal server client window. I had to kill the x-server. ctrl-alt-Backspace. [/QUOTE]

Hi!
I'm getting the same thing. All I have to do is leave the terminal client up and running, lock my computer (I use the blank screensaver, password protected), or just let the timer go until the screensaver comes on, and voila! Same thing. Mouse moves, but can't click on anything. Thankfully the keyboard still works, but I can't even get the menus (Applications, etc.) to properly respond so I can enact a nice clean logout (of Ubuntu, that is...)

-Roger A

Dapper 6.06 on a Dell Latitude D620

---

