---
title: "my computer seems to have deconfigured itself"
date: 2009-07-21
forum: General Help
---

### Post by daeiros on 2009-07-21
Ok not sure what information you need to help me, just ask and I'll do my best but bear in mind im still a fairly recent windows convert.
 
So I've been using ubuntu for a while now, and everything has been working great, until last night that is. I didn't do anything, no updates, no new installs or anything of that nature, I was playing flash games on a site I trust and I had been at it for quite some time, then midway through loading a new game, my internet disconnected and would not reconnect. Checked the router, everythings fine, other laptop is still connected so naturally, my next step was to reboot. thats when things went from bad to worse.
 
So I reboot, and now, my network manager icon is gone, simple enough, so i think, i just add it back to the pannel. so when the new icon apears, i click on it expecting to get a list of wireless networks to connect to. Nope. Instead i get the properties window for the lo connection. I right click to try to toggle the wireless enabled option, there is none. Ok my wireless didnt work out of the box, i had to get drivers, so I tried a wired connection, and that also did not work. ifconfig still shows my cards, but they arent listed in the dev folder or file or wherever i check, the file that the help file said my network card config should be in, the preview icon shows text, but when highlited it says 0 bytes and that is confirmed when i open it with a nice blank document.
 
so I dont really know what ifup or if down do exactly, but i gave those a shot and was got some sort of error message about acess denied, even when adding sudo before it, i know im getting more vauge as im getting more frustrated, ill elaborate anything you need me to with exact details. But come to find out, my network card isn't all that has suddenly stopped working, I try to mount my little storage partition, and nothing happens, its not listed under /media anymore, but that one i fixed by using disk manager, and it said that 2 partitions were detected and one was configured so i clicked configure and now that works just fine. Ok but my power manager is also broken(im on a laptop, guess thats important) nothing happens when I unplug or plug in, the battery icon does nothing, no mouseover text, nothing happens on a right click or a left click, I get an error message saying that my computer failed to sleep, and it says the power manager is not responding when I try to shut down.
 
So I figure that at this point, there isnt much I can do to fubar it more then it already is, and start trying things i read in the help to see if they make a difference, and I sat through a nice long dkpg reconfigure -all to no avail, everything is just as broken as ever, except one slight, itty bitty change, the power manager now works until i do anything, i can click it and change the setting and all that till i plug or unplug or try to sleep then it goes back to broke.
 
So.
I didnt do anything at all that may have changed anything, no updates, autoupdate is disabled, no installs, no websites of questionable security, just playing stupid little flash games on Kongregate, which is a fairly secure site, that I've never had a problem with in the two year ive been playing on it. No prompts came up asking for an administrator password, it was working one second, then disconnected and wont reconnect, and a reboot sealed the deal and screwed everything.
 
Any thoughts?

---

### Post by earthpigg on 2009-07-21
> **daeiros said:**
> 
Any thoughts?

let's rule out a sudden catastrophic hardware failure of a critical component:

how well do things work when running from the ubuntu live cd?

---

### Post by daeiros on 2009-07-21
well the cd has seen better days, its dirty and scratched because ive moved alot and havent taken proper care of it, might need to burn a new one, but when i try to run from the cd it just hangs indefinetly, on a livecd, install, or really any option i select from the menu, but it boots into the menu just fine, and it says something about not being able to connect to the livecd when it try to mount it if i put it in when im already logged in

---

### Post by daeiros on 2009-07-21
well it wasnt the gane i was trying to play, it works just fine on this computer. I dont think it was hardware failure either because everything still shows up, everything is listed by ifconfig, but its not listed anywhere else and it wont autoconfigure, so how do i do it manually?

---

### Post by daeiros on 2009-07-21
Alright, I'm in live CD mode now, and everything is working very nicely, I'm just going to reinstall because I was meaning to anyway, since I made the full switch and wiped out windows, because I had ubuntu on an extended partition, and I wanted to spread out into the newly freed space anyways, but couldn't transfer out of or resize the extended partition. 

I'd still like to know if anyone knows what happened and how to fix it though. Another note: I got another new message saying that I didn't have the authority to mount a drive, and gparted froze when trying to resize a partition, so my theory here, somehow, all my user rights were stripped down to the point that it wouldnt even let me use my network card or power manager properly, and this happened quite suddenly and unprompted and unprovoked. So if you have any idea what might have done this and how I can undo it if it happens again in the future, itd be greatly apprieciated. I'd still like to know how to solve the problem even though I have an effective workaround.

---

### Post by earthpigg on 2009-07-22
no idea how that might have happened :\

best of luck with the fresh install, though.... once you know the ropes a bit, a fresh install is usually a good idea. "who knows what noobish random thing i did that is waiting to pop its ugly head up?", was my thought when i was in your shoes.

---

