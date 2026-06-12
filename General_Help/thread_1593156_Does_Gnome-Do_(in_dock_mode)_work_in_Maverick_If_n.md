---
title: "Does Gnome-Do (in dock mode) work in Maverick? If not, is there a workaround?"
date: 2010-10-11
forum: General Help
---

### Post by martini1179 on 2010-10-11
I'd like to know

1) If Gnome-Do (in dock mode, not Docky) works in Maverick.

2) If not, is there a workaround? I don't want to use Docky/Kupfer when I have the excellent Gnome-Do. 

3) If it DOES work in Maverick, how well does it work? Any compatibility/performance issues?

---

### Post by lumbricus on 2010-10-11
When I upgraded from 10.04 the docky mode was disabled in gnome do and the entry for the docky theme was missing in the preferences. I'm still searching for a solution. I'd prefer too to have gnome-do inside docky and not seperatly.

---

### Post by lumbricus on 2010-10-11
Finally I found some more hints. It seems as if the dock theme was totally removed from do:
[http://www.lamalex.net/2010/03/docky-has-been-removed-from-do/](http://www.lamalex.net/2010/03/docky-has-been-removed-from-do/)
[http://askubuntu.com/questions/5865/does-gnome-do-with-the-docky-theme-work-well-with-10-10-maverick](http://askubuntu.com/questions/5865/does-gnome-do-with-the-docky-theme-work-well-with-10-10-maverick)
[http://askubuntu.com/questions/5790/gnome-do-in-doesnt-have-the-docky-appearance-anymore](http://askubuntu.com/questions/5790/gnome-do-in-doesnt-have-the-docky-appearance-anymore)

---

### Post by dregin on 2010-10-12
This is extremely annoying. What service does removing the theme completely provide???

---

### Post by ean5533 on 2010-10-12
See the discussion in [this thread]("http://ubuntuforums.org/showthread.php?t=1593137"). The authors of GNOME-Do decided to split the launcher and the dock into two separate projects. Neither of the projects is quite as whole as they used to be, but they're still working on it.

In the mean time, one of the last couple posts shows where to get an old version of GNOME-Do that still has the dock merged in.

---

### Post by lumbricus on 2010-10-12
Integration of Do in Docky is planned for Docky 2.2:
[https://bugs.launchpad.net/docky/+bug/446049](https://bugs.launchpad.net/docky/+bug/446049)

---

### Post by lava on 2010-10-16
The fact that gnome-do and docky would get released in such a state on Maverick is absolutely stupid. It broke functionality for a lot of people. 

I used gnome-do with the docky skin. Now gnome-do is broken and I can't get the property panel to show up, and docky isn't a launcher.

I'm not planning on using docky anymore, and gnome-do is completely broken for me. It showed up fine (with it's regular skin) right after the maverick update. Because I wanted the docky theme back, I tried to open preferences, gnome-do crashed, complaining that there was a problem with the docky theme, and now I can't even get it to show up in the old skin.

Smart move...

---

### Post by ean5533 on 2010-10-16
If you want the Docky+GNOME-Do functionality, I would use an old version of GNOME-Do as suggested earlier in the thread. Problem solved.

As far as the crashing, you should file a bug report. I'm sure the authors of GNOME-Do will fix it.

Finally, remember that GNOME-Do wasn't made by the same people who made Ubuntu (Canonical). Canonical simply packaged it up with Ubuntu. If you're disappointed in GNOME-Do not having a Docky skin anymore, you should [let them know]("https://mail.google.com/mail/?extsrc=mailto&url=mailto%3Adjsiegel+dohomepage@gmail.com"). Maybe they'll put it back in. The Ubuntu people aren't going to be able to help.

---

### Post by sandman6471 on 2010-10-16
[B]I have tried the docks. They seem to change as far as order of icons the look of the dock all by themselves. So I took the top panel bar and removed everything from it and added "windows list" to it thru add to panel. 

[/B]I took the bottom panel and added a custom gnome menu, added all the programs I wanted quick access to, the notification area's and the clock and weather from the top panel bar. I then selected properties set the size of the bar, uncheked the expand box. If you like you can select autohide, you can even change the icons appearance. I downloaded mine from rocketdock then when i placed my theme into effect everything matches. I like it and it's not using to many resources and it's easy to configure and maintain. Everyone has there own thing, so what ever is right you.

Linux is Great.....
Take Care Everyone....

---

### Post by metchebe on 2010-10-16
> **martini1179 said:**
> 
3) If it DOES work in Maverick, how well does it work? Any compatibility/performance issues?
For some reason Gnome-Do is now unable to run commands with parameters in Maverick. This is a regression, it used to work fine in Lucid.

In particular, this does not let you "gksudo" anything. Running Do with the debugger shows:
```
[Info  22:59:46.912] [EnvironmentService] Executing "gksudo gedit"
Error showing url: Error stating file '/home/metchebe/gksudo gedit': No such file or directory

```

Tested in Maverick 32 and 64 bit.

Regards,
Marco

---

### Post by ean5533 on 2010-10-17
> **metchebe said:**
> For some reason Gnome-Do is now unable to run commands with parameters in Maverick. This is a regression, it used to work fine in Lucid.

In particular, this does not let you "gksudo" anything. Running Do with the debugger shows:
```
[Info  22:59:46.912] [EnvironmentService] Executing "gksudo gedit"
Error showing url: Error stating file '/home/metchebe/gksudo gedit': No such file or directory

```

Tested in Maverick 32 and 64 bit.

Regards,
Marco

You should [report]("https://bugs.launchpad.net/do") that bug.

---

### Post by Berrex on 2011-02-14
> **lumbricus said:**
> Integration of Do in Docky is planned for Docky 2.2:
[https://bugs.launchpad.net/docky/+bug/446049](https://bugs.launchpad.net/docky/+bug/446049)
So let me get this straight. They had a fantastic idea going, decided to butcher it, and then decided to re-implement their fantastic idea in a (far) future release? What?

They should have kept everything as Gnome-Do, and Docky as an interface. Yeesh, I haven't seen such poor development ecisions made in a very long time. I mean, we're only at 2.0.12 right now, and it's already mid-February of 2011. How long will it take to reach 2.2?

At this point, I have extremely low hopes for the entire Docky/Gnome-Do project and anything their developers can put out, quite frankly. I'm sure Cairo/AWN + Kupfer/Synapse will do just fine. :-|

---

### Post by stinkeye on 2011-02-14
They're too busy pushing other mono apps into ubuntu.

---

### Post by directhex on 2011-02-14
> **stinkeye said:**
> They're too busy pushing other mono apps into ubuntu.

Define "they".

---

### Post by directhex on 2011-02-14
> **Berrex said:**
> I mean, we're only at 2.0.12 right now, and it's already mid-February of 2011. How long will it take to reach 2.2?

2.1 is pending upload to Debian. Assuming Docky follows GNOME numbering conventions, that'll be the first development release in the 2.2 branch.

---

### Post by stinkeye on 2011-02-14
> **directhex said:**
> Define "they".
The little green men inside my head. :shock:

---

