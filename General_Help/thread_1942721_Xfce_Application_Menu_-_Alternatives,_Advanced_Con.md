---
title: "Xfce Application Menu - Alternatives, Advanced Configuration?"
date: 2012-03-18
forum: General Help
---

### Post by ohnonot on 2012-03-18
Hello,
I'm rather unhappy with the default App menu in xubuntu 11.10.
I tried to install 3 alternatives: mintmenu, GnoMenu and cardapio but none worked - it seems they all depend on gnome-desktop components which i am not willing to install.

are there any alternatives to the default menu?
is it possible to configure it further than what is offered in the properties gui?
i'm particularly interested in speeding it up. i think loading it into ram would be good.

any suggestions?

asks a semi-nerd-noob.

---

### Post by WasMeHere on 2012-03-18
If you want speed, try LXDE, and you will get a choice between XFCE and LXDE at the login screen.
```
sudo apt-get install lxde
```
LXDE is a desktop environment with a very small footprint, so it is fast. But it is not as complete as XFCE, so try LXDE, and if you don't like it, you can purge it.

---

### Post by ohnonot on 2012-03-18
thanks, i had tried lubuntu before (as well as ubuntu and mint fluxbox and others) but i found it too light.
xubuntu offers the best from both extremes, to me.
anyhow other things are running smoothly, it's the menu that lags. and is not customizable.

btw, olle wiklund, i believe we had the pleasure of meeting earlier on this forum?

---

### Post by WasMeHere on 2012-03-18
> **ohnonot said:**
> thanks, i had tried lubuntu before (as well as ubuntu and mint fluxbox and others) but i found it too light.
xubuntu offers the best from both extremes, to me.
anyhow other things are running smoothly, it's the menu that lags. and is not customizable.

btw, olle wiklund, i believe we had the pleasure of meeting earlier on this forum?
Yes, we have seen each other's posts, but I cannot remember what topic we were writing about.

I have not tweaked the Xubuntu menu system, let us hope there is someone with experience how to tweak it, who can help you with the menus :-)

---

### Post by mike555 on 2012-03-18
you should open package manager , in Settings, Preferences, uncheck "consider recommends as dependencies ", then install "Alacarte" .......... it should only install a couple of small things , and then show in you menu in Settings, Main Menu.

---

### Post by The Cog on 2012-03-18
sudo apt-get --no-install-recommends install alacarte

If you forget to tell it not to install recommends it wants to install loads of stuff, including mono which I won't have on my computers.

---

### Post by ohnonot on 2012-03-18
thanks mike555 & the cog -
i have alacarte installed already, but it only allows to edit menu items, not any "performance tweaks" or "advanced settings".
actually, it only lets me de/activate existing entries - the buttons "properties" and "new item" do nothing...

still searching, still wondering-

---

### Post by brainwash on 2012-03-18
Not an expert myself, but maybe you could make the menu feel more snappy by "preloading" the .desktop files everytime you boot the system. Something like this here:

> for i in /usr/share/applications/*.desktop; do
  cat $i > /dev/null
doneDid not test it though.

---

### Post by ohnonot on 2012-03-19
> **brainwash said:**
> Not an expert myself, but maybe you could make the menu feel more snappy by "preloading" the .desktop files everytime you boot the system. Something like this here:

for i in /usr/share/applications/*.desktop; do
  cat $i > /dev/null
done                      

Did not test it though.
interesting. gave me this output:```
cat: /usr/share/applications/copy: No such file or directory
cat: of: No such file or directory
cat: ardour.desktop: No such file or directory

```- not sure if it actually did anyting. the folder in question is full of .desktop files.
so the idea is to copy the desktop files to RAM?
how would the menu know to find them there?
would i have to do that only once at bootup?

---

### Post by LewisTM on 2012-03-19
> **brainwash said:**
> Not an expert myself, but maybe you could make the menu feel more snappy by "preloading" the .desktop files everytime you boot the system. Something like this here:

Did not test it though.

This won't work if there are spaces in the .desktop filenames
This might work better and is simpler:
```
cat /usr/share/applications/*.desktop
```
You don't need the [FONT="Courier New"]> /dev/null[/FONT] if you just want to run it at startup since there will be no terminal to show the output. It won't actually move the files to memory, it will just read everything from disk so it is cached in memory for faster access once you open the menu.

You could also flash the menu at startup with this command (needs package xdotool)
```
sh -c "sleep 5 && xfce4-popup-applicationsmenu && xdotool key Escape"
```
That will launch the Xfce menu, read all necessary files, popup and immediately close.

To the OP, please do no duplicate threads, I know this is the same topic as this [thread]("http://ubuntuforums.org/showthread.php?t=1940316"). 'Bumping' up a thread to the top by posting a *bump* comment might be acceptable if not done abusively.

---

### Post by ohnonot on 2012-03-22
> **LewisTM said:**
> To the OP, please do no duplicate threads, I know this is the same topic as this [thread]("http://ubuntuforums.org/showthread.php?t=1940316"). 'Bumping' up a thread to the top by posting a *bump* comment might be acceptable if not done abusively.
you are absolutely right - though the threads started off with differnt intentions, the intentions have swapped... i'll try to be more precise-
:D

about the rest, the cat command doesn't seem to help any.
though it's fascinating that you can do sth like that in linux.

also the menu isn't slow only the first time i pop it up but *every now and then*.
so xtodo can't solve that.

i'm beginning to just accept the slow menu as a fact.

mayb sometime i'll install some docks and see what they offer.
well thanks for the help (again)!!!

---

### Post by Disident on 2013-01-10
> **ohnonot said:**
> interesting. gave me this output:```
cat: /usr/share/applications/copy: No such file or directory
cat: of: No such file or directory
cat: ardour.desktop: No such file or directory

```- not sure if it actually did anyting. the folder in question is full of .desktop files.
so the idea is to copy the desktop files to RAM?
how would the menu know to find them there?
would i have to do that only once at bootup?

```
cat "$i"
```

When you don't put $i in quotation marks it will have problems with spaces in names.

---

