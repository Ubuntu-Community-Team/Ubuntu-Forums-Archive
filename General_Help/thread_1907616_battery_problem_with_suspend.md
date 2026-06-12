---
title: "battery problem with suspend"
date: 2012-01-11
forum: General Help
---

### Post by josephellengar on 2012-01-11
Hi. HP dv7t, U11.10, Gnome 3

I am having a problem with power management on my laptop. When I resume from suspend, regardless of how much power it has left, it always thinks that the battery is about to die, and immediately shuts down or hibernates. It also has a lot of trouble guessing how much time is left otherwise (can be at 99% battery life and say 15 minutes when it will actually live for ~3 hours) but it is particularly bad when I resume from suspend. I literally cannot resume without the computer plugged in or it will shut down. Any suggestions? Thanks!

---

### Post by cllewis91592 on 2012-01-11
mine does something like that but it just pops up a window that says my power is low. not sure how to fix this. i have seen that some people have the same problem, hope people can fix it.

---

### Post by josephellengar on 2012-01-11
> **cllewis91592 said:**
> mine does something like that but it just pops up a window that says my power is low. not sure how to fix this. i have seen that some people have the same problem, hope people can fix it.

Mine does the pupup too, but immediately dies.

---

### Post by IWantFroyo on 2012-01-11
Open "Power Management", switch to the "Battery Power" tab, and change "When battery power is critically low:" to "Suspend."

There doesn't seem to be a way to just turn it off without removing acpi, which will probably screw up the ability to suspend in the first place.

Try uninstalling acpi if you have it, and install apmd.

---

### Post by pr3zident on 2012-01-11
> **josephellengar said:**
> Mine does the pupup too, but immediately dies.

Sounds like a burned out battery that needs to be replaced ... Further research though to see what it actually is ...

---

### Post by josephellengar on 2012-01-11
> **pr3zident said:**
> Sounds like a burned out battery that needs to be replaced ... Further research though to see what it actually is ...

It's not. The battery is new and tests at 88% capacity. I got the replacement only a month ago. On Windows it lasts about 3 hours. In Ubuntu it lasts 3 hours too, if I don't suspend.

---

### Post by pr3zident on 2012-01-11
> **josephellengar said:**
> It's not. The battery is new and tests at 88% capacity. I got the replacement only a month ago. On Windows it lasts about 3 hours. In Ubuntu it lasts 3 hours too, if I don't suspend.

Oo I see that's weird then ..

---

### Post by josephellengar on 2012-01-11
> **IWantFroyo said:**
> Open "Power Management", switch to the "Battery Power" tab, and change "When battery power is critically low:" to "Suspend."


I don't have the option to do this. My only options are Hibernate or Shutdown.

> 
There doesn't seem to be a way to just turn it off without removing acpi, which will probably screw up the ability to suspend in the first place.

Try uninstalling acpi if you have it, and install apmd.

Oddly acpi wasn't installed in the first place. But I just installed apmd. Now what do I do to get it set up or whatever?

Thanks!

---

### Post by IWantFroyo on 2012-01-11
I haven't used apmd for a long time, but you should be able to start it by running the command "apmd".

I checked my computer, and I don't have acpi installed either (note: I'm using 10.10). Odd, considering I need to use the pci=noacpi or acpi=off parameter to boot up.

Try uninstalling acpid. This seems to be the daemon for acpi. Maybe running apmd after removing acpid will set apm as your default power manager.

---

### Post by josephellengar on 2012-01-11
> **IWantFroyo said:**
> I haven't used apmd for a long time, but you should be able to start it by running the command "apmd".

I checked my computer, and I don't have acpi installed either (note: I'm using 10.10). Odd, considering I need to use the pci=noacpi or acpi=off parameter to boot up.

Try uninstalling acpid. This seems to be the daemon for acpi. Maybe running apmd after removing acpid will set apm as your default power manager.

I got a message: "No APM Support in Kernel"

---

### Post by IWantFroyo on 2012-01-11
They must have dropped it with 11.10. That's a shame. I'm not sure what to do about that, then.

Maybe you can remove gnome-power-manager and install the Debian Squeeze version via DEB and apt-get install -f?
[http://packages.debian.org/search?keywords=gnome-power-manager](http://packages.debian.org/search?keywords=gnome-power-manager)

---

### Post by topsites on 2012-01-11
Unlike desktops with laptops I find I'm better off shutting it down myself when I am done using it, leaving it plugged in continues to charge the battery, that's just been my experience.

---

### Post by IWantFroyo on 2012-01-11
> **topsites said:**
> Unlike desktops with laptops I find I'm better off shutting it down myself when I am done using it, leaving it plugged in continues to charge the battery, that's just been my experience.

Sometimes I have to get up and move around before I can keep working, and it's too much of a bother to shut down the computer and then turn it on again.

---

### Post by josephellengar on 2012-01-11
> **IWantFroyo said:**
> They must have dropped it with 11.10. That's a shame. I'm not sure what to do about that, then.

Maybe you can remove gnome-power-manager and install the Debian Squeeze version via DEB and apt-get install -f?
[http://packages.debian.org/search?keywords=gnome-power-manager](http://packages.debian.org/search?keywords=gnome-power-manager)

Yeah, the did dramatically change the amount of power management that you can do with this latest version. You can't even set different default screen brightness between when the computer is plugged in and not; you have to always manually change it. Pretty irritating. I like your suggestion, but it seems a little risky. What happens if they do a security update to the kernel or something that breaks compatibility with the power manager? Is that possible? It seems like a kind of important part of the computer to leave outside of the package management system.

But thank you very much for the suggestion. I really appreciate the help.

---

### Post by Toz on 2012-01-12
Have a look at this post - [http://ubuntuforums.org/showpost.php?p=11222710&postcount=2]("http://ubuntuforums.org/showpost.php?p=11222710&postcount=2") - perhaps it might help.

---

### Post by josephellengar on 2012-01-12
> **Toz said:**
> Have a look at this post - [http://ubuntuforums.org/showpost.php?p=11222710&postcount=2]("http://ubuntuforums.org/showpost.php?p=11222710&postcount=2") - perhaps it might help.

Thanks. I just ran the command and I'll try it out. I'll post back here if it doesn't work.

---

### Post by josephellengar on 2012-01-12
No good. I'm still having the same problems. Possibly because of the shift from gconf to dconf? I doubt that power manager looks in that area for its settings anymore.

---

### Post by Toz on 2012-01-12
Possibly. I'm not using gnome so I can't check. Does a similar entry exist in the dconf database?

---

### Post by josephellengar on 2012-01-12
> **Toz said:**
> Possibly. I'm not using gnome so I can't check. Does a similar entry exist in the dconf database?

There is a power manager entry in dconf, but all of the keys are associated with the GUI display of information-- none with how the system actually manages this stuff. I suppose it's possible that this simply can't be changed now; they stripped out so many customization options in the switch to Gnome 3.

---

### Post by josephellengar on 2012-02-26
I don't know if anybody has any fresh ideas or anything, but this has gotten worse in the past few days. Now I get the "critical battery" message literally every time I resume the computer from suspend. My battery can be at 95% and it will give me that message.

Last night I watched a movie for two hours on battery, so I know that the battery works. Also, sometimes, if I press "cancel" quickly enough on the popup box, it won't go back into suspend, but other times it will, and then when I resume I have two popup boxes. Anyway, suggestions would be appreciated, if you have anything that hasn't already been said.

---

