---
title: "x11vnc problems"
date: 2009-11-23
forum: General Help
---

### Post by 748Snowman on 2009-11-23
So I got vnc installed and when I try to set the pass word I get an error telling me the file isn't there.

when I tried to change the pass or add a pass it would tell me to install 
vnc-common 
so I did and I'm still having the same issues. Might anyone have an incite into this?

Thx

---

### Post by krunge on 2009-11-23
> So I got vnc installed and when I try to set the pass word I get an error telling me the file isn't there.

when I tried to change the pass or add a pass it would tell me to install 
vnc-common 
so I did and I'm still having the same issues. Might anyone have an incite into this?

Thx
Could you post the messages you are seeing? And the names of the packages you installed.

---

### Post by 748Snowman on 2009-11-24
I installed x11vnc than installed vnc-common, due to when I typed vncpasswd ~/.vnc/passwd 

I get the password:
then verify

and it responds with "couldn't open /home/"name"/.vnc/passwd for writing".

I'm running Hardy Heron LTS

---

### Post by 748Snowman on 2009-11-25
bamp :D

Still stuck on this if anyone might know what I need to do, and I'm pretty new to Linux.

---

### Post by krunge on 2009-11-25
> Still stuck on this if anyone might know what I need to do, and I'm pretty new to Linux.
Learn about the "ls -l" command ("man ls") and run it on the file you mention above and its containing directory.

Sounds like you are having a basic file permission problem to me (look for beginner unix tutorials on the web.)

---

