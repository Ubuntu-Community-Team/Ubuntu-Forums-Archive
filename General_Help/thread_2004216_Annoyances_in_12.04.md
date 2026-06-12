---
title: "Annoyances in 12.04"
date: 2012-06-15
forum: General Help
---

### Post by yuanzhoulu on 2012-06-15
Hi all,

I did a reinstall recently and went to 12.04. Needless to say, frustrating, as Ubuntu always seems to want to take AWAY features at every release. Features that were not only important but ESSENTIAL to some people. :confused:

Rather than rant, it seems like life is just this way, and everyone just wants to copy Apple's horrible interfaces, too bad for the people like me who need to get real work done. Could anyone please help me with the following?

1. How do I get glunarclock? It is a date/time applet that has a Chinese calendar in it, and used to be included with all Ubuntu before. I used it HEAVILY.

2. I've switched to xfce. How do I get xfce4-xfapplet-plugin? It seems nonexistent in the repository. This is required for #1.

3. I NEED compiz for productivity features. I have a 17-button mouse and I had them configured to do everything such as switch VWMs, invert colours on windows, etc. I managed to get it installed, but it uses gtk-window-decorator. HOWEVER, I can't find gnome-appearance-properties @&*@&$@@. How can I configure the theme? And by configure the theme I mean SEPARATELY configure (1) the window borders (2) the widgets and (3) the colours. This used to be provided by gnome-appearance-properties. I tried gnome-tweak-tool but it does not allow for individual fine-tuning of colours, widgets, etc.

Thanks!

---

### Post by mansonfan78 on 2012-06-15
I also switched to xfce.  I believe xfapplet is no longer available because when they switched to Unity they removed most, if not all, of the gnome panel applets, which would make xfapplet pointless.
As far as your compiz issue, you could try installing Emerald and see if that lets you do anything.
Basically, anything gnome-based has been nerfed by Unity to some degree.

---

### Post by Paqman on 2012-06-15
In your case the features have been taken away not by Ubuntu, but by Gnome.

Gnome recently moved to a new version (Gnome 3). The tools and applets you're referring to are Gnome 2, and therefore no longer supported.

If you want to keep using them you'll have to use a Gnome 2 based release. Ubuntu 10.04 or 11.10 will be supporting Gnome 2 until April next year, and CentOS should be supporting it for several years after that.

---

### Post by Paqman on 2012-06-15
> **mansonfan78 said:**
> 
Basically, anything gnome-based has been nerfed by Unity to some degree.

Not so, see my comment above. It's been nerfed by Gnome. Unity is a Gnome-based interface, it relies on the underlying Gnome architecture. If Gnome takes stuff away, it's gone in Unity too.

---

### Post by ptn107 on 2012-06-15
glunarclock is only available in Ubuntu 10.04 LTS or Ubuntu 11.04.  It was considered abandoned as noone is maintaining the project or package.

---

### Post by LewisTM on 2012-06-15
To configure window decoration themes in Compiz, the easiest for you would be to install Ubuntu Tweak:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
Then run it and go to Tweaks/Theme
Pick or install you favorite Window Theme. You can also pick your GTK 3.0 theme. NOT your icon theme, that is controlled by Xfce.
Good luck installing emerald, I haven't succeeded. This fine program appears to have been left for dead.

Cheers!

---

### Post by yuanzhoulu on 2012-06-15
> **Paqman said:**
> In your case the features have been taken away not by Ubuntu, but by Gnome.

Sigh ... so the people at Gnome decided that all the THOUSANDS of hours of work by programmers in creating applets for Gnome 2 needed to be just trashed in a whim? Is not backward-compatibility a first priority for people these days? Could they not have written something to support Gnome 2 applets in Gnome 3?

As much as I like Linux, and have been a long-time user of Linux for 15+ years, I suppose this is exactly why people don't switch to Linux as a desktop environment :-/ What you rely upon, just disappears at any moment...

I'm also frankly more than annoyed that the interface has to keep undergoing drastic changes every release. I know part of it is Gnome's fault, but Ubuntu also has its fair share of blame for killing things from the repository and changing software without providing any kind of transition whatsoever. I remember the time when the window buttons suddenly switched to the left, reducing my working speed, so I had to google and use gconf-editor to put them back to the right, rather than a clearly labeled, fully-featured, dedicated window-frame editor to deal with button locations, like KDE has. SCIM also got switched to iBus without any kind of phrasebook converter whatsoever. QQ support was dropped from Pidgin too without notice. Every install, I have to spend hours trying to make this system even _barely_ usable.

Also, what's all this hype about Unity and Gnome 3? Is the notion of a traditional computing interface not going to be supported for long? I thankfully still have xfce available to me as a LIFELINE, but is xfce going to go and become Unity-like, too? It sure sounds like it from their 4.10 description, and I fear touching it. I mean, seriously, I love my 17-button mouse, FAST menus, and things designed so I can do real work at extreme efficiency. The difference between being able to switch to an application in 0.1 second and 1 second makes a BIG difference to me, since I have a macro keyboard that I record operations and play back to get tasks done at high speed in GUI apps. I also need my different applications to start using different locales, different environment variables, etc. These are exactly the reasons I use Linux. And it seems to me none of these things are available in Unity.

---

### Post by yuanzhoulu on 2012-06-15
> **LewisTM said:**
> To configure window decoration themes in Compiz, the easiest for you would be to install Ubuntu Tweak:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
Then run it and go to Tweaks/Theme
Pick or install you favorite Window Theme. You can also pick your GTK 3.0 theme. NOT your icon theme, that is controlled by Xfce.
Good luck installing emerald, I haven't succeeded. This fine program appears to have been left for dead.

Cheers!

Thanks!! I can change the window border now. But how to edit the colours of the widgets? There used to be this setting.

---

### Post by Zill on 2012-06-15
> **yuanzhoulu said:**
> ...Could they not have written something to support Gnome 2 applets in Gnome 3?...
"They" have!  Take a look at [MATE]("http://mate-desktop.org/about/") which is a fork of Gnome 2.

If you want a traditional (Gnome 2) OS you might prefer [Linux Mint]("http://www.linuxmint.com/download.php") with default MATE DE, rather than adding MATE to Ubuntu.

---

### Post by Paqman on 2012-06-16
> **yuanzhoulu said:**
> Sigh ... so the people at Gnome decided that all the THOUSANDS of hours of work by programmers in creating applets for Gnome 2 needed to be just trashed in a whim? Is not backward-compatibility a first priority for people these days? Could they not have written something to support Gnome 2 applets in Gnome 3?


Afraid so. The software world moves pretty quickly, and Gnome2 was judged to be getting a bit too long in the tooth, taken out to the back paddock and shot. Many users such as yourself have reacted with dismay, and there has been some effort put into various forks of the Gnome 2 branch, such as the Mate project mentioned above.

In the long-term these forks will probably run out of energy, but in the meantime they're an option. Most Gnome distros are also still supporting Gnome 2 for a little while, and as I mention above some are going to support it for many years yet. So if you love your Gnome 2, nobody is going to make you give it up for quite a while. So while you may not get backwards compatibility, you will still be able to run the old software on a supported system.

> 
I'm also frankly more than annoyed that the interface has to keep undergoing drastic changes every release.

Interfaces have been quite stable for a long time. But right now we're going through a phase of disruption and change as new form factors (eg: tablet, phone, TV) and interfaces methods (eg: touch, gesture, voice) come into play. Those who don't try to adapt to the new environment will be left behind.

The other obvious option to avoid change in every release is: don't upgrade to every release. You sound like someone who values stability, for you staying on the LTS upgrade path would be ideal. You'd have a stable system that would only change every two years at the most, and you can now use the desktop LTS for five years if you want.

---

