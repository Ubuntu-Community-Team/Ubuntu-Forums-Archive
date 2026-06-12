---
title: "Help with installing Mono 2.8?"
date: 2012-07-15
forum: General Help
---

### Post by Stonecold1995 on 2012-07-15
I'm trying to run [this]("https://www.youtube.com/watch?v=so64S8XAySQ") screensaver through Wine, but I'm having troubles.  When I try to run it through Terminal, I get this:
```
alex@kubuntu:~/Bad Apple screensaver$ wine *.scr
err:menubuilder:init_xdg error looking up the desktop directory
wine: Install Mono 2.8 or greater for Windows to run .NET 4.0 applications.
```

This actually happens with any program that is a .NET 4.0 application.  I tried installing Mono 2.8 using Winetricks but when I select it to install I get an error message saying "dotnet40 does not yet fully work or install on wine. Caveat emptor".  It then opened ~/.cache/winetricks/dotnet40 in Dolphin and opened [http://www.mediafire.com/?v8rw5h1ra7maod4](http://www.mediafire.com/?v8rw5h1ra7maod4) in Chromium, and told me "Please download gacutil-net40.tar.bz2 from [http://www.mediafire.com/?v8rw5h1ra7maod4](http://www.mediafire.com/?v8rw5h1ra7maod4), place it in /home/alex/.cache/winetricks/dotnet40, then re-run this script".  After I finished all the instructions and the .NET 4.0 installer ran, it said I already had that or a newer version installed!  So why do no .NET 4.0 applications run?  I'm pretty sure they ran on my previous install (Kubuntu 11.10, now I'm using 12.04)...  Can anyone help with this?  There are so many programs that aren't working for me because of this error.

---

### Post by Stonecold1995 on 2012-07-19
It turns out that my Wine thinks it can't run ANY .NET applications (.NET 2.0 fail as well).  The package "mono-common" is installed, and I can't remove it to try to install the official one [here]("https://www.microsoft.com/en-us/download/details.aspx?id=17851").

Any suggestions?

---

### Post by directhex on 2012-07-20
> **Stonecold1995 said:**
> It turns out that my Wine thinks it can't run ANY .NET applications (.NET 2.0 fail as well).  The package "mono-common" is installed, and I can't remove it to try to install the official one [here]("https://www.microsoft.com/en-us/download/details.aspx?id=17851").

Any suggestions?

You're confusing Mono for Windows and Mono for Linux.

For Wine, you care about Mono for Windows.

At any rate, try updating to Wine 1.5 - it has MUCH better support for running .NET apps, and will show you a popup offering to download, install & integrate Mono for Windows on first run.

---

### Post by Stonecold1995 on 2012-07-20
> **directhex said:**
> You're confusing Mono for Windows and Mono for Linux.

For Wine, you care about Mono for Windows.

At any rate, try updating to Wine 1.5 - it has MUCH better support for running .NET apps, and will show you a popup offering to download, install & integrate Mono for Windows on first run.

This is what I got:
[IMG]http://www.pictureshack.us/images/42713_net.png[/IMG]

And yet when I try "wine some_.net_program.exe" I still get an error saying I have to install Mono 2.8 to run .NET 40 (or 20) applications.

---

