---
title: "How do I install fonts manually?"
date: 2006-05-05
forum: General Help
---

### Post by Norppa on 2006-05-05
How do I install fonts that I already have on disc? Is there a folder I just need to copy them (like in Windows), or is it more complicated? Please help!

*U - B - U - N - T - U - 4 - L - I - F - E - !*

---

### Post by racoq on 2006-05-05
Don't, give yourself to much work to install fonts. There is a better solution.
Install Automatix, it has a option that installs all windows font's like Times new Roman, Arial, Etc...

Fore more detail, see this topic:

Automatix (Automated GUI installation script)

[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

:-({|= 

I think these fonts will be enough to you

---

### Post by Norppa on 2006-05-05
Thanks, but I already have Automatix installed. The reason why I want to install these fonts is that I have many special fonts on my hard drive that I would like install on my Ubuntu. How would this be done? Or can it be done?

---

### Post by kaamos on 2006-05-05
Try moving the font files to /home/username/.fonts and running the command "fc-cache"

---

### Post by MiniJames on 2006-05-05
usr/share/fonts

---

### Post by mcduck on 2006-05-05
[QUOTE=Norppa]Thanks, but I already have Automatix installed. The reason why I want to install these fonts is that I have many special fonts on my hard drive that I would like install on my Ubuntu. How would this be done? Or can it be done?[/QUOTE]
Make a directory called .fonts inside your home directory (if there isn't one already), put the fonts there, log out and log in. Your fonts work now. 

If you want to install the font for all users, I think the right place would be /usr/share/fonts or something like that..

Oh, files and folders with a . in front of the name are hidden, so you need to check 'show hidden files' in nautilus to see them..

---

### Post by medya on 2006-05-05
I have the same problem I need to install some Kurdish fonts , (Automatix is not Everything) ... please tell me how to install

I tried to go to ://fonts in file manager but I can not Paste any Font file there... I dont know why.

---

### Post by parktownprawn on 2006-05-05
The easiest way is to put the fonts in the .fonts directory in your  home directory and restart gnome.

You can also open a terminal and type 

```
nautilus fonts:///
```

and drag and drop the fonts into the nautilus window that opens up.

Then you either need to restart gnome or type something like

```
fc-cache -f
```

you may need to make a .fonts directory

type 

```

cd ~/
mkdir .fonts

```

for a system wide installation

for a system-wide installation type
```

sudo mkdir /usr/share/fonts/myfonts
sudo cp wheremyfontsare/*.ttf /usr/share/fonts/myfonts/
sudo fc-cache -f

```

---

### Post by parktownprawn on 2006-05-05
also see [https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto)

---

