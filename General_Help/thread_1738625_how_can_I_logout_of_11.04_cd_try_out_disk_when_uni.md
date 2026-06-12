---
title: "how can I logout of 11.04 cd try out disk when unity boots up"
date: 2011-04-25
forum: General Help
---

### Post by rocket777 on 2011-04-25
How can I logout of the 11.04 cd (32 bit intel version) when it starts up in Unity?](*,)

I'm looking to solve some issues by checking out 11.04 and unity just slows me down.

When I boot up the cd, sometimes I get stuck in unity, sometimes it starts up in gnome. This seems to be a random timing issue related to troubles with my particular graphics adapter. Anyway, that's what I trying to resolve and unity just gets in the way.

The problem is when in unity, I can't find any way to logout, it's not in the shutdown menu.

I need to logout and in to change my desktop from unity to classic. So, where's the logout in the cd trial version of unity?

---

### Post by conradin on 2011-04-25
press ctrl+alt+F4
```

sudo pkill unity

```
kill all that gui BS. Now you have a terminal session. What else do you want?

---

### Post by rocket777 on 2011-04-25
Is there a simple command to run gnome at that point? Is there a way to force the system to recheck what displays are attached?

Any ideas why I don't get a consistent start up? 

Is it a problem in unity, or is unity supposed to come up only when there's a small display, and when more than some set value for screen resolution, it comes up in gnome? Or does unity fail and then gnome comes up?

If that can be understood, perhaps it will point to the problem I have getting both my graphics adapters going at the same time - the real problem I'm trying to resolve. I think the two issues could be related. Especially since sometimes the ubuntu startup, with the rolling dots appears on one display, and then the gui comes up on the other and shuts down the first display.

This inability of ubuntu to use both my displays is the incorrect behavior I see in 10.04, and I was asked to see if  11.04 fixed it, which it does not, however, it acts differently. I'm trying to see if I can provide some useful data points to the developers.

---

