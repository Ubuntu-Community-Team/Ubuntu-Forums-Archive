---
title: "Do I have to reinstall?"
date: 2006-03-22
forum: General Help
---

### Post by Gosta on 2006-03-22
Hi, I'm using ubuntu and now I have done something that messed up the installation. If I start the computer as usual the log-in screen appears but when I have entred my username and my pass the screen goes brown and nothing else but the mouse pointer. If I try to use the recovery-mode and log in as root then it also stops and I cannot do anything.
What is the best to do? New install or can I do someting else?
I am not sure what I did to make things like this. I had resently installed ubuntu and I was configuring several different things.

---

### Post by Mustard on 2006-03-22
Can you get to a command line with the ctrl + alt + f1 keys?

If so it could be a problem with your .ICEauthority or .Xauthority files having the wrong ownership.

Mine look like this when I do this command...

```
mustard@slave:~$ ls -al .*authority
-rw-------  1 mustard mustard 5137 2006-03-23 11:37 .ICEauthority
-rw-------  1 mustard mustard  165 2006-03-23 09:48 .Xauthority

```

Try this command yourself and post the output.  I'm expecting that the files will be owned by root, rather than the user.

---

### Post by Gosta on 2006-03-22
No, the screen goes completely blank if I try to get to the command line.

---

### Post by Mustard on 2006-03-22
[QUOTE=Gosta]No, the screen goes completely blank if I try to get to the command line.[/QUOTE]

Hmmm..ok.  It might be unrelated to the above issue then.

What were you specifically configuring when the problem occured?

When you log in in recovery mode and its 'stops' do you receive an error message?

---

### Post by Gosta on 2006-03-22
Yes, I dont understand much of the error message but i might have something to do with my network card. But since I cant get to any command line I dont know how to edit my settings.

---

### Post by az on 2006-03-22
[QUOTE=Gosta] If I try to use the recovery-mode and log in as root then it also stops and I cannot do anything.[/QUOTE]
What do youmean log in as root?

Did you set a root password?  Because recovery mode is supposed to dump you into a shell as root.

If you set a root password, you need to type it in to log in.  What exactly happens?

---

### Post by Gosta on 2006-03-22
I have a root password and I typed it in, and then after som loading I get the error message.

---

### Post by Mustard on 2006-03-22
[QUOTE=Gosta]I have a root password and I typed it in, and then after som loading I get the error message.[/QUOTE]

That error message is the essential clue we need to proceed.  I would get a pen and paper out now and write it down.  Until then its going to be very hard to know which way to go from here.

---

### Post by Gosta on 2006-03-22
Ok, but I dont want to reboot my computer right now. I will do it later. Thanks anyway.

---

