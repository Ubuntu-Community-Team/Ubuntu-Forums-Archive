---
title: "remote computing"
date: 2006-04-25
forum: General Help
---

### Post by dhjohnson on 2006-04-25
Hello.

I need a way to connect to my machine at home from work.  I've been using VNC over SSH which worked very well, but I now have a new problem:  I've recently gotten married and moved in with my new wife.  When she starts another session using "New Login", I am then unable to remotely view my already running session.  I'm just now reading about the chvt command, but the ideal solution is for both of us to be able to use the computer at the same time (one remotely and the other locally).

Thanks in advance for your help.

---

### Post by jazzmuzik on 2006-04-25
I haven't tried vnc over ssh, but just today I tried sshfs and it works. Search on sshfs for the link to the instructions.

---

### Post by dhjohnson on 2006-04-25
[QUOTE=jazzmuzik]I haven't tried vnc over ssh, but just today I tried sshfs and it works. Search on sshfs for the link to the instructions.[/QUOTE]

This didn't really answer my question.

---

### Post by jazzmuzik on 2006-04-25
My suggestion was to look into sshfs because you can run multiple sessions at the same time.

---

### Post by dhjohnson on 2006-04-26
Bump.

---

### Post by dhjohnson on 2006-05-12
Bump.

---

### Post by ZylGadis on 2006-05-12
I am not sure the "New Login" option keeps your old session running. Try looking into that. If all else fails, you can always start another X server (there is a howto somewhere in the forums), and have your wife use the one at ctrl+alt+f7 while you remotely use the one at ctrl+alt+f8. I am quite sure that you can have more than one simultaneous session on an X server, though.

---

### Post by steve.horsley on 2006-05-12
Which VNC server are you using? 

I thought that most of them create a new X desktop for the remote user rather than mirriring the existing X desktop. Woud this behaviour do for you?

---

