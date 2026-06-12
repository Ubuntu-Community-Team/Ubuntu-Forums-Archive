---
title: "Zeitgeist Datahub Purpose in Ubuntu"
date: 2011-06-02
forum: General Help
---

### Post by Shinypaper on 2011-06-02
From what I can tell Zeitgeist is some sort of data logger, and also something relating to Gnome. What purpose does it serve in Ubuntu and would removing it cause any problems?

Cheers,

- Shiny

---

### Post by hawthornso23 on 2011-06-02
I'm interested in the answer to this too. 

As I understand it, it keeps a database of which files you open and which applications you run. Unity makes extensive use of it to populate its dash and so forth. The idea is that unity will preferentially present you with the stuff you use most frequently. The new Gnome Shell also uses it for much the same purpose. So this isn't just a Unity issue. There is supposed to eventually  be a privacy tool that permits you to turn it off and on and control what kinds of data it records, but I don't think they have this part working yet.

I suspect removing it would probably break unity. But it might not be such a problem if you are running the classic desktop.

---

### Post by stinkeye on 2011-06-02
There is an Activity Log Manager available from the Zeitgeist PPA.
You must first upgrade Zeitgeist from this PPA before installing Activity Log Manager.
[**[COLOR="DarkRed"]_Install Activity Log Manager for Zeitgeist_[/COLOR]**]("http://www.omgubuntu.co.uk/2011/05/activity-log-manager-for-zeitgeist-lets-you-blacklist-files-and-apps-delete-your-history-more/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29")

---

### Post by Shinypaper on 2011-06-05
Thanks for all your replies. Sorry for the slow response, have been away for a few days. 

hawthornso23: I figured just about the same actually. I had it disabled on my test machine for a while and it doesn't seem to cause any issues. Also, I use the Ubuntu classic desktop environment, Gnome. I've always disliked unity.

---

### Post by dajhorn on 2011-06-07
You can safely remove the zeitgeist-core package if you are using the Classic Desktop.  Afterwards, delete the "$HOME/.local/share/zeitgeist/" folder.

Zeitgeist is in the default Ubuntu Natty install because the unity package recommends the unity-place-application package, which depends on the zeitgeist-extension-fts package.

Zeitgeist seems like a non-feature in Natty.  I think that most people would uninstall it if they understood that it records desktop activity.

---

### Post by Nemo_bis on 2011-06-23
Also, it was using about 74 % CPU on one core of my AMD E350 right now, for some reason... I'm removing it now.

---

### Post by movieman on 2011-08-24
I wondered what was causing my machine to trash the disk for nearly five minutes when I log in. I uninstalled this junk that I don't want and suddenly as if by magic my logins are as fast as they were a couple of versions back.

Ugh, I see that it's using sqlite, so I'm not surprised that it runs like crap if it's doing lots of database updates whenever I log in; sqlite has its place but database writes are exceedingly slow compared to a real database.

---

### Post by cybrsaylr on 2011-09-04
> **stinkeye said:**
> There is an Activity Log Manager available from the Zeitgeist PPA.
You must first upgrade Zeitgeist from this PPA before installing Activity Log Manager.

WOW!

Was hoping for a simpler way to do this, right inside of Natty already!

---

### Post by 02darkRS on 2011-10-13
Does this just disable the logging feature or will it ruin Unity all together? I use classic but other users on the PC use Unity. Also, I am on an SSD so where does it store it's info & do it's "disk trashing"? Is it in the /home folders or / ?

---

### Post by Keith Fox on 2011-11-14
I'm not sure what it does either. But I disabled it in Startup Applications and things seem to be great.

---

### Post by philinux on 2011-11-14
> **Keith Fox said:**
> I'm not sure what it does either. But I disabled it in Startup Applications and things seem to be great.

[http://zeitgeist-project.com/about/](http://zeitgeist-project.com/about/)

And to tweak it's use.
[http://www.webupd8.org/2011/05/keep-files-from-showing-up-in-unity.html](http://www.webupd8.org/2011/05/keep-files-from-showing-up-in-unity.html)

There is also the Activity Journal.

The package names from the ppa are activity-log-manager and gnome-activity-journal

---

