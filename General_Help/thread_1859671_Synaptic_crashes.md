---
title: "Synaptic crashes"
date: 2011-10-14
forum: General Help
---

### Post by lothur on 2011-10-14
Hi!

Just did a fresh ubuntu 11.10 install. I then installed synaptic pm and I can`t get it to open. It loads up for a second and then shuts down. I have an dell inspiron 6400 (that has always been great on ubuntu).
Any fixes out there?

---

### Post by matt_symes on 2011-10-14
Hi

If you start it from the command line do you get any feedback as to why it's crashing ?

From the terminal type.....

```
synaptic
```

Kind regards

---

### Post by TeoBigusGeekus on 2011-10-14
Start it from terminal
```
gksu synaptic
```
and post us any error messages.

EDIT: Oh hi Matt!!!

---

### Post by matt_symes on 2011-10-14
Hi Teo. I hope you are well.

---

### Post by TeoBigusGeekus on 2011-10-14
> **matt_symes said:**
> Hi Teo. I hope you are well.

Hale and hearty mate; "bad weeds grow tall".

I hope you're well too.

---

### Post by lothur on 2011-10-14
Thanks for quick respons!

I got this from the terminal: (synaptic:2781): Gtk-WARNING **: Kunne ikke finne temamotor i module_path: «pixmap».

It`s in norvegian :-)

It says something like; could`nt find theme engine in mdule_path: «pixmap»

---

### Post by TeoBigusGeekus on 2011-10-14
Try changing your gtk theme and repeat the procedure.

---

### Post by Quarkrad on 2011-10-14
Sorry to break into his thread.  I have configured yesterdays release (11.10) to have gnome classic desktop and install synaptic via the software centre.  Synaptic launches OK and I can select (Mark) something to install.  But when I click on **Apply** synaptic crashes.

---

### Post by lothur on 2011-10-14
Thanks!

Now it works:)

changed it to radience...

---

### Post by matt_symes on 2011-10-14
Hi

> **Quarkrad said:**
> Sorry to break into his thread.  I have configured yesterdays release (11.10) to have gnome classic desktop and install synaptic via the software centre.  Synaptic launches OK and I can select (Mark) something to install.  But when I click on **Apply** synaptic crashes.

Run it from the terminal and post back any errors.

> **TeoBigusGeekus said:**
> Hale and hearty mate; "bad weeds grow tall".

I hope you're well too. I'm a tiny bit hungover :D I blame Mr Kronenbourg. BTW: Good call on changing the theme.

Kind regards

---

### Post by Quarkrad on 2011-10-14
It crashes via terminal - this is the output.

[B]mimi@mimi-VirtualBox:~$ sudo synaptic
[sudo] password for mimi: 

(synaptic:2465): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:2465): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:2465): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:2465): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Discarding: 1 over 9
FATAL -> Failed to fork.[/B]


I don't think  this is relevant but....  When I type **libmtp** in the search field **lib** appears as I type but then nothing - the cursor turns into a circle that seems to be searching.  This goes on for some time and then the rest of the letters **mtp** appear and I get the list of packages in the main window.  I thought at first this searching was because it was the first time I had used synaptic but it takes a long time to search every time.  Perhaps it is because it is being used within Virtualbox.

---

### Post by matt_symes on 2011-10-14
Hi,

Is this a memory issue ? How much memory did you allocate in VirtualBox ?

From the terminal type (with synaptic open)

```
free -m
```Kind regards

---

### Post by Quarkrad on 2011-10-14
Thank you - that did it.  I allocated more memory in VB  and everything works.  Many thanks.

---

