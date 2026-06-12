---
title: "winetricks!"
date: 2009-07-06
forum: General Help
---

### Post by Find on 2009-07-06
Hello,

I installed wine, and then i managed to install MS Office 2007, Word works fine, but Excel crashes! and I have no clue why, I'd appreciate if someone gives any hint!

Googling for "a" solution i got to this link
[http://menelkir.wordpress.com/2008/04/09/installing-microsoft-office-2007-using-wine/](http://menelkir.wordpress.com/2008/04/09/installing-microsoft-office-2007-using-wine/)
which 'proposes' to install 
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
now three questions,
1: how can i run a code like this?!
2: before running such a code, how can i make sure it is not something which i should avoid?!
3: and if there is not an easy way to find out the harmfulness of such a code, is this one safe?!

Thank you
Find!

---

### Post by Jebtrix on 2009-07-06
When you load that page just copy and paste into a text file. Save it as winetricks.sh. In terminal navigate where you saved the text file do: 

```
sh winetricks.sh
```

---

### Post by Jebtrix on 2009-07-06
It doesn't run as root, so its relatively safe. I've used it many times. I would make a copy of /home/<username>/.wine folder as a backup first.

---

### Post by Tibuda on 2009-07-06
Read [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

I would worry more about this:
> Note: Although using winetricks may be very useful for getting some programs working in Wine, doing so may limit your ability to get support though WineHQ. In particular, reporting bugs may not be possible. See Reporting bugs after you have used Winetricks below. 

---

### Post by 67GTA on 2009-07-06
When you open a terminal it defaults to your /home directory. If you save the file there, you can just run the command Jebtrix gave without worry about which directory your in. Just for future reference, if you saved the file in /usr/bin, you would move to the /usr/bin directory with ```
cd /usr/bin
``` and then run the command.

---

### Post by Jebtrix on 2009-07-06
True, I only use winetricks *after* checking winehq support doesn't resolve it. Its also the reason I backup ~/.wine folder. If winetricks doesn't help, I just restore the backup.

---

### Post by 67GTA on 2009-07-06
> **Jebtrix said:**
> True, I only use winetricks *after* checking winehq support doesn't resolve it. Its also the reason I backup ~/.wine folder. If winetricks doesn't help, I just restore the backup.

That's very good advice. I've totally screwed wine up before with winetricks. If you don't really need something from winetricks, don't install it.

---

### Post by Jebtrix on 2009-07-06
> **67GTA said:**
> When you open a terminal it defaults to your /home directory. If you save the file there, you can just run the command Jebtrix gave without worry about which directory your in. Just for future reference, if you saved the file in /usr/bin, you would move to the /usr/bin directory with ```
cd /usr/bin
``` and then run the command.

If you want to make winetricks a 'permanent fixture' I would save it without the .sh extension. Then in terminal

```
chmod +x winetricks
sudo mv winetricks /usr/bin 
```

Then you can just type winetricks anytime in terminal or make a launcher with winetricks as command.

---

### Post by Jebtrix on 2009-07-06
> **67GTA said:**
> That's very good advice. I've totally screwed wine up before with winetricks. If you don't really need something from winetricks, don't install it.

Yeah, it sure can depending on what component you needed. I find the comctrl32 'package' to be the most helpful (like for Notepad++).

---

### Post by stinger30au on 2009-07-06
> **danielrmt said:**
> Read [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

I would worry more about this:

have you had a read thru the wine hq database and see what you need to make office run, i think u will find you need to install winetricks

---

