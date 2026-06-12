---
title: "Restarting the desktop and/or fixing"
date: 2012-04-10
forum: General Help
---

### Post by ulugeyik on 2012-04-10
Hi,

I am having difficulty understanding the concept of the desktop/unity/gdm etc since unity was picked up. 

I used to be able to do:
sudo service gdm restart
or even just kill gdm amd restart it to fix problems with frozen items on the desktop, messed up graphics etc without restarting the whole system.

Now this command gives me a new login screen but keeps the existing user logged in so I can't fix the problems.

According to this URL and others:
[http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal](http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal)


I should do:
unity &> /dev/null & disown
which indeed fixes a lot of the frozen things and removes the weird leftover graphics that end up on the screen but I the menus, the top bar of the windows etc are gone.

I tried     
unity-window-decorator &> /dev/null & disown
which messed up everything.

In summary, how can I restart the window manager with or without saving all my open windows?

Thanks,

---

### Post by cortman on 2012-04-10
The answer depends what version of Ubuntu you're using. 11.10+ uses LightDM instead of GDM for display manager. You can stop/start it with

```
sudo stop lightdm
sudo start lightdm
```

But perhaps a better idea would be to figure out why you're having graphics issues in the first place. Maybe need a better graphics driver?

---

### Post by ulugeyik on 2012-04-10
Good point, I should have included which distro I use. I use "lightdm". 

I have no idea what causes the problems. I have tried to debug it few times but with no luck. The only thing I can say is that this machine has been upgraded many times -- atleast through ~6 cycles (3 plus years) -- and in the past after few cycles I was ending up reinstalling everything to get a nice and clean OS but I hate to do it here.

---

### Post by ulugeyik on 2012-04-10
This being said. I would be interested in a method that may allow me to salvage the windows that are open.

---

### Post by cortman on 2012-04-10
Still not sure I understand. If you use lightdm, do ther stop/start commands I gave not work?
And not sure what you mean about salvaging open windows.

---

### Post by ulugeyik on 2012-04-11
I apologize. Yes, indeed "lightdm" works fine.  However, it kills everything and restarts them.

I am also looking for an alternative to salvage the open windows etc because not everything is frozen. For example, I think one problem is related to flash usage on firefox and it leads to some windows staying open even though I kill all the firefox related processes. they are unresponsive but take up screen real-estate. When I restart "unity" with:
unity &> /dev/null & disown

Indeed, I am able to  salvage what I am doing, however, sometimes it loses the menus, sometimes it messes up the dual-screen set up I have -- for example, maximizing maximizes through both screens. There must be "proper" way of restarting just unity or compiz.

---

### Post by cortman on 2012-04-11
Ok I understand now. For restarting compiz, have you tried

```
compiz --replace
```

---

### Post by ulugeyik on 2012-05-07
> **cortman said:**
> Ok I understand now. For restarting compiz, have you tried

```
compiz --replace
```

Sorry, I missed the update email on your reply. This restarts many things but one of the missing things, the black unity menu on the left still persists.

---

