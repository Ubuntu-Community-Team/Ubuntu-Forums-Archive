---
title: "sudo: unable to resolve host username"
date: 2010-11-26
forum: General Help
---

### Post by Roman10 on 2010-11-26
Good morning to all. 

When I try to launch something from terminal, it shows this error. I have also read previous topics on this issue, but I still have not fix this.

gksudo gedit /etc/hosts

> 
127.0.0.1	localhost
127.0.1.1	matt-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


My computer always had this name and I never had concerns related to his name. So, what's wrong now?

---

### Post by dino99 on 2010-11-26
here is mine (first lines)



127.0.0.1	localhost
::1	localhost6	oem-desktop
127.0.1.1	oem-desktop


note: user=oem in my case

---

### Post by Roman10 on 2010-11-26
> **dino99 said:**
> here is mine (first lines)



127.0.0.1	localhost
::1	localhost6	oem-desktop
127.0.1.1	oem-desktop


note: user=oem in my case


Hi dino99, thank you fore reply. I'm not sure that I've understand what you are saying to me. If you are saying that I must change this

> 

::1 localhost ip6-localhost ip6-loopback



with this

> 

localhost6 matt-laptop



I still have the problem (even if seems that with this settings I speed up launching commands from terminal)... :(

---

### Post by wet-willy on 2010-11-26
Your post is a little confusing...
Do you get this /etc/hosts file displayed every time you try to launch "something" from the terminal, or does the terminal just open the file in CLI mode rather than GUI mode when you asked to open gedit as superuser?
What exactly is the response when you try to launch nautilus?

Anyway, I don't see what the hype is with this gksudo thing, especially when there is no package in repositories by that name, there is a gksu.

I always just do:
sudo gedit /etc/hosts
And the GUI front end of gedit opens the file as root.
In Debian, I issue command: **su -** to swith to root to get a GUI as root, a simple **su** to root returns a dummy response when asking to open a GUI app as root.

```
127.0.0.1	ubuntu	localhost.localdomain	localhost
::1	ubuntu	localhost6.localdomain6	localhost6
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by dino99 on 2010-11-26
look at your first post: you have 2 lines, mine have 3

so it miss:

 ::1 localhost6 matt-laptop ( insert it between your 2 lines)

--> make it like that:

127.0.0.1 localhost
::1 localhost6 matt-laptop
127.0.1.1 matt-laptop

---

### Post by Roman10 on 2010-11-26
> **wet-willy said:**
> Your post is a little confusing...
Do you get this /etc/hosts file displayed every time you try to launch "something" from the terminal, or does the terminal just open the file in CLI mode rather than GUI mode when you asked to open gedit as superuser?
What exactly is the response when you try to launch nautilus?


Hi **wet-willy**, thank you for reply. When I try to launch nautilus or others kinds of application from terminal as sudo (or similar), I get the problem in the topic. However, it seems that I don't have any problems with applications as I can work normally with them. The problem is just in this row that I get after all my terminal commands as sudo. 

I've posted my /etc/hosts/ file because I thought that the problem could be here, in mine config and maybe somebody, with just a look, could solve quickly this problem.

I wrote gksudo because normally I use it to launch graphical applications. Clearly, now it's a mistake, it's like a mine custom...

**dino99**, I've tried to change the settings in that way, but it still not fixes the problems.

---

### Post by wet-willy on 2010-11-26
> However, it seems that I don't have any problems with applications as I can work normally with them. The problem is just in this row that I get after all my terminal commands as sudo.
Hmmm!
If I read this correctly, there really is no 'actual' issue here, can still use the app as root, just concerned about the terminal output....
You can't find a girl/woman to worry about?
Or is the terminal output dilemma less stressful thus more attractive?

---

### Post by Roman10 on 2010-11-26
> **wet-willy said:**
> Hmmm!
If I read this correctly, there really is no 'actual' issue here, can still use the app as root, just concerned about the terminal output....
You can't find a girl/woman to worry about?
Or is the terminal output dilemma less stressful thus more attractive?

I can assure you that this issue doesn't disturb my sleep :)

Nonetheless, it's always a good thing try to understand if this issue could give me problems in the future or in others things that I don't have already tested.

---

### Post by wet-willy on 2010-11-26
My Debians always do this, I don't have sudo installed in Debs, I issue command: **su -** to get super(duper)user prompt and type: **kate /etc/rc.local**, (KDE), then about ten to thirty errors display, then kate appears, I do my thing, more errors ripping up the terminal with every action, I click "Save" and close, the terminal hangs, I hit the return key and the prompt is back looking like a dog sitting at your bekkin' call with it's tongue waggling.
I don't see a problem....!

---

