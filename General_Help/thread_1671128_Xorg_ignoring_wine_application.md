---
title: "Xorg ignoring wine application"
date: 2011-01-19
forum: General Help
---

### Post by J V on 2011-01-19
A wine application is behaving very strangely.


  While rendering correctly, Xorg isn't picking up on it's existence,  and because of this the game only refreshes it's image when another  application requests that portion of the screen to be updated.


  For example, I will get maximum framerate if I move the window, or go  into the compiz cube, while placing a terminal with top running in it  behind the game will make that portion of the screen render at 3 fps (In  the video I will link it's running top -d 1.0 hence the 1 fps) whereas a quickly updating window shows the game at a more reasonable framerate.


  In the [video]("http://www.speedyshare.com/files/26361066/ao-render-framerate-bug.ogv") I have uploaded you can see this strange behavior, as the output from the game and the top combine to basically split the game between fast fps and slow fps in real-time.
  
[LIST]
[*][Video of Xorg/wine issue]("http://www.speedyshare.com/files/26361066/ao-render-framerate-bug.ogv") (AFAIK can only be opened in totem and VLC, recordmydesktop is bugged)
[*][Wine bug report]("http://bugs.winehq.org/show_bug.cgi?id=25821")
[/LIST]
    Does anyone know how to fix this problem? Quick xorg config file?  Recompile wine? I'll settle for a cheap trick (Other than putting a  looping terminal behind the game every time, that really drains CPU)


I have this stuck on stackexchange too...

Edit: Reports say that compiling 1.2.2 will fix this, [SOLVED]

---

