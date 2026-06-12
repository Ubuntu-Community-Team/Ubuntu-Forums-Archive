---
title: "Lost panel after upgrading to 10.04"
date: 2010-05-01
forum: General Help
---

### Post by TentacleJoe on 2010-05-01
Hi Guys,

Just upgraded to 10.04 and everything was working fine until my Chrome browser crashed and then I lost my top panel. I can't seem to get it back to it's default state.

I've tried a few things that gives me the panel back without maximus running but when I restart the panel doesn't return. Actually Maximus is running but it's not maximizing anything.

If somebody can point me in the right direction to get the panel back to it's default state I would really appreciate that. 

PS: The panel and maximus work fine when creating new users.

Thanks!

Joey

---

### Post by brunocarv on 2010-05-01
Hey,

I have the same problem. I very unhappy about the update!!
I hope someone can solve this problem...  I'm not a very experiencied user and I dont have any idea of what to do.

I really want solve this.

thanks
Bruno

---

### Post by brunocarv on 2010-05-01
I forgot to say: someone know to to undo the update do ubuntu10?

thanks

ps: sorry about my english, I hope it is ok

---

### Post by TentacleJoe on 2010-05-01
I discovered something interesting as I was tracing my steps back to see if I had changed anything. The only thing I could think of was that I changed the effects in the Appearance properties. So I went in and changed them back and that causes my close / minimize / maximize buttons to reappear which I didn't notice they were gone before and then I am able to maximize as long as I have the panel up. This works until I log out. When I log back in the panel isn't there. So I have to start the panel manually then go into the effects properties and switch it from what ever setting it is on to a different one and that  causes my close / minimize / maximize buttons to reappear and then I'm able to maximize again. Kind of weird?

Somebody in another forum suggested the following which I will post here in case it helps somebody else.  I haven't tried this yet but I'll let you know when I do:

> And one thing I'd try to actually fix the problem... in a terminal, run: "sudo dpkg-reconfigure maximus gnome-panel" or "sudo dpkg-reconfigure --force maximus gnome-panel" to "reinstall" the relevant packages.

---

### Post by TentacleJoe on 2010-05-03
I tried that suggestion above and it didn't work.

---

### Post by WorMzy on 2010-05-03
To reset the panels, in a terminal write:

```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```

NOTE: This will completely reset your panels to the default configuration, they will look the same as if you'd done a fresh install.

---

### Post by augusto on 2010-05-03
Awesome, thanks Wormzy.

---

### Post by zirikkanen on 2010-05-06
Great! It worked for me also!! 
I had to reboot at the end.

Thank you very much!

Z.

---

### Post by TentacleJoe on 2010-05-13
Hey thanks Wormzy. I actually "fixed" it a different way. I discovered compiz wasn't running so I added that to the startup and that fixed everything for me.

---

### Post by Iowan on 2010-05-13
Glad you found a solution...
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?  :)

---

### Post by TentacleJoe on 2010-05-14
Thanks. I didn't know I had to mark it =)

---

### Post by moondoggy2 on 2010-05-15
Thanks guys.  This saved my day!!

---

