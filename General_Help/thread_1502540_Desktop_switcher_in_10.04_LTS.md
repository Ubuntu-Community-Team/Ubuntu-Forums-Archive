---
title: "Desktop switcher in 10.04 LTS?"
date: 2010-06-05
forum: General Help
---

### Post by Ernesto RD on 2010-06-05
Im considering installing Ubuntu Network remix 10.04 on my Dell mini10V, but i would like to have a choice to switch from the UNR style interface to the normal ubuntu one and back everytime i want to.
I know that in 9.10 the Desktop switcher utility was scraped due to serious bugs on previous versions, but i also heard that a new functional version would be included in 10.04.

So, Is there a way to switch desktop modes in 10.04 NRE?

thanks

---

### Post by acrazyplayer on 2010-06-05
Actually as long as you install "ubuntu-desktop" then when you go to log in to your computer after entering your user name you will see at the bottom a little box that says "sessions" and there is where you click what you want to log into.

---

### Post by CoreyB. on 2010-06-05
Not even that, just install Netbook Edition and you can change the session to "Ubuntu".

---

### Post by Ernesto RD on 2010-06-05
Thanks guys, one more question please...

And does it work properly this time? i remember that switching desktop modes in previous versions was 100% quick, simple AND broken! :)

---

### Post by acrazyplayer on 2010-06-05
The only way to really know is to just try it. As you can see on here many people have many problems with certain things that affect no one else, so I guess it boils down to luck sometimes.

---

### Post by Ernesto RD on 2010-06-05
well, i have an disk image of my current windows XP pro installation, If something doesnt work, i can go back to XP in 30 minutes, so i will give it a shot.

thanks for your help guys :)

---

### Post by whitecue on 2010-07-17
> **acrazyplayer said:**
> Actually as long as you install "ubuntu-desktop" then when you go to log in to your computer after entering your user name you will see at the bottom a little box that says "sessions" and there is where you click what you want to log into.

I installed the desktop and wanted the UNR too, but I only have xterm and failsafe gnome to choose from in the login screen, no UNR. So I managed to find this:

[https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/DesktopUNESession](https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/DesktopUNESession)

so just run

sudo apt-get install ubuntu-netbook

in the terminal and after a while you will be able to choose from standard gnome and netbook remix at log in screen. Just thought I'd make this thread more complete for future users:)

---

