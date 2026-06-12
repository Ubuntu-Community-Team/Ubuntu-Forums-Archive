---
title: "I did a bad, bad thing..."
date: 2010-12-15
forum: General Help
---

### Post by Karl10 on 2010-12-15
[FONT="Comic Sans MS"]Ohhh, I think I did it now !!   I had a perfectly good install of 10.10 in place and running mostly fine.

I stumbled across Unity while reading a blog about Ubuntu switching user interface over to Unity.  Being the curious sort, I wanted to take it for a spin and kick the tires to see if I should be outraged or not at this impending switch.

I was led to believe that the Unity install would show up as another choice in Grub at bootup.  It didn't, and I hit my regular boot choice with an "oh, well."

Yah, right.  It booted up alright - - into Unity !!  It runs horrible, mouse is twitchy, it's jerky and slow and My ATI Radeon doesn't like it and neither do I.

I'd love to pull it out cleanly, leaving me back in my original 10.10 install as it was, but "SURPRISE !!" I don't know how to do that (maybe shoulda thought of that FIRST....).

Here are the commands I used to shovel it IN:[/FONT]

[FONT="Fixedsys"]sudo add-apt-repository ppa:canonical-dx-team/une
sudo apt-get update && sudo apt-get install unity[/FONT]

[FONT="Comic Sans MS"]So have I scr3w3d the pooch, or is this a recoverable lapse of judgement??

Unhappy Me[/FONT]

---

### Post by guildofghostwriters on 2010-12-15
Have you tried
```
sudo apt-get remove unity
```
?

---

### Post by qamelian on 2010-12-15
You can revert to the regular Gnome interface by logging out and selecting the option for Desktop Edition from the menu that appears at the bottom of the login screen after you enter your username.

---

### Post by cracker89 on 2010-12-15
> **qamelian said:**
> You can revert to the regular Gnome interface by logging out and selecting the option for Desktop Edition from the menu that appears at the bottom of the login screen after you enter your username.

@qamelian: Lol, no offence meant, but that just goes so well with ur profile picture.:lolflag:


Cheers..

---

### Post by qamelian on 2010-12-15
> **cracker89 said:**
> @qamelian: Lol, no offence meant, but that just goes so well with ur profile picture.:lolflag:


Cheers..
No offence taken. :)

---

### Post by Karl10 on 2010-12-15
@guildofghostwriters:  Thanks; it seems obvious enough in hindsight....  I'm not nearly as good with the command line yet as I plan to be.

Okay, Unity is gone (uninstalled), but still shows up as my desktop.  Is/are there files to be edited go load the standard interface?

Karl

---

### Post by Karl10 on 2010-12-15
Hi qamelian

I've logged out, but all I have is a black screen, like in terminal (or DOS), no menu at screen bottom.

???

---

### Post by mr clark25 on 2010-12-15
try
```
startx
```

---

### Post by qamelian on 2010-12-15
> **Karl10 said:**
> Hi qamelian

I've logged out, but all I have is a black screen, like in terminal (or DOS), no menu at screen bottom.

???

So, you no longer get the GDM login screen? What about if you reboot?

---

### Post by Karl10 on 2010-12-15
Hey Mr Clark 25

Thanks for that.  I stubmled across it about 10 minutes before I came back here.  It did indeed restore the 10.10 GUI, but a bare-naked generic desktop, not MY GUI with all my settings and folders and such.  I can see all that in file manager, but for some reason my old settings aren't loading.  I'm sure there's some file(s) somewhere just off root that needs a little editing.  Just need to find out which one(s).

Any command-line gurus out there?

---

### Post by potat on 2010-12-15
First try
```
sudo apt-get remove unity
```
if you haven't already, and reboot your computer.
Everything _should_ go back to normal after that.

---

### Post by karmila on 2010-12-15
I think the best way to revert changes from an installed ppa is with using ppa-purge. It not only remove installed packages from that ppa but also redownload and reinstall previous packages that had been removed or upgraded because of that ppa.

You can install ppa-purge with
```
sudo apt-get install ppa-purge
```

And purge a ppa with
```
sudo ppa-purge [ppa-name]
```

---

