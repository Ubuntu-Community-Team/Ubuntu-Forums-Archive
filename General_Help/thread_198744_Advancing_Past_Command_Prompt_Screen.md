---
title: "Advancing Past Command Prompt Screen?"
date: 2006-06-17
forum: General Help
---

### Post by wind0s on 2006-06-17
I *finally* got ubuntu installed on my laptop, but for some reason, I can't get past the command prompt screen. How do I get so that I can actually see icons for programs and a more user-friendly display?

---

### Post by maniacmusician on 2006-06-17
chances are that you don't have an actual desktop environment installed. To get one (or all) of the three basic environments, which are Ubuntu, Kubuntu, and Xubuntu, here's the code you would use:

To get the Gnome desktop environment (which would be ubuntu):
```

sudo apt-get install ubuntu-desktop

```

To get the KDE desktop environment (which is Kubuntu):
```

sudo apt-get install kubuntu-desktop

```

And to get the Xfce desktop environment (Xubuntu):
```

sudo apt-get install xubuntu-desktop

```

---

### Post by Lord Illidan on 2006-06-17
Once you login, type startx

---

### Post by wind0s on 2006-06-17
It gives me an error:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

---

### Post by wind0s on 2006-06-18
Help?

---

### Post by Ramses de Norre on 2006-06-18
What's the X server output it's talking about?

---

### Post by wind0s on 2006-06-18
I have no idea? It's just the error message I've been getting. Is there something I should look for if I opt to view the output?

---

### Post by jimmygoon on 2006-06-18
[QUOTE=wind0s]I have no idea? It's just the error message I've been getting. Is there something I should look for if I opt to view the output?[/QUOTE]

The message(s) at the end of it when you scroll down. anything that gives an indication of what causes the Xserver to die? what kind of PC do you have, or more importantly graphics card?

---

### Post by aysiu on 2006-06-18
This should help you:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by wind0s on 2006-06-18
I followed the instructions, but it still does not work.

Someone with the same laptop as me said that it was easier on our machine to install Dapper Drake Flight 6 and upgrade from there. Flight 6 is no longer on ubuntu.com, and the torrent spy torrent I got did not start.

Any suggestions?

---

### Post by joshrobinson on 2006-06-18
im guessing your xserver isnt set up right, or is trying to run an incorrect video driver.. what kind of video chipset is in your laptop? ati? nvidia? intel? you can always try to reconfigure the xserver, but you should know what driver you want to run

you can always try vesa, that seems to work for pretty much everything

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by wind0s on 2006-06-18
Intel GMA 950

I've tried Reconfiguring, but it gives me an error halfway through and doesn't seem to help. Is there anywhere that still has Flight 6?

---

### Post by wind0s on 2006-06-19
Is there some host not easily viewable from google that still has it?

---

