---
title: "How do I exit conky?"
date: 2011-05-24
forum: General Help
---

### Post by airspoon on 2011-05-24
Hello, I'm new to Ubuntu, having recently installed 11.04, though due to problems with the Nvidia graphics driver, I'm using Gnome classic (not sure if that is pertinent here). In short, I can't find a way to close conky, other than to terminate the process -which I'm not sure if that would hurt anything.

I read a quick internet tutorial ([http://www.junauza.com/2009/03/installset-up-conky-on-ubuntu.html](http://www.junauza.com/2009/03/installset-up-conky-on-ubuntu.html)) on configuring conky so after installing 'conky-all', I created the configure file. It seems to work fine, minus a few alerts in the terminal at startup of the app.

On startup of conky through the terminal, it was kicking back messages such as:

```
 Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
```and...

```
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/apm: No such file or directory
```Sorry I can't cut and paste the original message but I accidentally closed the terminal before I could copy.

I pretty much figure that the latter messages are due to the fact that I'm on a desktop as opposed to a laptop so I'm not too worried about those.

However, the conky window that is showing, is really ugly (IMO) so I'm wanting to play around with the configuration file to get it just right and to match my Gnome theme. When I tried to change a few values in the configuration file, the same conky window just stayed on my desktop. I'm figuring it's because Conky has to be restarted. Is that correct?

I can't figure out how to exit conky so that I can make changes to the configuration file and then restart conky. Is this possible? Is there a command for exiting conky?

Any help would be greatly appreciated. Thanks.


--airspoon

---

### Post by enochpc on 2011-05-24
You can type killall conky in the terminal, or just kill conky.  Might have to sudo it, but I would try without first.

---

### Post by Frogs Hair on 2011-05-24
Alt+F2 ```
killall conky
```

---

### Post by airspoon on 2011-05-24
Awesome, thanks to both of you guys. It worked! Will the 'killall' command work for everything else too? Again, thanks.

---

### Post by bodhi.zazen on 2011-05-24
> **airspoon said:**
> Awesome, thanks to both of you guys. It worked! Will the 'killall' command work for everything else too? Again, thanks.

yes. As will kill , and there is also xkill .

---

