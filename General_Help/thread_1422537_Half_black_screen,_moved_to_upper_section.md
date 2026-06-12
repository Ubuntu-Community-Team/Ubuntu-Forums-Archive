---
title: "Half black screen, moved to upper section"
date: 2010-03-05
forum: General Help
---

### Post by Jirinovak on 2010-03-05
[FONT=Arial][SIZE=2]Hi,
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]My little girl played with my keyboard and mouse and moved my entire screen to upper section. I tried everything, and can't figure it out how to bring it down. I see black color trough half of my display. I can go blindly in upper section without being able to see, and from time to time click the shut down bottom. [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Do you any of you have idea how to fix it? Ubuntu rocks, I love it, very stable, solid rock . . . I twill never use anything else.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Thank you,[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Jiri[/SIZE][/FONT]

---

### Post by asmoore82 on 2010-03-05
You could try this:

Open the "Run" prompt, Alt+F2 by default, and ```
xrandr --auto
```

I would guess that it's going to take a more complex xrandr line to actually fix it.
Something like: ```
xrandr --output default --mode 1024x768
```

---

