---
title: "Unknown Program?"
date: 2009-09-15
forum: General Help
---

### Post by blunderhawk on 2009-09-15
Sometimes when I Shut down I get a message saying that there is a program labeled "Unknown" that is not turning off. The pop up further asks me if I want to log off anyway, or wait or cancel.

I tried clicking on this program to get more info. but it doesn't give me any more info. except for it's name..which is, as stated above, of little use >_>

Being a long time Windows user, when something weird happens, it's usually bad news.

I know I'm probably jumping to conclusions, but if I don't know what the heck this thing is, then I can't help but assume the worst.

I'm running 9.04 and I also have a Windows partition on my Hard drive. I haven't use the windows partition though. I keep my system updated too. Besides that I can't really think of anything more to say. If you all need any info. let me know.

It would be nice to know if this is just a bug in the operating system and that others have been having the same problem. But knowing what they heck this is is and getting rid of it will work just as fine.

Thanks in advance!

---

### Post by Yannick Le Saint kyncani on 2009-09-15
You could log into a console (ctrl+alt+f1) and see running processes from there.

---

### Post by blunderhawk on 2009-09-15
Pardon me if this is a stupid question (I'm new), but how do I see the running processes? I used the Keyboard command you posted and it prompted my username and password. I entered it in and then I'm at a loss on what to do from there.

---

### Post by Yannick Le Saint kyncani on 2009-09-15
ps -edf | grep `whoami`

---

### Post by uylug on 2009-09-15
```
ps aux
```
```
ps ux
```

---

### Post by blunderhawk on 2009-09-17
Alright so I got the message again and I used the "PS UX" code. I assumed that all 3 codes did the same thing so I just used the easiest one to type in.

I took some pictures too so hopefully that will help. 

Here's the message I keep getting when I log out.

[http://i26.tinypic.com/1z6bpfn.png](http://i26.tinypic.com/1z6bpfn.png)

When I go to system monitor and look at the processes, these are what are running at the time of the mysterious message.

[http://i28.tinypic.com/20gcnbl.png](http://i28.tinypic.com/20gcnbl.png)
[http://i27.tinypic.com/1269rg6.png](http://i27.tinypic.com/1269rg6.png)
[http://i27.tinypic.com/208trbp.png](http://i27.tinypic.com/208trbp.png)

Now when I typed the "PS UX" command, here is what I got. Some of the info. got cut out and I don't know how to view it. Any ideas? Would setting my resolution setting fix the issue?

[http://i26.tinypic.com/2n8syzb.jpg](http://i26.tinypic.com/2n8syzb.jpg)
[http://i26.tinypic.com/2w20vhc.jpg](http://i26.tinypic.com/2w20vhc.jpg)
[http://i26.tinypic.com/3588dpy.jpg](http://i26.tinypic.com/3588dpy.jpg)
[http://i32.tinypic.com/2iu2pvq.jpg](http://i32.tinypic.com/2iu2pvq.jpg)


So, any ideas for what this unknown program is? Is anyone at all having this same issue!? This is just so weird, I never had this with 8.04

---

### Post by Vaphell on 2009-09-17
hm, it's much easier to copy-paste the output o_O

---

### Post by blunderhawk on 2009-09-20
I tried copying and pasting that that didn't work. I used CTRL+C, is there some other way I can copy and past besides that?

---

### Post by falconindy on 2009-09-20
If you want to copy from a terminal, you need to use ctrl+shift+c. ctrl+c is already reserved for something else.

---

### Post by maverick340 on 2010-01-14
[http://ubuntuforums.org/showthread.php?t=1062579&highlight=unknown+program+shut&page=2](http://ubuntuforums.org/showthread.php?t=1062579&highlight=unknown+program+shut&page=2)
I posted some info here

---

