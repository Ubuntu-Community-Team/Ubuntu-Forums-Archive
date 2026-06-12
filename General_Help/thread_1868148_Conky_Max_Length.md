---
title: "Conky Max Length?"
date: 2011-10-23
forum: General Help
---

### Post by kainalu on 2011-10-23
Hello Community,

I use the Conky sysmon. I love it, but I recently tried to fill it out with some more data, and it seems to me that it has a capped length. It simply will not go to the bottom of my screen, and instead clips my data off.

I have attached a PNG of the issue. (Image is cropped to problem area for file & image size restraints) Any ideas?

---

### Post by kemtnbkr on 2011-10-23
I'm having the same problem here.  I can't see any options in the config file that would affect this at all, but maybe I'm missing something, I just started messing with Conky the other day.

---

### Post by kainalu on 2011-10-23
As far as I can tell the only things that could do it are :

minimum_size 216 5
maximum_width 220

gap_x 5
gap_y 0

But they are all set to variables consistent with what I want...as far as I know...

---

### Post by kemtnbkr on 2011-10-24
Comment number 7 here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

It looks like this guy got his longer than mine can be, but I see nothing in the code that would effect that that I don't have...

Another weird thing just happened to me.  Mine didn't display entirely, but then I reloaded Conky and it all showed up- nothing changed though.  I also can't see anything that the minimum_size and minimum_width effect.

Mine also might not be the best representative to experiment with as I'm running Lubuntu, so I have to manually start it because I haven't found a way to get the startup scripts to include it yet.  But I have to have some different settings for it to work with openbox/ pcmanfm, and I don't have it fully figured out- if I accidentally click on the background, Conky disappears!  It gets pushed 'behind' my desktop wallpaper; I guess I might be able to make a transparent wallpaper, but I don't like ugly hacks like that.

Anyways, that's my long-winded story :)

---

### Post by kainalu on 2011-10-24
For the clicking the desktop thing, add this up top if you haven't already, ABOVE the word TEXT

```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
```

You have to do that on GNOME, don't know about LXDE, but it don't hurt to try.

As for the autostart, this should work. I don't run LXDE, but after looking at how to create startups for LXDE online, I created a script that should work. Attached here. Simply mark it as able to run as a program and then run it in a terminal.

---

### Post by kemtnbkr on 2011-10-24
Wow, thanks for the effort!  I can't try it right now because I'm at work, but I'll try it later today.  

I was looking to see if anyone else has had this issue; I've found a few older threads back to '06ish, although none had a solution.

One guy said his issue was fixed when he changed the window type from normal to desktop; what is yours set at?  Mine was truncating the display even set at desktop before, I think.

I'm not 100% sure on that, though, I can't remember, I'll have to look when I have access to my machine.

---

### Post by Flymo on 2011-10-24
I'm usually trying to go the other way - finding what to truncate so that conky is not too wide for my screen.

Let us know how you get on!

---

### Post by kemtnbkr on 2011-10-24
Thanks kainalu, your solution worked!  

I didn't have the own_window_hints line before, and that fixed the hiding issue.

Your script almost worked, except the copy line pointed at /usr/share/applications.desktop instead of /usr/share/applications/conky.desktop (the newly-created file).  Either that or I'm too much of a n00b to know what even should be happening.

I didn't know at first what was happening so I just modified the script to dump straight into /home/kyle/.config/autostart/conky.desktop, and once I had conky.desktop in there, it worked fine.  Also the 'double_buffer yes' made it quit flickering entirely; I had it (almost) not flickering before, but not quite completely.

I'd also like to apologize for hijacking your thread; you ended up helping me with all my issues, and I couldn't even come up with an idea for one of yours :(

Thanks again, though :)  I'll keep my eyes peeled for a solution to your issue.

---

### Post by kainalu on 2011-10-25
Hijacking? you kept it at the top of the heap so more people could read it. like bumping for free! :D In any case, I love to help. Fixes the karma and all... 

Sorry about the script, I wrote it in like two minutes. I don't have LXDE so it is hard to plan for everything, but I should have caught such a big error. I'm glad you caught it and it works. If you want a conky icon for your applications menu, you can copy the one from your home folder to /usr/share/applications/conky.desktop, and it should show up in the applications menu next time you log in...if I understand LXDE to be the same as GNOME in that respect.

Glad it works for you!

--Kainalu

---

