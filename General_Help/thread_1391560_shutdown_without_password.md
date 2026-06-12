---
title: "shutdown without password"
date: 2010-01-26
forum: General Help
---

### Post by ardvark on 2010-01-26
I've been trying to get my UPS to shutdown the PC on low battery. Through some help it was determined that Gnome-Power-Manager is running under my user not root. So I've been trying to set up /etc/sudoers with visudo to get the shutdown command to execute under my user.

I've tried    (user) (host)=(root)NOPASSWD: /sbin/shutdown
      and     (user)    ALL=NOPASSWD: /sbin/shutdown

](*,)And it still says I need to be root to shutdown. Is shutdown a special command that you cannot fix this way? If this isn't going to work, how would Gnome-Power-Manager ever function properly?

---

### Post by raktarok on 2010-01-26
Hi,

Just try this line:
```

<your_user_name> ALL=(root) NOPASSWD: <your_command>
```

without the brackets, of course.

Now you can do **sudo <your_command>** and you won't be asked for password. Note that you still need to use sudo. Starting the command without sudo won't work. This probably was the problem with the lines you are using...

I don't understand what exactly you are trying to do though. Is the gnome-power-manager supposed to shutdown the computer once the battery is low and its not doing that for you? If this is the case, I don't think the above lines will make any difference - its probably a problem with gnome-power-manager itself.

---

### Post by ardvark on 2010-01-27
Well, I'm not sure where the problem is. There's an option under power manager if you have a UPS on your PC, it will monitor it and auto shutdown when the battery gets low during a power outage. This was a suggestion from someone, that since Gnome-Power-Manager's process is under my user instead of root that if it issues a shutdown command, it won't work because it's not root. It would make more sense to me that a program like Power Manager was running under root. This fix was a try to get my user to be able to shutdown without being root or with a password. If someone has a better fix, great. I tried searching for this but came up with nothing.

---

### Post by t4thfavor on 2010-01-27
If it's an APC ups, you can install apcupsd. It works well.

---

### Post by ardvark on 2010-01-27
It's a Trip-Lite Internet550U connected with a USB. Trip-Lite actually had some Linux software (Fedora & Suse RPM's) but it's only written for a serial connection. Of course I didn't know that when I bought it...

I had some bad experiences with APC products a few years ago. Hopefully they've improved since then.

I was going to pose this problem on the Gnome forum, but looking through that forum it doesn't look like much is being answered.

---

