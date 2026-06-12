---
title: "Ubuntu 11.04 with GNOME 3 won't login the user"
date: 2011-05-02
forum: General Help
---

### Post by SoG-Hawking on 2011-05-02
Hello everybody, I need several answers, because I'm in a very unpleasant situation.

I was eager to try GNOME 3 in Ubuntu 11.04 (because I wasn't very satisfied with Unity, like almost everybody around) so I installed it using this guide:

[http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml]("http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml")


After rebooting the system (to finish the installation), I've got an error message while trying to login:
> Could not update ICEauthority file /home/<username>/.ICEauthority

I've googled for some time and found different 'solutions', however none of them seems to be working.

What can be done with a system like this? I'm not able to login, how can I downgrade the system?

I am afraid, that my internet connection isn't working as well, just in the shell (using CTRL+SHIFT+F1). 

Thanks in advance

---

### Post by zvacet on 2011-05-02
In terminal 

```
sudo chown test:test /home/test/.ICEauthority 
sudo chmod 600 /home/test/.ICEauthority
```

**replace test with your username**

---

### Post by daanjordaan on 2011-05-02
Same problem here,

I'm on a Asus eee PC 1215N

Maybe it has something to do with the Nvidia Ion GPU?
Ubuntu and Nvidia Ion don't work with one another:(

When the Nvidia drivers are installed (but not activated) Gnome 2 boots.
When I disable the Nvidia drivers, it uses the Intel chip instead. So Unity boots without any problems.
But when I install Gnome 3 after that I get the same error message.
I will try to install Gnome 3 without disabling the drivers in a moment.
I'll check back in about an hour.

---

### Post by SoG-Hawking on 2011-05-02
> **zvacet said:**
> In terminal 

```
sudo chown test:test /home/test/.ICEauthority 
sudo chmod 600 /home/test/.ICEauthority
```

**replace test with your username**


Sorry, but this is not working at all.

There's probably no solution.

---

### Post by daanjordaan on 2011-05-02
> **SoG-Hawking said:**
> Sorry, but this is not working at all.

There's probably no solution.

Same here.

Just did a fresh install didn't touch anything. Installed Gnome 3 and had the same issue again.:(

---

### Post by gaz514 on 2011-05-02
I had the same problem. I went back to Unity and haven't tried again since. However, that guide seems to be missing a step when compared to the other guides: ```
apt-get install gnome-shell
```. Perhaps if you do that it'll fix the problem, just a guess though.

---

### Post by SoG-Hawking on 2011-05-04
I saw that one while trying to find the solution. It's probable that it would help, but unfortunately, it seems that I have no real internet connection without logging in. Can it be fixed somehow?

---

### Post by gaz514 on 2011-05-05
> **SoG-Hawking said:**
> I saw that one while trying to find the solution. It's probable that it would help, but unfortunately, it seems that I have no real internet connection without logging in. Can it be fixed somehow?

You can go to a virtual terminal (Ctrl+Alt+F1 etc.) and connect to the network from the command line. This is easy on a wired network, harder on a wireless network, and a big pain on a WPA-secured wireless network. Personally I just did a reinstall as it seemed like less hassle, especially as I had already completely broken Unity by trying to change things in the Compiz Config manager; gotta love Ubuntu's policy of shipping software that's not quite ready and stable yet. For now I'm just using Unity and trying to decide whether I actually like it; haven't yet had the time to mess about with Gnome 3 again.

You might also be able to fix it by using chroot from a livecd, but I couldn't figure out how to make my network connection accessible from within the chroot.

---

### Post by SoG-Hawking on 2011-05-06
> **gaz514 said:**
> You can go to a virtual terminal (Ctrl+Alt+F1 etc.) and connect to the network from the command line. This is easy on a wired network, harder on a wireless network, and a big pain on a WPA-secured wireless network. Personally I just did a reinstall as it seemed like less hassle, especially as I had already completely broken Unity by trying to change things in the Compiz Config manager; gotta love Ubuntu's policy of shipping software that's not quite ready and stable yet. For now I'm just using Unity and trying to decide whether I actually like it; haven't yet had the time to mess about with Gnome 3 again.

You might also be able to fix it by using chroot from a livecd, but I couldn't figure out how to make my network connection accessible from within the chroot.

Thanks, you're probably right, I've come to the same solution. I am still not sure whether use Unity or not, it's not basically that bad.

We'll see later...

---

