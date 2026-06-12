---
title: "poll_schedule_timeout"
date: 2011-11-21
forum: General Help
---

### Post by johnuk on 2011-11-21
Been having a look through the google and search on here.

I'm getting it as well, 'poll_schedule_timeout' on 90%+ of everything in system monitor.

Running the latest release and all updated as of Mon 21st Nov 2010. 

My CPU and memory are not saturated. But everything seems to have massively slowed down. Particularly Firefox.

I thought it was Firefox it's self, as I'd installed two video grabbing plugins from it's archive the week before. I disable those. 

I've tried restarting and hard resetting, and fingering the button hands on, but it's constantly reappearing at start up.

It does something quite special to Firefox. 

When Firefox first starts, it will browse back to some of the pages I had left open, but then start dying. I'll get loading circles on them, timeout errors and unable to contact server errors. 

But, if I manage to download something like a PDF, it'll come down at a normal speed, showing it's definitely nothing to do with the connection it's self.

I've also tried removing and reinstalling Firefox, and swapping desktop environments. No luck.

It's as if something has acquired the highest interrupt but is sitting there doing nothing, stalling up everything else in the meantime.

---

### Post by johnuk on 2011-11-21
Actually, I just checked my sys mon again and yes, the CPU is loaded to full.

And system monitor seems to be a major chunk of that. 

I'll see if I can roll back to early version of ubuntu, then come back up.

Any suggestions in the meantime would still be great!

John

---

### Post by An Sanct on 2011-11-21
By the latest version, I assume Oneiric ...

Could you please tell us what the output of "top" is? (run the terminal and execute the *top* command)

---

### Post by johnuk on 2011-11-21
Oneiric yep. I usually use gnome.

Actually, I have Oneiric and gnome on this laptop and have poll_schedule_timeout all over this one's processes as well, despite it only having just been installed. Although, the CPU load is normal and everything is working fine.

On the desktop, the one that is suffering, I can't get online. It's sat next to me at the moment.

I've just rebooted it, the network isn't connecting and I'm not trying to run anything. Browser is closed.

**top**

There is nothing using more than a few percent of the CPU.

I try opening system monitor. Everything in processes is queued, waiting or timed out. The vertical scroll bar for the list is missing. Enlarging the box does not display the rest. Clicking resources does nothing. Clicking exit I get a 'busy and not responding' for the sys mon.

Close it and the terminal. Try reopening sys mon. Nothing.

Ask it to reset. Seems to hang on the way down. Use hard power off.

Again, seems to be taking longer than it should to boot.

Get back into the desktop and go straight to sys mon. Again, everything timed out, waiting or queued.

Network has now connected (randomly). 

Memory and swap are flat. Network history is also basically at 0.

CPU is constantly at 60%+. I'm watching the graph right now and it's waving up and down from 60 to 75% with no pattern or drive activity. I am doing **nothing** on the machine but watching sys mon. 

**top**
CPU
52.9% Xorg
17.9% gnome-sys-mo 

I have just spotted a weird pattern!

If I click off the resources tab to 'system', and then back to resources. There is a huge dip in the graph to 0, then it immediately rises back to the busy state. It also happens if I click processes or file systems, then return to resources.

It does not happen if I send the sys mon to the toolbar. Neither it's own graph, nor the output of **top** show it dropping.

There is another very odd behavior. If I bring sys mon back up, but simply decrease the size of the box, the CPU usage drops. By making it as small as possible, it'll drop to 15% or so and stay around there. The drop is even mimicked in the **top** results.

Full screen it and the CPU is instantly back up at 60%+ for both results.

Try closing sys mon. Nothing for a few seconds, then a 'busy not responding', then it closes it's self and the **top** result drops back to nothing using more than 1% of the CPU.

How odd! :D

---

### Post by An Sanct on 2011-11-21
hm .. sound like a weird graphics problem then :) as the system monitor is actually drawn really nice and smooth :)

there was a thought about this [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488849"), but I would guess its not the same issue...
now [this one]("http://ubuntuforums.org/showpost.php?p=10155193&postcount=2") talks about your problem (memory gone after system monitor execution..)

what about if you don't run the system monitor - as this seems to be the culprit :) instead run *top*...

---

### Post by johnuk on 2011-11-22
It wasn't really the sys mon that originally highlighted a problem, it was firefox it's self doing weird things.

If I downloaded something like a PDF, it'd come down fine at a few hundred kbs. But the tabs would often simply sit there doing nothing or timing out; as if I had some huge ping, even though they were big, well supported sites. And others would work fine at the same time.

For example, I have ten or so tabs open right now looking at different sites, but the Stihl (garden tools) site (which I was just on fine until the computer was reset) now won't load, it's sitting with the circle spinning on the tab.

I just redid top and now it's saying the plugin container is hogging all the CPU.

---

### Post by An Sanct on 2011-11-22
aha :) plugin container points to something with flash.

Which flash version do you use?

As you mentioned, you use FireFox, this is the address to check it out

```
about:plugins

or even better

http://www.mozilla.org/plugincheck/
```

As flash is a pain ... I can only recommend, that you check out [Flash AID]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"), this will simplify everything done concerning flash installation and FireFox.

---

### Post by johnuk on 2011-11-25
Thanks, I do have flashaid installed.

After forcing the container to close and updating the flash version, it does seem to be working better now.

Although sys mon is still doing the odd thing of using more CPU the bigger the screen is! :P

---

