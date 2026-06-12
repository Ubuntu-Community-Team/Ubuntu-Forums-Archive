---
title: "Switch X display over SSH"
date: 2009-09-19
forum: General Help
---

### Post by zephyrcat on 2009-09-19
I can successfully connect to my machine via SSH. I am now trying to access it graphically through SSH. When I login via SSH and execute startx &, a window pops up showing my machine, but not the display that X is running on.

How can I switch to the correct display over SSH? (Ctrl+alt+F-something changes the display on the local machine.)

---

### Post by Bachstelze on 2009-09-19
You want VNC, not SSH.

---

### Post by Slim Odds on 2009-09-19
Check the SSH options -X and -Y

Then you can run X apps via SSH

---

### Post by nothingspecial on 2009-09-19
```
ssh -X user@ip
```

It has to be a capital X

Now just type the command to launch the app you want to run - nautilus, firefox, deluge, whatever

---

### Post by zephyrcat on 2009-09-19
I know VNC would be another option, but I already have SSH set up, so I want to try it out.

I am running SSH with the -X option and I have enabled X in the SSH configuration:
```

X11Forwarding yes
```

When I just type the application name, I get this error:
```

X11 connection rejected because of wrong authentication.
Could not parse arguments: Cannot open display:
```

---

### Post by zephyrcat on 2009-09-20
Anyone?

---

