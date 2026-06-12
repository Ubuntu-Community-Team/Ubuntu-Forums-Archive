---
title: "Laptop fan does not work; How to control fans?"
date: 2006-03-15
forum: General Help
---

### Post by Veniogenesis on 2006-03-15
Hi everyone,

I've noticed that my laptop fan has never turned on while using Ubuntu.  (It works in Windows.)  Is there a way to control it (settings in a file, etc.), either automatically or manually?

Thank you so much!
Cheers,
Venio

---

### Post by pcmxkeith on 2006-03-15
I believe there isnt, I think everything is in the BIOS

---

### Post by sublime on 2006-03-15
i know with my laptop i can set it to either performance or battery life.  the battery life option only allows the fan to turn on when it gets really hot, whereas with performance it keeps the fan on most of the time.

---

### Post by dmizer on 2006-03-15
this is probably the one thing i have the most linux experience with.  i myself burned up 3 laptops as a result of acpi failing to work properly.  first ... make sure your cpu temperature requires the fan to come on.  you can load a little utility like gkrellm (sudo apt-get install gkrellm), or you can just do:

```
cat /proc/acpi/thermal_zone/THM1/temperature
```

let's start with what kind of computer you're using ... make, brand, any model identifiers.  for example ... the machine i used was a toshiba tecra 8100.

it MIGHT also help to know your bios manufacture and version.  and, while we're on the topic of bios ... have you checked to see if there are any updates available for it?

let me know, and we'll go from there.

ps. unless your's is an extreme case, there are ways to toggle cpu fans on and off both automatically and manually.

---

### Post by Veniogenesis on 2006-03-16
Hmmm, my CPU is running at 130 F and rising.  Wow.

It's a Toshiba M35-S359 or something like that.  I'm sure it's in the M35 series though.

I don't know how to update the BIOS since the download is a Windows EXE zip.

---

### Post by dpaint4 on 2006-03-16
I use a HP Pavilion dv1000, and the fan works, but I run consistantly at around 130 degrees ferenheit (55 Celcius).  I'm only using about 4-10% of my CPU unless I'm encoding video, music, or playing a game.

That's normal right? I always figured the laptop should be a little warm to the touch. 130 dosen't sound bad to me.

I'm not sure when the fan *does* come on, but it's usually when I'm nearing 100% CPU useage.

Let's all straighten this out. Maybe you don't have a problem and you just don't do stressful things with your laptop. Try encoding something and see if the fan kicks in. Maybe Windows was just much less efficient.

---

### Post by dmizer on 2006-03-16
that ... is a bit too hot. laptops run a bit higher than desktops, but it's not too bad.

try this:

```
sudo modprobe toshiba_acpi
sudo echo "force_on:1" > proc/acpi/toshiba/fan
```

the fan should then come on.  you can turn it off by typing:
```
sudo echo "force_on:0" > proc/acpi/toshiba/fan
```

---

### Post by dpaint4 on 2006-03-16
I don't think this is the sort of thing that should have to be done manually. I mean, obviously not. If I was in that position, I think I'd just revert to my prior OS and wait for updates.

Silly to be constantly watching one's laptop's temperature and turning on and off the fan via the command line. Smart fix though, band-aid wise.

I've now been running for a few hours and I'm still steady at 130 myself (55C). So I'm accepting that as normal running temp of my laptop, and the fan never comes on until I start a game or an encode.

I still encourage Veniogenesis to do something intesive for a moment and truly see if the fan won't come on. I'm currently still clinging to the notion that s/he's just a light user.

---

### Post by dmizer on 2006-03-16
[QUOTE=dpaint4]I don't think this is the sort of thing that should have to be done manually. I mean, obviously not. If I was in that position, I think I'd just revert to my prior OS and wait for updates.

Silly to be constantly watching one's laptop's temperature and turning on and off the fan via the command line. Smart fix though, band-aid wise.[/QUOTE]
turning the fan on and off by the command line is not a bandaid. neither is it a fix.  i am simply attempting to determine if that module will control his fan.  if it does, then it can be automated, if not ... we will have to look elsewhere.

dpaint4: your fan probably does come on in linux, just not full on.

you're right ... 55c is not too hot for a laptop.  and in fact, your fan may not be comming on.  but it probably does not come on because your bios is stepping down your processor's speed to keep it cool.

---

### Post by dpaint4 on 2006-03-16
[QUOTE=dmizer]turning the fan on and off by the command line is not a bandaid. neither is it a fix.  i am simply attempting to determine if that module will control his fan.  if it does, then it can be automated, if not ... we will have to look elsewhere.

dpaint4: your fan probably does come on in linux, just not full on.

you're right ... 55c is not too hot for a laptop.  and in fact, your fan may not be comming on.  but it probably does not come on because your bios is stepping down your processor's speed to keep it cool.[/QUOTE]

Oh no. My fan comes on fine. It just dosen't do it at that temperature, but everything seems fine from my perspective, so I'm advocating that he might not actually have a 'problem' unless it get's significantly hot. I'd like to see a more specific number than '130F and rising'. Basically, rising to what? Just constantly rising? That'd be bad.  Hovering between 90 and 130-ish would be normal I'd say.

Anyway, sorry to dismiss your 'bandaid' without knowing what you were up to. Thought you were proposing it as an end-sollution. Sounds like a really great approach if there really is an issue. I just think there might not be.

---

