---
title: "Quick questions before getting started."
date: 2012-10-03
forum: General Help
---

### Post by Twilk73 on 2012-10-03
Switching to Ubuntu. 

I am running windows 7 and I use two main programs cc cleaner and disk defraggler. Do I need similar programs for ubuntu? If I recall correctly from my research Link doesnt use the same file storage as windows and thus never needs defraged is that true or false. Also is there a similar program to cc cleaner for ubuntu? And lastly are there any tools you guys suggest to keep my laptop running at optimum performance or tweaks maybe?

---

### Post by Bucky Ball on 2012-10-03
Welcome. Most of that is not required, the defragger definitely not. Don't know anything about CC but your Ubuntu machine should be running at optimal always once setup.

There are several programs that can clean up non-required bits, Bleachbit to name one, but really, you can do a lot from a terminal with one command:

```
sudo apt-get autoremove
```That will remove pretty much everything not required. Remove programs you don't use after about a month then run that command. Easy.

Your best bet is to focus on how Linux works and forget too many comparisons with Win. Download the ISO and make a LiveCD. Boot from that and you will get to a desktop. Play around for awhile and get the feel, see if you like. If so, there is an 'install' icon on the desktop. They're not slip in replacements and absolutely not the same (well, they both have folders, files and programs I guess). ;)

PS: If the standard Ubuntu 12.04 LTS (supported until April 2017) is not to your liking (some don't like the desktop environment, Unity) there are other options. You might try Lubuntu, Xubuntu, Kubuntu, that's going from lightest to heaviest as far as use of resources goes.

 If you have a low-spec machine, Lubuntu or Xubuntu are the go. If you have a something more powerful, you could try Kubuntu for the bells and whistles experience! Resource hungry though. 

There are heaps of options and you can even run one flavour with a desktop environment used by another, xfce4 used by Xubuntu in Ubuntu for instance. Good luck.

---

### Post by Twilk73 on 2012-10-03
Thanks. 

Yeah i plan to just mess around a bit and play. I installed it once before and jjst tried to learn everything off the bat. I got so boggled i just ended up removing it for a later date. Anyway now i have a new asus g75 with more space and the specs are superior to my old thinkpad t61.

12gb ram, 500gb hard drive, win7 64bit, nvidia 660m gfx card

Anyway i already know i like ubuntu/linux iv been in love with the idea of linux forever and ubuntu is a pretty cool os. Nice and easy for us newbies too. 

Right off the bat ill be working on getting the logitech g700 setup, iv hear the pointer speed on linux works faster than windows. Next ill work on getting all the hot keys from the asus laptop setup if possible. After that i just got to get java working so i can play tankpit.com lol than ill just have some fun probably play around with the u.i. and hopefully lear the new language of the file system over time. 

That probably sounds like a lot but trust me its far from the objective list i had last time.

---

### Post by Bucky Ball on 2012-10-03
Sounds good and relaxed. Once you're using it in a basic setup you learn things as you go in the process of customising it into the ideal hybrid beast! Um, I mean computing environment for you. Enjoy the learning curve and the OS ... ;)

---

### Post by CapnKirk on 2012-10-04
> **Twilk73 said:**
> Switching to Ubuntu. 

I am running windows 7 and I use two main programs cc cleaner and disk defraggler. Do I need similar programs for ubuntu? If I recall correctly from my research Link doesnt use the same file storage as windows and thus never needs defraged is that true or false. Also is there a similar program to cc cleaner for ubuntu? And lastly are there any tools you guys suggest to keep my laptop running at optimum performance or tweaks maybe?

Re: cc cleaner

Isn't that the registry cleaner? Linux doesn't have a registry. But as others have noted, the "apt-*" series of utilities handles all the package management. I suppose the functionality of the Windows registry is provided by all the configuration files in /etc.

HTH,

Kirk

---

### Post by Twilk73 on 2012-10-04
Yeah its a registry cleaner. It performs a bunch of diff cleaning tasks as well though. Like temp files, prefetched files if you have that on. Its a serious clean of any and all junk. Its a pretty great program. It can also be used to clear old restore points, check start up programs, uninstall things. Honestly, everything you can do with ccleaner you can do with the pc regularly. Ccleaner just puts it all in one simple package. I really only use it to clean the reg files and the all junk off the pc. Its easier than doing sagerun50, cleaning the temp and prefetched out individualy because its just a one click and done thing. I am usually not a fan of programs like these but this one does the job fast, easier and extreamly well to not use it.

---

### Post by Bucky Ball on 2012-10-04
Not required. Never used anything like it in Linux. When you kill a program it is pretty much killed. Doesn't generally leave junk everywhere like a Windows lunar landing. Doesn't really work that way (although you could get pretty messy with effort).

---

### Post by greenpeace on 2012-10-05
hi!

I would heartily recommend the "Ubuntu Tweak" program.  This comes with, amongst other configurations and tools, a "janitor" section which helps you remove unwanted temp files and caches of data.

Although I would stress that you probably won't need to do as much system maintenance as you seem to be anticipating!  

Hope that helps,

g

---

### Post by Bucky Ball on 2012-10-05
> **greenpeace said:**
> 
Although I would stress that you probably won't need to do as much system maintenance as you seem to be anticipating!  

+1. Ubuntu Tweak janitor and Bleach Bit (but be careful with that) are about all you'll need, if you ever need them.

---

### Post by fyfe54 on 2012-10-05
This was originally (as far as I can tell) known as Crap Cleaner, which pretty much describes perfectly hat it actually does.

---

### Post by Twilk73 on 2012-10-07
Thanks guys, awesome tips.

---

