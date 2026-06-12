---
title: "Weird update manager behavior wrt PPAs"
date: 2011-01-14
forum: General Help
---

### Post by dewdrop_world on 2011-01-14
Maybe a dumb question, but is there a way to configure the update manager to select ONLY the important security updates?


I'm in a crunch time now and I can't afford a lot of downtime, so I don't want to perform updates that aren't critical. But, I also don't want to leave security holes.


The only way I can find is to deselect various updates by hand. But, there is an "interesting" interface glitch with that -- after deselecting several dozen updates, I accidentally clicked "Settings..." This asked me for my admin password, but I didn't really want to change the settings so I canceled. Update manager promptly rechecked all the updates and forgot my selections! That's pretty stupid. User selections should not be discarded in that case.


So then I changed the settings to enable critical security updates only (first checkbox in software sources > updates tab). This made NO difference -- it still selected to update packages that are not in the "important security updates" section.


I installed a couple of packages (not many) from LP-PPA-falk-t-j-lucid a few weeks ago. Now it looks like it wants to update *every* package contained in that PPA which I had previously installed from canonical. Huh? Why is that necessary? Is there no way to prevent that other than to disable the software source before updating?


I'll be happy to file a feature request @launchpad, but I just wanted to make sure I understand the rationale for the current behavior before doing. Especially the thing with the PPA -- I really just wanted a few things from it (jack2, pulse-jack) and I did not want a system update to cause the PPA to modify dozens of other applications.


James

---

### Post by Pollox on 2011-01-15
> **dewdrop_world said:**
> 
So then I changed the settings to enable critical security updates only (first checkbox in software sources > updates tab). This made NO difference -- it still selected to update packages that are not in the "important security updates" section.


Those radio buttons are under the heading "automatic updates". Hence, if you select "install security updates without confirmation", it will install security updates automatically. This has nothing to do with what boxes are checked when you go to update manually.

> 
I installed a couple of packages (not many) from LP-PPA-falk-t-j-lucid a few weeks ago. Now it looks like it wants to update *every* package contained in that PPA which I had previously installed from canonical. Huh? Why is that necessary? Is there no way to prevent that other than to disable the software source before updating?


The package manager will prompt you to update a package when there is a newer version available from one of your software sources, without regards to which source. Unless you need automatic updates of the packages you installed from LP-PPA-falk-t-j-lucid, I suggest you uncheck the box next to that PPA in your software sources. The programs you installed will stay installed but will not be automatically updated unless a newer version of them appears in one of your other software sources.

---

### Post by dewdrop_world on 2011-01-15
> **Pollox said:**
> Those radio buttons are under the heading "automatic updates". Hence, if you select "install security updates without confirmation", it will install security updates automatically. This has nothing to do with what boxes are checked when you go to update manually.

No, they aren't. You're talking about a different option. On the Updates tab, there are three sections: Ubuntu updates, Automatic updates and Release upgrade. I'm talking about:
 
** Ubuntu updates**
[check] Important security updates (lucid-security)
[check] Recommended updates (lucid-updates)
[check] Pre-released updates (lucid-proposed)
[check] Unsupported updates (lucid-backports)
 
I had unchecked all except "Important security updates" but the update manager still presented recommended updates to me -- hence my conclusion that the setting was ignored.
 
> The package manager will prompt you to update a package when there is a newer version available from one of your software sources, without regards to which source. Unless you need automatic updates of the packages you installed from LP-PPA-falk-t-j-lucid, I suggest you uncheck the box next to that PPA in your software sources. The programs you installed will stay installed but will not be automatically updated unless a newer version of them appears in one of your other software sources.
I did figure that out eventually, but it does raise what I think would be a valid feature request. It is not far-fetched that somebody would want to have a software source available to install packages, but not use it for update-manager updates. Currently the software sources tool gives you only a binary choice: on for everything, or off for everything. But that binary switch is used for at least two different purposes.

What I'm saying is that the control offered by "software sources" is not granular enough. One switch --> multiple meanings = confusion.
 
James

---

### Post by dewdrop_world on 2011-01-15
> **dewdrop_world said:**
> I had unchecked all except "Important security updates" but the update manager still presented recommended updates to me -- hence my conclusion that the setting was ignored.

Oh wait, I got confused here. "Recommended updates" didn't appear -- it was "Other updates" that showed up before.

So these checkboxes are being respected.


My other concern about the granularity of enabling/disabling sources remains.


James

---

### Post by Pollox on 2011-01-15
> **dewdrop_world said:**
> No, they aren't. You're talking about a different option. On the Updates tab, there are three sections: Ubuntu updates, Automatic updates and Release upgrade. I'm talking about:
 
** Ubuntu updates**
[check] Important security updates (lucid-security)
[check] Recommended updates (lucid-updates)
[check] Pre-released updates (lucid-proposed)
[check] Unsupported updates (lucid-backports)



Ah, okay, I know what you're talking about now, but it seems you're all set with that now.
 
> 
I did figure that out eventually, but it does raise what I think would be a valid feature request. It is not far-fetched that somebody would want to have a software source available to install packages, but not use it for update-manager updates. Currently the software sources tool gives you only a binary choice: on for everything, or off for everything. But that binary switch is used for at least two different purposes.

What I'm saying is that the control offered by "software sources" is not granular enough. One switch --> multiple meanings = confusion.


Yeah, I can see that being a decent feature request. Something along the lines of being able to only consider certain packages in a PPA. The "force version" and "lock version" options in Synaptic do give you some control over which PPA to use for a package, but not to the degree you are talking about. Generally, specialty PPA's are good about only including one package and its dependencies, but it looks like the PPA you're using has more than that.

---

