---
title: "Ubuntu - Loving it but..."
date: 2010-12-15
forum: General Help
---

### Post by BlueSpecial on 2010-12-15
Hello,

so I have Ubuntu 10.10 installed for some time now and I don't boot my Win7 machine in weeks!

I love how solid, robust it is... and also how good it looks. Love the features like Ubuntu One (use it a lot!) and the Software Center. I'm 95% converted and I would be 100% if it weren't for 2 issues:

1 - The machine won't shutdown. Rebooting works fine but shutdown it just hangs... Kinda sucks having to press the Power Off button every time...

2 - I'm on a laptop but it doesn't recognize my battery. All I get is a "electric ray" on the panel. Even if I remove AC power it still does the same... No charging information, nothing... I tried ```
sudo modprobe pmu_battery
```on the terminal but is says that the module could not be found.

Anyone could me help get a 100% system? Everything else works terrific (better than Windows!) with this two exceptions... :(

---

### Post by timgood on 2010-12-15
> **BlueSpecial said:**
> 

1 - The machine won't shutdown. Rebooting works fine but shutdown it just hangs... Kinda sucks having to press the Power Off button every time...



Which wireless adapter is installed in your laptop? There is a known problem with some, including some RALink models. A fix for this is described in this [post]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103").

Hope this helps.

---

### Post by BlueSpecial on 2010-12-15
Many thanks.. I'm at work right now but as soon as I get home I will try that fix.

Anyone have an idea to fix point number 2?

---

### Post by Axolotl9250 on 2010-12-15
Only a suggestion with point two as I'm not quite sure, but if it's possible, reinstall (or even install) the battery module you tried to load, as you said it was invoked but not found. Maybe some sort of installation error with the module. That would be my initial thoughts.

---

### Post by BlueSpecial on 2010-12-15
> **Axolotl9250 said:**
> Only a suggestion with point two as I'm not quite sure, but if it's possible, reinstall (or even install) the battery module you tried to load, as you said it was invoked but not found. Maybe some sort of installation error with the module. That would be my initial thoughts.

Sorry for the noob question...

How can I do that?

---

### Post by rcayea on 2010-12-15
I know this doesn't fix the problem but I am curious if the machine hangs when you try the command, "sudo halt" without the quotes.

---

### Post by BlueSpecial on 2010-12-15
> **timgood said:**
> Which wireless adapter is installed in your laptop? There is a known problem with some, including some RALink models. A fix for this is described in this [post]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103").

Hope this helps.

Realtek

---

### Post by BlueSpecial on 2010-12-16
I'm sorry... no Realtek.... it's a SiS....

---

### Post by Spyderkid on 2010-12-16
can you install Firewall from the software centre and then go onto the application click "enable listening report" then say what it says in the box there should be 2 avahi-daemon processes open these are the things that help shut down the computer

---

### Post by kuvanito on 2010-12-16
as per the battery problem
i had some problems like this,battery not charging on a dell latitude
my problem was the charger,replaced it and all was good but i will also suggest to check the state of the battery.

---

### Post by BlueSpecial on 2010-12-20
> **timgood said:**
> Which wireless adapter is installed in your laptop? There is a known problem with some, including some RALink models. A fix for this is described in this [post]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103").

Hope this helps.

Unfortunately the problem persists even after trying this solution :(

> **kuvanito said:**
> as per the battery problem
i had some problems like this,battery not charging on a dell latitude
my problem was the charger,replaced it and all was good but i will also suggest to check the state of the battery.

The problem is not the battery. The battery charges. The problem is that I don't see any battery indicator... I miss the battery charge indicator when I'm working on battery only.

---

### Post by BlueSpecial on 2010-12-20
The shutdown and the battery issue are becoming a showstopper for me... :(

---

### Post by colobix on 2010-12-20
So the battery doesn't show up on your panel?
Have you removed the notification area? That's where the battery should be.
The shut down issue can be caused by things such as a huge cache folder that hasn't been recycled and not deleted temp files such as .deb archives from installed programs.
If you run sudo apt-get autoclean you will empty the cache.
If you have Ubuntu Tweak installed you can easily remove useless temp files.

Or if there is something wrong with a package on your system, that could also be the reason.
If you open up synaptic, and from the "edit" menu, go to Repair broken packages.

The first solution solved the problem for me when I had it back in ubuntu 9.10.

---

### Post by BlueSpecial on 2010-12-20
I didn't remove the notification area. :(

I will try to clean useless temp files to see if it fixes shutdown. Thanks ;)

---

### Post by BlueSpecial on 2010-12-23
> **rcayea said:**
> I know this doesn't fix the problem but I am curious if the machine hangs when you try the command, "sudo halt" without the quotes.

Still hangs!

I read somewhere in the net that by disabling the wireless drivers on the kernel and installing the property drivers might solve the issue. Any thoughts?

---

