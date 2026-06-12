---
title: "Windows Ubuntu connection"
date: 2009-06-26
forum: General Help
---

### Post by alejiss on 2009-06-26
i have two hard disks, one of them with ubuntu 9.04 and the other with vista. is there a way to run windows programs on ubuntu?

i had wine but it seems you need to instal the windows program on the ubuntu hard disk to run it.

---

### Post by diegogto on 2009-06-26
actually haven't done it... but, what if you point your wine's C:\ to your windows partition?

There may appear some errors in wine, I don't know for sure. Just an idea.

---

### Post by Nburnes on 2009-06-26
All I know about is wine, so I really cannot helo you here.

Would be interesting to find out if it is possible.

---

### Post by alejiss on 2009-06-26
Wine only reads 2 directories in the programs files directory in the vista hard disk.... common files and internet explorer.  and i have a lot of programs there....

I dont know if the fact that wine is not upgraded to vista has anything to do with this..

---

### Post by themusicalduck on 2009-06-26
Some programs work and some programs don't. The only difference between running already installed programs and programs you install within wine is that any registry entries that are normally made on install won't be present in the wine registry. So if the program is absolutely dependent on a registry entry being there then it might throw out an error. I run WoW on my XP partition fine without reinstalling it in Ubuntu. 

After installing wine just double click on the .exe in your vista partition and see if it works. You can make a shortcut to a .exe file with the command wine /path/to/exe . Except you need to mount the partition before clicking the shortcut.

It's a bit strange if you can't see your program files in the Vista partition.. Are you running 64 bit vista? Then most of the programs are installed in Program Files (x86) instead of the actual Program Files folder.

---

### Post by ajgreeny on 2009-06-26
Occasionally it is possible to run the executable in your windows install using wine on your ubuntu install, but it is very hit & miss.  I certainly did it with Irfanview v4, which I used in windows before I started using ubuntu, but there were a lot of other executables which did not run that way.

EDIT:  Too slow again!

---

### Post by alejiss on 2009-06-26
thanks for your help!! but it didnt work... i want to open windows programs on ubuntu........   as themusicalduck i tried to execute exe's but it didnt work, i wonder why when i browse the vista hard disk with wine it doesnt recognize the actual directories i have on it...but i do see them whem i browse them with nautilus

actually i am thinking to install a vmware on ubuntu to run windows and reintall all the windows programs on it... deleting the windows i have on my second hard disk....

---

### Post by alejiss on 2009-06-26
hey thanks!!!

as themusicalduck suggest


i mounted the vista hard disk.. then I made shortcuts for the exe files i wish to use (wine /path/to/exe)... and its done!

---

### Post by themusicalduck on 2009-06-26
You can browse and run .exe files from nautilus. I'm not sure how you even browse a drive from wine. It doesn't have a file browser built in as far as I'm aware..

Just to check did anything come up when you clicked on the .exe? If nothing happened at all then there was probably a problem of some kind. You can get more information about an error normally if you run the .exe from the terminal with the command wine /path/to/exe

Otherwise you might just have to reinstall the program in wine.

Also it sometimes helps to run a newer version of wine if you aren't already which you can get following the steps here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

edit: I just read your new post.

I think what you might be doing is clicking on Browse C:/ Drive in the wine entry under Applications? This doesn't browse your vista drive but it opens a virtual Windows drive that is stored in your home folder. If you installed a program using Ubuntu then it will appear here. That shortcut just takes you to the virtual windows folder in nautilus which is not your Vista partition.

VMware will work for running Windows programs. I prefer to use Virtualbox. But it might be worth just trying to reinstall the programs in wine first. Is there a specific program you want to use?

---

### Post by alejiss on 2009-06-26
actually i was willing to use Adobe suite, but it didnt work.... however it did work as you said with starcraft. i have the last ver of wine.. 

thanks!

---

### Post by diegogto on 2009-06-26
> **themusicalduck said:**
> 
I think what you might be doing is clicking on Browse C:/ Drive in the wine entry under Applications? This doesn't browse your vista drive but it opens a virtual Windows drive that is stored in your home folder. If you installed a program using Ubuntu then it will appear here. That shortcut just takes you to the virtual windows folder in nautilus which is not your Vista partition.

As I said before, you can point your wine's drive to your vista partition on applications->wine->configure wine, then click on "drives". You need to have your vista partition mounted, then it can be *mounted on wine*. I couldn't mount it as wine's C: drive. Maybe reinstalling wine.

> **themusicalduck said:**
> VMware will work for running Windows programs. I prefer to use Virtualbox. But it might be worth just trying to reinstall the programs in wine first. Is there a specific program you want to use?

I do prefer Virtualbox, you just have to find it in applications -> Add/Remove... search for virtualbox... (at least in jaunty)
If that doesn't work (i don't remember how i installed it) you can google "howto install VirtualBox"

---

