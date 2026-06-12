---
title: "Start a GUI application on remote computer using ssh"
date: 2011-08-18
forum: General Help
---

### Post by electriceddy on 2011-08-18
Hi All,

I forgot to run a GUI process on a remote computer.  I need to run the application as if I was at the computer i.e the application needs to open on the desktop on the remote computer.

I can connect to the computer through an ssh tunnel via another computer at the remote site and run non GUI based processes using Screen or bring some GUI programs to the computer I'm working from using the ssh -X option, however, this is not what I'm looking to do.

On Windows I used to use a program from sysinterns called PsExec which would let me start applications such as Word on the remote computer and I'm hoping that there is something similar on Linux.

Appreciate any help.

Thanks 

Patrick

---

### Post by Lars Noodén on 2011-08-18
Log into the remote machine and then set the display to be that machine:

```

export DISPLAY=:0.0

```

Then any graphical programs you run there after will be displayed on the remote machine.

---

### Post by electriceddy on 2011-08-18
You're a star! Thanks a million that worked perfectly.
 
Patrick

---

### Post by electriceddy on 2011-08-18
One quick related one, how do reset the display output to normal.  I'm not quite sure what the 0.0 relates to so is there a number for the connecting screen or a way to retrieve it?

Patrick.

---

### Post by WorMzy on 2011-08-18
> **electriceddy said:**
> One quick related one, how do reset the display output to normal.

Not sure what you mean by that. You can unset the DISPLAY value by running:
```
unset DISPLAY
```

> I'm not quite sure what the 0.0 relates to so is there a number for the connecting screen or a way to retrieve it?

As I understand it:
:0 = the first X server
.0 = the first screen on the X server

So :0.0 = the first screen on the first X server.

If you had multiple X servers running, you could choose to open the GUI apps on the second server with:

```
export DISPLAY=:1.0
```

etc.

---

