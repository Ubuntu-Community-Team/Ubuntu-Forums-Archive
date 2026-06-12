---
title: "need help installing songbird with gdebi"
date: 2009-07-29
forum: General Help
---

### Post by xpinsx on 2009-07-29
ok. so i've downloaded the .deb package for songbird to my desktop. i've tried installing it with dpkg in terminal, but it tells me "cannot access archive: No such file or directory." i'm not sure what i'm doing wrong here. so then i tried using the gdebi package installer, and get to the window that give me the button to install. i click it, and my computer freezes. this has happened close to 20 times now... so then i went to synaptic and looked for other package installers. i found one called gdeb, and installed it. when i went to install songbird with it, it prompts me to enter my password, i enter it, and nothing happens. i tried that a few times, but i'm stuck. i'm really not sure what else to try. i recently just wiped my hard drive and reinstalled jaunty due to other issues. help would be nice, because i really like song bird and it works great with my ipod. help would be appreciated

---

### Post by jmszr on 2009-07-29
xpinsx,

Try downloading Songbird 1.2.0 from here: [http://www.getdeb.net/search.php?keywords=songbird](http://www.getdeb.net/search.php?keywords=songbird) . There are Jaunty 32-bit or 64-bit versions ** Note:If you have an NVIDIA graphics card you may need to remove the libvisual-0.4-plugins package ** ( warning from site) When Songbird downloads "Open with GDebi Oackage Installer and see how that works.

Perhaps that will do it.

Edit: Please go into Synaptic first and make sure there is no Songbird installed.

---

### Post by xpinsx on 2009-07-30
that still froze my computer. and it isn't just the songbird package....it's any .deb package that i download and try to install. i'm really not sure what's wrong. this is the first time i've ever had ubuntu do this to me, and i've installed it on multiple computers

---

### Post by jmszr on 2009-07-31
xpinsx,

Are you able to install anything using Synaptic or Applications > Add/Remove?

---

### Post by xpinsx on 2009-07-31
i can use synaptic and add/remove software. just not gdebi

---

### Post by jmszr on 2009-07-31
xpinsx,

You might try removing GDebi and then reinstalling it. Besides that, I really don't have any ideas. Google didn't turn up anything relevant. Hopefully someone on these forums will know.

---

### Post by MaxIBoy on 2009-07-31
I can think of a few things which could result in the error you mentioned:

[LIST]
[*]You saved the file somewhere, but you didn't tell the terminal *where* you saved it. So if the file is on your desktop, and you just typed "sudo dpkg -i songbird.deb", that won't work.
[*]You didn't save the file anywhere specific, so it went to /tmp by default. Then you rebooted. When that happens, /tmp is cleared out (because it's specifically for temporary files.) However, the file would still show up in the download list under Firefox.
[/LIST]


Try it this way:

First download the file and save it somewhere, for example your desktop.

Then, pull up a terminal and type this in:
```
sudo dpkg -i 
```
Then drag-and-drop the icon for the .deb file into the terminal, so that it looks something like ```
sudo dpkg -i '/home/whatever_your_username_is/Desktop/songbird.deb'
```
Then hit enter.

If it still doesn't work, copy and paste the *entire* output of the program into a post so we can look at the error message and figure out what's wrong.

---

### Post by xpinsx on 2009-07-31
thank you so much! i got it installed using dpkg, but i'm still a bit confused as to why gdebi or gdeb won't work

although one thing... songbird doesn't seem to want to load. i click on the icon and it just sits there. if i click on it again, it says "Songbird is already running, but is not responding. To open a new window, you must first close the existing Songbird process, or restart your system." i seem to remember having this problem before though, so i may just need to reboot a few times. and i also remembered that my gdm screen manager would cause my computer to crash when i loaded it. i wonder if it could somehow be related to gdebi


ok....so i got songbird working by removing libvisual-0.4-plugins (duh) and deleting the .songbird2 folder. still no luck with gdebi though

---

