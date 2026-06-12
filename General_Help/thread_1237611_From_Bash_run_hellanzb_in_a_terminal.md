---
title: "From Bash: run hellanzb in a terminal"
date: 2009-08-11
forum: General Help
---

### Post by brownbat on 2009-08-11
I want a script that opens a terminal window and runs hellanzb. I want this hellanzb window to stay open, so I can monitor the progress of the app. 

gnome-terminal "-x" runs the rest of the command in that terminal; "-e" for xterm (but neither -e nor -x keeps the window open alone, each requires |less).
for "sh" (the shell), "-c" reads commands from the command_string rather than standard input.

Code:
gnome-terminal -x sh -c "ls|less"

Code:
gnome-terminal -x sh -c "cal -y|less"

Those work fine, but when I try: 

gnome-terminal -x sh -c "hellanzb|less"

The status is filled with weird "ESC" characters, and does not update. 

The xterm version of that command has the same problem.

Any other ways to accomplish this?

---

### Post by SlugSlug on 2009-08-11
> **brownbat said:**
> I want a script that opens a terminal window and runs hellanzb. I want this hellanzb window to stay open, so I can monitor the progress of the app. 

gnome-terminal "-x" runs the rest of the command in that terminal; "-e" for xterm (but neither -e nor -x keeps the window open alone, each requires |less).
for "sh" (the shell), "-c" reads commands from the command_string rather than standard input.

Code:
gnome-terminal -x sh -c "ls|less"

Code:
gnome-terminal -x sh -c "cal -y|less"

Those work fine, but when I try: 

gnome-terminal -x sh -c "hellanzb|less"

The status is filled with weird "ESC" characters, and does not update. 

The xterm version of that command has the same problem.

Any other ways to accomplish this?

hummm, when I used to use it the terminal stayed on till I closed it, 
could I recommend sabnzbd to you - much better ;)

---

### Post by DaithiF on 2009-08-11
Hi
I don't know anything about hellanzb, but generally if you want a gnome-terminal window to remain open after its command exits you can control this via a profile.

In gnome-terminal, create a new profile (Edit -> Profiles -> New, give it a name like KeepOpen, in the dialog box go to Title and Command tab, and choose 'Hold the Terminal Open' for the 'When command exits' dropdown.

Then in your script or launcher:
```
gnome-terminal --window-with-profile=KeepOpen -x hellanzb
```

---

### Post by brownbat on 2009-08-11
DaithiF: brilliant! Works like a charm!

SlugSlug: Does sabnzbd do automatic par-skipping? That's a must have feature for me. Either way, might wait until it works its way into the main repos.

---

### Post by SlugSlug on 2009-08-11
sab doesn't do par-skipping, but there is an option to skip 'sample' files other than that it does all hella does but with better queue management 

it is in the repos...

---

### Post by brownbat on 2009-08-11
"it is in the repos... "

So it is, my bad.

(hint: "sabnzbdplus")

Nice enough queue management, and maybe the par skipping wouldn't matter as much. I'll give it a shot, thanks for the tip!

---

### Post by doas777 on 2009-08-11
never had a problem with spare pars using sab. works like a charm. just drag a nbz to a network share on my downloading-stuff box, and off we go.

---

### Post by SlugSlug on 2009-08-11
yer it cleans up the stuff, but I think he was referring  to the par feature in hella - it will only download pars if it needs them - so saves bandwith..

---

