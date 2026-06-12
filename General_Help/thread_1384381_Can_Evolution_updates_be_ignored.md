---
title: "Can Evolution updates be ignored?"
date: 2010-01-18
forum: General Help
---

### Post by Sleepy-zz-John on 2010-01-18
I'm using SeaMonkey as my mail client,  and have never set up Evolution, so when Update Manager keeps offering me Evolution updates,  I've been  unchecking and ignoring them. 
But I suspect there might be some common files in the Evolution package that other mail clients or other Gnome features depend upon. 
My question is: Could I totally remove Evolution software in order to stop me being bombarded with updates to Evolution, or are there dependencies I should be aware of before doing that?

---

### Post by Grenage on 2010-01-18
Remove it using the synaptic package manager, it will warn you if there are other dependencies.

---

### Post by nanotube on 2010-01-19
or you could just install the updates and it'll stop bothering you, if you don't want to uninstall.

---

### Post by Sleepy-zz-John on 2010-01-19
Thanks.    I did try Grenage's suggestion, and I uninistalled the parts that appeared to be safe from other dependencises,  and that's stopped some of the updates,  but not all of them.   I'm still seeing "evolution-common" (3MB) and "evolution-documentation-en" (120KB) updates being offered.  

In truth, I'm wary of being over-enthusiastic about uninstalling evolution because a couple of years ago when I tried to do the same thing on Hardy, I somehow ended up breaking my Gnome and despite various advice and attempts to restore it from a terminal, I failed,  and lost everything. 
 
I'm tempted to try nanotube's suggestion and simply accept the updates,  but of course that won't prevent new updates in future.    If I could safely uninstall more now,  that would at least lessen the chances of new future updates being offered
.   
Actually I'm a little puzzled why any Gnome or other system essentials should be included in packages under the name of Evolution when Evolution is after all only one of many e-mail client options. 

Thanks for the replies.

---

### Post by nanotube on 2010-01-19
> **Sleepy-zz-John said:**
> Thanks.    I did try Grenage's suggestion, and I uninistalled the parts that appeared to be safe from other dependencises,  and that's stopped some of the updates,  but not all of them.   I'm still seeing "evolution-common" (3MB) and "evolution-documentation-en" (120KB) updates being offered.  

In truth, I'm wary of being over-enthusiastic about uninstalling evolution because a couple of years ago when I tried to do the same thing on Hardy, I somehow ended up breaking my Gnome and despite various advice and attempts to restore it from a terminal, I failed,  and lost everything. 
 
I'm tempted to try nanotube's suggestion and simply accept the updates,  but of course that won't prevent new updates in future.    If I could safely uninstall more now,  that would at least lessen the chances of new future updates being offered
.   
Actually I'm a little puzzled why any Gnome or other system essentials should be included in packages under the name of Evolution when Evolution is after all only one of many e-mail client options. 

Thanks for the replies.

well, unless you're on a severely limited internet account, or a severely constrained hard drive space, i fail to see any downsides to just accepting the occasional evolution update when it comes your way. that's what i've always done myself, and never had any problems. 

my understanding is that evolution did get somewhat more untangled from the rest of gnome, on the way between hardy and karmic, so it may be possible to remove it if you know what you're doing, but i myself have never done it, so won't counsel you to try either. :)

(i only tried it once, back on dapper or thereabouts, and then synaptic said "i'll remove a whole bunch of these other packages, some of which look very useful" and i said 'no thanks' and have just lived with unused evolution just sitting on my system ever since.)

---

### Post by Grenage on 2010-01-20
> I'm still seeing "evolution-common" (3MB) and "evolution-documentation-en" (120KB) updates being offered.

If you open the synaptic package manager and search for "evolution", you should get a full listing of evolution-related stuff.  I did that here, and it's displayed the common and documentation packages et cetera.

It should be safe for you to select anything in there that refers to evolution, and there is a decent description if you're unsure.

---

### Post by Yellow Pasque on 2010-01-20
You can remove all evolution packages EXCEPT evolution-data-server-common, as that package is used by other gnome stuff.

---

### Post by Sleepy-zz-John on 2010-01-20
OK guys,  thanks to nanotube and Temüjin's recommendations, I've now downloaded and installed the Evolution-common package, so that one's no longer cluttering up my Update Manager,  and thanks to Grenage's recommendation I've uninstalled evolution-documentation-en in synaptic package manager, so I've got rid of that permanently.
So no sign of Evolution in my Update Manager at all now.   Many thanks for all three helpful replies.

---

