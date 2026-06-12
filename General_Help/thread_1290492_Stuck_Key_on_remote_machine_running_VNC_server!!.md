---
title: "Stuck Key on remote machine running VNC server!!"
date: 2009-10-13
forum: General Help
---

### Post by makaveli789 on 2009-10-13
I have a x11vnc installed and running on my Ubuntu 9.04 machine that I am trying to VNC into. I also have a ssh server installed and running. So here is the scenario:

-I ssh in to my server using my Vista desktop with Cygwin
-launch x11vnc from the terminal (i normally turn it off after I finish every vnc session)
-then I run my VNC viewer, connect, enter password, connects fine and loads the dialog prompt for unlocking the user logged in
-as I enter the password I discover that the login textbox is rapidly updating with extra characters on the end and so my authentication fails

I can see from 'leave user a message' feature that the character is 'P'. I believe something has fallen on my keybaord on my remote machine and is keeping the key pushed down. I have ssh access to my machine so is there anything I can do like disabling the local keyboard??

---

### Post by StuartN on 2009-10-13
> **makaveli789 said:**
> I believe something has fallen on my keybaord on my remote machine and is keeping the key pushed down. I have ssh access to my machine so is there anything I can do like disabling the local keyboard??

If you are really lucky then simply ejecting your CD tray will dislodge (or frighten) whatever has fallen on your keyboard. At last, the motorized eject has a purpose in this world!

---

### Post by makaveli789 on 2009-10-13
It's a desktop machine at work. And the tower is on the floor. I wanted to do some work before tomorrow. I'm screwed lol

---

### Post by StuartN on 2009-10-13
> **makaveli789 said:**
> It's a desktop machine at work. And the tower is on the floor. I wanted to do some work before tomorrow. I'm screwed lol

If you get root access (my SSH is not set up to allow root) then you could try this bit of wading through the system: [http://ubuntuforums.org/showthread.php?p=4575032](http://ubuntuforums.org/showthread.php?p=4575032)

---

### Post by makaveli789 on 2009-10-13
> adding "i8042.nokbd" to the kernel boot line works

I guess that requires a reboot? I have a lot of windows open in my current ubuntu session so a restart at this point would be a no-go for me. Although that was a good find so kudos to you for pulling that link out. I will keep it in mind should as a possibility for next time.

---

### Post by krunge on 2009-10-13
You may be experiencing this Xorg bug. Have you seen this thread?

[INDENT][http://ubuntuforums.org/showthread.php?t=1125694&highlight=x11vnc+key+repeat&page=4]("http://ubuntuforums.org/showthread.php?t=1125694&highlight=x11vnc+key+repeat&page=4")[/INDENT]

A workaround is in post #32 of it.  It is: "x11vnc -repeat ..."

To avoid restarting your current X session, using "x11vnc -clear_keys" may
'unstick' the key.  But if you restart X, you should only need "-repeat".

---

### Post by makaveli789 on 2009-11-13
[Just a heads up to those having similar problem with x11vnc]

Yes Krunge,  I was in fact experiencing the very same issue. I didn't give your suggestion a try for my issue in this thread because I just gave up in the end and forgot about it. However, I had the issue again today. Running,

```
**-repeat -clear_keys**
```eliminates the issue for me. \\:D/

---

