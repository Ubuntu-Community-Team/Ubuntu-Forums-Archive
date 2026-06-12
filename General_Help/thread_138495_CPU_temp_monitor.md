---
title: "CPU temp monitor"
date: 2006-03-02
forum: General Help
---

### Post by mackinax on 2006-03-02
I'm looking for a (simple) app to monitor my cpu temp.
And I want to be able to add it to a panel. (like System Monitor)

I didn't see anything included in the base install...
is there anything in the repositories?

If not, I need recommendations.

Thanks!

---

### Post by cronholio on 2006-03-02
You might want to have a look at GKrellM (in the repositories).

---

### Post by steve.horsley on 2006-03-02
I looked at synaptic and the various gkrellm module descriptions, and it seems it only does temperature monitoring for Dell laptops (gkrellm-i8k). Is there another package we don't know about?

---

### Post by Lux Perpetua on 2006-03-02
Gkrellm reports my CPU temperature ostensibly with no problems (IBM laptop).

---

### Post by Razorback on 2006-03-02
Try conky.  It is also versatile for displaying other useful information.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by ow50 on 2006-03-02
[QUOTE=mackinax]And I want to be able to add it to a panel. (like System Monitor)[/QUOTE]

[http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)
[http://www.cs.auc.dk/~olau/hardware-monitor/](http://www.cs.auc.dk/~olau/hardware-monitor/)

Both are in the repositories.

You'll need to install lm-sensors first and at the command line run
```
sensors-detect
```

---

### Post by mssm on 2006-03-02
[QUOTE=mackinax]I'm looking for a (simple) app to monitor my cpu temp.
And I want to be able to add it to a panel. (like System Monitor)

I didn't see anything included in the base install...
is there anything in the repositories?

If not, I need recommendations.

Thanks![/QUOTE]

I can suggest a cool piece of software : Install Superkaramba first and then from SuperKaramba Aero All In One( Aero AIO). It has many nice monitora including CPU usage and temp. monitor. Looks beautiful too.

---

### Post by mackinax on 2006-03-02
[QUOTE=cronholio]You might want to have a look at GKrellM (in the repositories).[/QUOTE]
Got this running along with the mbmon daemon. :)
Thanks, this will work well for now!

[QUOTE=ow50]http://sensors-applet.sourceforge.net/[/QUOTE]
That seems to be exactly what I want... Thanks!


@ all :
I will look at the other suggestions later, thanks for the replies!

---

### Post by mastergunner on 2007-09-01
Just looked in adept manager and it say this program is for monitors. what gives?

---

