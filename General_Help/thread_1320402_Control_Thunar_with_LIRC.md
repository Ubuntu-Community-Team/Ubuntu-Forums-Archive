---
title: "Control Thunar with LIRC"
date: 2009-11-09
forum: General Help
---

### Post by dethredic on 2009-11-09
Is possible to make LIRC control thunar? (like the arrow keys do: move from 1 file to the next). I also want the back button to up 1 directory.

I would also like to make one of my remote buttons send "alt tab".

thanks in advance

---

### Post by dethredic on 2009-11-10
Ok, I got some stuff, but there are still some problems:

stuff in bold isn't working.
> begin
	prog = irxevent
	button = Aspect
	config = Key f MPlayer
end
begin
	prog = 
	button = Power
	config = 
end
begin
	prog = 
	button = Radio
	config = 
end
begin
	prog = irexec
	button = Music
	config = mpc toggle
end
begin
	prog = irexec
	button = Videos
	config = thunar
end
begin
	prog = irxevent
	button = Pause
	config = Key p MPlayer
end
begin
	prog = irxevent
	button = Play
	config = Key p MPlayer
end
begin
	prog = irxevent
	button = Stop
	config = Key Enter MPlayer
end
begin
	prog = 
	button = Forward
	config = 
end
begin
	prog = 
	button = Skip
	config = 
end
begin
	prog = 
	button = Replay
	config = 
end
begin
	prog = 
	button = Rewind
	config = 
end
[b]begin
	prog = irxevent
	button = OK
	config = Key Enter CurrentWindow
end
[/b]
begin
	prog = irxevent
	button = Up
	config = Key Up CurrentWindow
end
begin
	prog = irxevent
	button = Down
	config = Key Down CurrentWindow
end
begin
	prog = irxevent
	button = Left
	config = Key Left CurrentWindow
end
begin
	prog = irxevent
	button = Right
	config = Key Right CurrentWindow
end
begin
	prog = 
	button = Back
	config = 
end
begin
	prog = irxevent
	button = VolUp
	config = Key 0 MPlayer
end
begin
	prog = irxevent
	button = VolDown
	config = Key 9 MPlayer
end
begin
	prog = irxevent
	button = Mute
	config = Key m MPlayer
end
begin
	prog = 
	button = ChanUp
	config = 
end
begin
	prog = 
	button = ChanDown
	config = 
end
[b]begin
	prog = irxevent
	button = Home
	config = Key alt-Tab RootWindow
end[/b]
begin
	prog = irxevent
	button = More
	config = Key v MPlayer
end
begin
	prog = 
	button = Red
	config = 
end
begin
	prog = 
	button = Green
	config = 
end
begin
	prog = 
	button = Yellow
	config = 
end
begin
	prog = 
	button = Blue
	config = 
end

---

### Post by deankovell on 2009-12-25
I am trying to accomplish the same thing. Did you ever get anywhere with it?

---

