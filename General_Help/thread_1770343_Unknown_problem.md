---
title: "Unknown problem"
date: 2011-05-29
forum: General Help
---

### Post by Sapro on 2011-05-29
Hello, I wonder if anyone could shed some light on this problem I have.

I'm running a ubuntu lucid server and I am trying to run a game server that only has a windows exe through wine, this is not the problem. I am also trying to get it to execute through an apache based control panel.

I have configured everything on the apache panel, and it launches the game fine. But its being killed by: 
```

Error opening terminal: unknown
```

[FONT=Verdana]I don't get this error when I launch the server through SSH only via the apache panel. 

The panel is running as user www-data. I did notice one discrepency tho, when I echo TERM
in SSH it shows it set as xterm.

I have done the same thing in the command shell on webmin which I use to administrate most
of the server, and it comes back as dumb? im not sure if this might be it, as I set the SSH
to dumb to test if it gave the error, but it did not.

I have searched for an answer to no avail! if anyone could help it would be great!
[/FONT]

---

