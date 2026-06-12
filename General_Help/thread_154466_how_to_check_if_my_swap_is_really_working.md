---
title: "how to check if my swap is really working?"
date: 2006-04-03
forum: General Help
---

### Post by syklitengutt on 2006-04-03
How can I check if my swap is really working.
I suspect it doesnt some times.

---

### Post by encompass on 2006-04-03
good question... there are many ways... the best way for you would be the system monitor in the applications menu under system tools... it will tell you how much swap you ahve used so far.  if any.

---

### Post by GeneralZod on 2006-04-03
1) Find a file that is larger than the amount of RAM in your PC - an Ubuntu .iso, for example.
2) Open that file with vi!
3) ?
4) See whether swap has been used by running "top" from the command-line.

Why do you want to check, by the way? Are you seeing lots of apps crashing/ extreme disk thrashing?

---

### Post by syklitengutt on 2006-04-03
damn.... it isnt listed there, but its listed under system administration disks...

---

### Post by syklitengutt on 2006-04-03
but its in my fstab:
/dev/hda4       none            swap    sw              0       0

the reason is when playing cs I get some crashes after some time.
I have the newest ati drivers.
In system monitor swap isnt mentioned...

---

### Post by halfvolle melk on 2006-04-03
[QUOTE=syklitengutt]In system monitor swap isnt mentioned...[/QUOTE]
Did you click the "Resources" tab? It should mention your swap.

---

### Post by syklitengutt on 2006-04-03
ok... its listed there...
I dont have any big iso files.
Just img files.
Is there any other way I can check if its actually working?

---

### Post by halfvolle melk on 2006-04-03
Maybe run CS non full screen while checking your system monitor?

---

### Post by mozetti on 2006-04-03
I'm running a gDesklet that monitors my RAM/Swap usage -- if you're running that, add the desklet and start poppin' open large files.

---

### Post by syklitengutt on 2006-04-03
ive tested now... I opened all big programs I could think of:
gimp, blender, qview, firefox, openoffice, k3b etc etc etc.
After opening 40 programs + I got it to write 100MB to swap.

---

### Post by bluetoad on 2006-04-03
[QUOTE=syklitengutt]ok... its listed there...
I dont have any big iso files.
Just img files.
Is there any other way I can check if its actually working?[/QUOTE]

The free command 

$ free
             total       used       free     shared    buffers     cached
Mem:       1027580     325576     702004          0        204     115136
-/+ buffers/cache:     210236     817344
Swap:      3358712      10640    3348072

---

