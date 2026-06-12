---
title: "What to do after install - All opinions needed"
date: 2009-10-23
forum: General Help
---

### Post by CupofDice on 2009-10-23
I installed Kubuntu 9.04 64bit yesterday after 2 years of using windows. I need some tips on what to do after an install.

Now, I installed some codecs with amarok's urging, and I installed the restricted pagkages as suggested by [http://kubuntuguide.org/Jaunty](http://kubuntuguide.org/Jaunty)

1. I want to stay as far away from gnome as possible. I really want to dive into kde4 and it's apps.

2. KDE4 is still buggy, I see. So where is a list to some good commands for konsole, where I can relearn moving and copying, and not rely on the gui and it's crashing.

3. Is there an kde4 app for UbuntuOne?

4. Is there another KDE4 browser besides Konqueror?

5. I remember adding repositories for my old linux install. Should I do the same for Kubuntu or is there no need?

6. Is KOffice good enough? Does it support opening and saving .doc and opening .doc? Can I do headers on every page? That's all I really need and if KOffice ties into KDE4 better than OO.org, I would definitely like to use it.

7. Is there an app like RealplayerSP for Kubuntu? Or any hacks I can do to get something like that working? RealplayerSP downloads videos from various site. A similar app is Jaksta for windows.

8. I don't need a complicated video player, just one that works and plays everything. I don't want to use vlc btw, and dragonplayer seems fine. But what and how do I get the best backend for it? It doesn't play wmvs for example.\

9, In Software Updates, I have 4 blocked updates, all having to do with linux headers and linux image and linux generic and linux restricted. Should I install them? If so, how?

10. Fonts aren't smooth. I installed microsoft fonts with the restricted package. Should I use one of them system wide? Also, there use to be a Font hack, where you added a bit of code to a file in the Home directory. Does that work in kde 4? Basically, my question is how do I get smooth fonts in all my apps?

Not your normal problems, but if you know anything that can help, Great!-

1. Spotify doesn't have any sound. It doesn't give me an error either. There is some static noise when I use it.

2. Anyone here ever used syncplicity? Are there any unofficial apps for it? I don't need syncing, but simply to download my folders onto my comp. I can always go to my windows machine and do it, but that'll be a pain.

3. How to get yWriter working with Kubuntu 9.04? I compiled mono 2.4 as yWriter's site said to do, but it's still not working.

4. Is Basket note organizer still be updated? Anything else like it for KDE4, a note-taking app with automatic saving?

5. On Windows, I had google desktop, which I brought up by clicking ctrl twice. It searched my desktop and the net. I used it though, to run apps. KRunner is the equivalent here right? If so, how can I get it to run by doing ctrl twice?

6. I've had Nvidia driver or something crash a few times (having no noticeable effect). How do I make sure I have the most stable drivers for Nvidia?

7. That black box that appears in the lower right corner when downloading (I am now using KGet). What is it?

8. Do I need a firewall anymore than I did last time? If so, is Uncomplicated Firewall (ufw in apt) good enough?

Sorry if I went overboard with the questions! Just wanted to get it out of the way, and this forum looks way too different than a few years ago, so I'm feeling a bit lost. Google isn't helping by only having info a year or so out of date. Glad to be back in the linux world!

Thanks to all who reply and help! Also, any other advice is welcomed.

---

### Post by rob1408 on 2009-10-23
The first thing I'd do is update KDE 4.2.4 to KDE 4.3.2.  Things ran a lot smoother for me after doing that.

---

### Post by DeMus on 2009-10-23
2. Look here: [Linux Shell]("http://www.linuxcommand.org/learning_the_shell.php")

---

### Post by CupofDice on 2009-10-23
@rob1408, How do I do that? :D I am on 4.2.2 right now. I thought I was at the latest for Jaunty.

Thanks Demus!

---

### Post by rob1408 on 2009-10-23
[http://www.ubuntugeek.com/how-to-install-kde-4-3-1-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/how-to-install-kde-4-3-1-in-ubuntu-jaunty.html)

The article mentions KDE 4.3.1 but 4.3.2 is in the backports and it upgrades to that instead.  Personally I find it faster, smoother and I'm yet to encounter a bug.  I updated a month ago.

---

### Post by golanbatrac on 2009-10-23
> **CupofDice said:**
> 
9, In Software Updates, I have 4 blocked updates, all having to do with linux headers and linux image and linux generic and linux restricted. Should I install them? If so, how?


Dependencies have changed for the four packages.  To download, open a Terminal and type the following:

```

sudo apt-get dist-upgrade

```

> 
8. Do I need a firewall anymore than I did last time? If so, is Uncomplicated Firewall (ufw in apt) good enough?


ufw should already be installed on your system.  In the terminal:

```

ufw enable
ufw default-deny

```

Reboot.

---

### Post by CupofDice on 2009-10-23
Thanks rob and golan! Will get started on it right away. Good to see the forums are as helpful as ever. At least that hasn't changed. :D

---

