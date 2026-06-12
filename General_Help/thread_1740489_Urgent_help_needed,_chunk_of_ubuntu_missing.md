---
title: "Urgent help needed, chunk of ubuntu missing"
date: 2011-04-27
forum: General Help
---

### Post by Ominae on 2011-04-27
Okay 

i was just uninstalling a few things i did not need or want on the laptop about 20 min ago, Transmission And the default mail client forget its name I just did a system restart and now my menu bars at the botem of the screen are Missing with no way to re enable then i fear i have uninstalled something that Ubuntu needed.

I still have acsess to some things thanx to runny docky ie. firefox terminal and empathy i was still setting it up at the time :(

is there any way to fix this with out a full reinstall as i had just gotten to the point where i was happy with the laptop after a week of learning and work.  i am not to good with terminal but i can use it iff i have to :)

any help would be greatly appreiated at this time
thanx guys an gals

mark "a paniky new ubuntu user :P"

---

### Post by earthpigg on 2011-04-27
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

then, restart.

post results?

---

### Post by wilee-nilee on 2011-04-27
> **Ominae said:**
> Okay 

i was just uninstalling a few things i did not need or want on the laptop about 20 min ago, Transmission And the default mail client forget its name I just did a system restart and now my menu bars at the botem of the screen are Missing with no way to re enable then i fear i have uninstalled something that Ubuntu needed.

I still have acsess to some things thanx to runny docky ie. firefox terminal and empathy i was still setting it up at the time :(

is there any way to fix this with out a full reinstall as i had just gotten to the point where i was happy with the laptop after a week of learning and work.  i am not to good with terminal but i can use it iff i have to :)

any help would be greatly appreiated at this time
thanx guys an gals

mark "a paniky new ubuntu user :P"

Look in synaptic history, in the terminal if needed.
gksudo synaptic

There is a history in the terminal if you were using that.

There is also this site for whole desktop adding or removal, lower left playing around. Take note of the distro besides the desktop.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by Ominae on 2011-04-27
> **earthpigg said:**
> ```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

then, restart.

post results?

Hey earthpigg

dude your a life saver thanx dude i did what you said and i now have it all back the way it was :D talk about ouver the moon an this all happend at school loooool so i sorta needed the help many thanx agnen....

jus missin my volume option on the bar now will have a bash at that later..

and thanx wilee-nilee for the help also even though i did not get to your help :)

Update got the volume controles back :) big thanx agen

---

### Post by earthpigg on 2011-04-27
good. 

now, in the future, make sure you read warning messages when uninstalling stuff.

if you want a stripped-down custom version of ubuntu, the correct approach is to start with a command-line only system and **build up** -- not the other way around.

---

### Post by wilee-nilee on 2011-04-27
Cool its fixed, you can get the volume icon to appear with in the startup applications command
gnome-volume-control-applet

[ATTACH]190185[/ATTACH]

---

