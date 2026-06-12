---
title: "How do you expire gksudo's timeout?"
date: 2010-11-12
forum: General Help
---

### Post by bigbaraboom on 2010-11-12
I know sudo has a '-k' option but what about gksudo?

It seems really strange to me, probably because i don't know how to expire it.:confused:

---

### Post by sisco311 on 2010-11-12
gksudo is a frontend for sudo, so *sudo -k* shoukd work just fine.

---

### Post by bigbaraboom on 2010-11-12
I see that works.

However the reason I asked is in reference to say gui applications, such as Gparted, Synaptic, etc.

Upon first opening they prompt you to authenticate. Subsequent launches do not! 
That is for a little while, which leads me to the conclusion they are being authenticated differently.

---

### Post by WorMzy on 2010-11-12
If you want to modify the timeout, open a terminal and run

```
sudo visudo
```

You should see a line with

"Defaults        env_reset", append the following onto the end of it:
```
,timestamp_timeout=0
```
so it looks like this:
```
Defaults        env_reset,timestamp_timeout=0
```
Save the file and exit (you'll be prompted if you've made a mistake)

This will make sudo prompt you for a password every time you use it. This behaviour should extend to gksudo and gksu (assuming you've left gksu using the sudo backend, and haven't switched it to use su). Change the 0 to 1 for a one minute timeout, 0.5 for a 30 second timeout, etc. Default is five minutes.

Run
```
man sudoers
```
for a list of other options you can set.

---

### Post by bigbaraboom on 2010-11-25
I am familiar with the [FONT="Courier New"].timestamp_timeout[/FONT] option.
In my case both [FONT="Courier New"]gksu[/FONT] and [FONT="Courier New"]gksudo[/FONT] expire as expected, and this is where the thread title I chose is somewhat misleading.

Here is an attempt to improve my last one ..

There are GUI Apps that require authentication before starting (Gparted, Synaptic, etc.). I falsely made a correlation between opening such applications through the command line with [FONT="Courier New"]gksudo[/FONT], and opening them from the *System* menu.

Suppose all the steps below occur in the order they are listed and within the [FONT="Courier New"].timestamp_timeout[/FONT] setting.

case1: [FONT="Courier New"]gksudo[/FONT]
- after initial authentication the program launches
- exit program and run [FONT="Courier New"]sudo -k[/FONT]
- starting the program presents a password prompt

case2: *System* menu
- after initial authentication the program launches
- exit program and run [FONT="Courier New"]sudo -k[/FONT]
- starting the program **does not** present a password prompt

Hopefully this made it clearer to whoever's reading this (most likely not paying any attention).

Anywho, can someone explain the last step in case2 to me?

---

### Post by bigbaraboom on 2011-03-29
I just can't understand this behavior:

Launcher for Synaptic is:
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

In gconf-editor > apps > gksu > sudo-mode is set, which means that gksu uses sudo as a backend, yet sudo -k does NOT expire the timestamp when using the launcher(System->Administration->Synaptic) :confused:
(i.e. start Synaptic, get a passprompt; quit Synaptic; sudo -k; start Synaptic, NO passprompt!)

if I run the launcher command from the shell it considers sudo -k and DOES expire the timestamp.
It seems like the processes forked from launcher and shell treat the timestamp differently. Does this have something to do with the parent that creates the process( bash vs gnome )?

---

