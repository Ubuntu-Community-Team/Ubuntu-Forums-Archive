---
title: "Completely Downgrade GNOME/Unity"
date: 2012-03-03
forum: General Help
---

### Post by Tramx on 2012-03-03
Hi, I've been using Ubuntu 10.10 a lot lately mainly due to the fact that I do not prefer the current desktop environment interface design especially for GNOME 3 which limits my productivity. However, I want to prepare for the upcoming 12.04 release. 

Testing 11.10, is there any way I can completely remove the Unity desktop (not using fallback) and downgrade to GNOME 2?
I wanted to try to install GNOME on top of 11.10 using the Maverick repository but I fear that this might break the system.
The only other option I know is to compile GNOME 2 from source but this seems difficult and I prefer to use pre-compiled packages. Is there any other way? Please let me know.

I miss the old GNOME 2 interface but if it is truly not possible I may have to switch to XFCE which in my opinion is the next best & closest option.  :cry:

---

### Post by kurt18947 on 2012-03-03
I'm not an expert but I'm pretty sure the answer is no, it's not possible.  There are several options though.  Gnome 3 with some extensions can come very close to the gnome 2 desktop.  I've attached a screenshot of my top panel.  There are a couple choices for a bottom panel if you want it.  Gnome-session-fallback has gotten some love lately. Xubuntu/Xfce4-desktop is indeed a nice alternative; at least it's still in development unlike gnome 2.  Lubuntu/LXDE desktop is another nice choice especially for less powerful machines.   Are you aware of Linux Mint with Gnome 3, Mate & Cinnamon desktops?  Cinnamon seems quite usable and can be installed on Ubuntu.  You could download a Live CD or Live DVD and play around with those alternatives.  I've settled on Gnome 3 with extensions,  Unity just doesn't really fit me but not everybody works or plays the same.  Lots of alternative.

[ATTACH]213655[/ATTACH]

---

### Post by HavarN on 2012-03-03
You should not try to use old packages from a previous distribution. However, you could use the forked Gnome 2 desktop environment Mate via this ppa:
[https://launchpad.net/~amanas/+archive/mate-desktop](https://launchpad.net/~amanas/+archive/mate-desktop)

Never tried it though, so I don't know how well it works, or if it is a complete Gnome 2 desktop environment.

---

### Post by Tramx on 2012-03-04
Thank you for your feedback. I am aware of the MATE desktop project. I believe that it is an excellent idea and I will try testing it. However, my main fear of MATE is the same fear I had when Oracle took over Sun. I fear that they would one day discontinue developing Open Office and other open source applications by Sun. Thankfully there is Libre Office now. For now, I want to give MATE time to mature and ensure that they do not discontinue development.

Forgive me for still carrying the Windows mind-set, but when I use fall-back, I feel like using Safe Mode for fixing issues relating to video drivers, and I don't want to use it as a main interface :-?. When I look for a good Desktop environment, I want to look for a sturdy, stable yet simple and productive interface where I can access all the features as a result of years of hard work and development (As I see in Linux). I care not for visual effects that pointlessly consumes system resources. It is a great shame to see GNOME 2 pass away as it full-fills my personal requirements. :(

---

### Post by edm1 on 2012-03-04
Using an old repository will most likely not work. It depends exactly what you're after but as of 12.04 the indicator applet has been ported to GTK3 meaning that if you install gnome-fallback-session (Classic Desktop) then you get a desktop very similar to the old GNOME 2 but based on GTK3. [http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html](http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html)

---

### Post by Tramx on 2012-03-04
What I originally was looking for was for ways to install GNOME 2 on top of newer Ubuntu releases. If you guys stress that I cannot use older repositories to do the job, I will not do it. Right now, I can't really find myself liking GNOME fallback. As much as it may look like GNOME 2 it is not GNOME 2 including the software and some functionality. Like all other things, I could test it when it gets released. I do not like where the GNOME project currently is heading. I feel the best option for me is to move to other supported desktop environments.

Disappointed... :(

---

### Post by bob-linux-user on 2012-03-04
Try Xubuntu-it can be configured to act and look like gnome 2. I am running Xubuntu on Ubuntu 12.04

---

### Post by 3rdalbum on 2012-03-04
Unity has been winning a lot more fans in 12.04. If you can comprehend in your heart that Unity is a vast change along different principles than ever used before, and learn its features, you may come to appreciate it.

---

### Post by kurt18947 on 2012-03-05
> **Tramx said:**
> What I originally was looking for was for ways to install GNOME 2 on top of newer Ubuntu releases. If you guys stress that I cannot use older repositories to do the job, I will not do it. Right now, I can't really find myself liking GNOME fallback. As much as it may look like GNOME 2 it is not GNOME 2 including the software and some functionality. Like all other things, I could test it when it gets released. I do not like where the GNOME project currently is heading. I feel the best option for me is to move to other supported desktop environments.

Disappointed... :(

Trying an alternative desktop does seem like your best bet.  Quite a few people in your position seem to like Mate or Cinnamon. I'm pretty sure Cinnamon can be installed on Ubuntu and I think Mate can be as well.  The advantage of installing alternative desktops on Ubuntu is that you're not bound by any one desktop.  When you log on, you can select from a list of installed desktops/ window managers.  The downside is that for example Xfce4-desktop is not a "pure" Xfce environment; gnome apps are still there.  I don't see this as a negative, others may.

I believe the removal of some more powerful configuration apps is intentional.  It is an effort on the part of Ubuntu and/or Gnome to make installation and use easier for inexperienced people that don't want to be faced with multiple choices they don't understand.  I've found ways to restore functionality I missed.  For instance, I was able to restore the old-style printer install/configure and the old-style users & groups.  I suspect the reasoning is that if a user is experienced enough to be able to find and install advanced configuration utilities, he/she is experienced enough to not bork-beyond-repair his/her box.

---

### Post by MARP1961 on 2012-03-05
You should install Ubuntu 11.10 (or wait for 12.04) and then add the Gnome Shell desktop alternative. Gnome Shell is modern, good looking and can be configured to act like Gnome 2 with a bottom panel showing workspaces. You can even have your favorite icons on the top panel. Have a look at Gnome Shell extensions which are just 2 clicks away:

[https://extensions.gnome.org/](https://extensions.gnome.org/)

I also did a short video showing some of this working on my HP laptop:

[http://www.youtube.com/watch?v=evgvL0X33rg&feature=g-upl&context=G2f6e881AUAAAAAAAAAA](http://www.youtube.com/watch?v=evgvL0X33rg&feature=g-upl&context=G2f6e881AUAAAAAAAAAA)

---

### Post by holycow131415 on 2012-03-05
Just use the XFCE environment.

---

### Post by Tramx on 2012-03-06
I've already tried the Xubuntu and Lubuntu distributions. They were both very nice and the usability, just great. I prefer Lubuntu out of the box because of it's outstanding simplicity and speed (due to being lightweight, but no software center :O). I will give GNOME Shell (With Extensions) and MATE a try next weekend when I have more time.

> The downside is that for example Xfce4-desktop is not a "pure" Xfce environment; gnome apps are still there. I don't see this as a negative, others may.

Quite right you are, kurt18947. I realized there where GNOME 2 like applications like gcalctool and gthumb in XFCE. While I also don't view this as an issue, it may become unsupported as GNOME 3 progresses. But there are more software to choose from/updates that can be added later.

There is also one more problem I'd like to point out. While this may not be in my place to say it, but I think it is really unfair how the Ubuntu family distributions are "ranked":

1.) Ubuntu/Kubuntu/Edubuntu (5 years LTS)
2.) Xubuntu (3 years LTS)
3.) Lubuntu (No LTS)

They should have equivalent support time-spans as this forces you to stick with the most mainstream distro. But again, this is up to the developers assigned to each distribution. I could just as well stick with Debian, and get all I want in terms of user interface and LTS but I feel they purged too much "non-free" software out of the kernel/software hindering usability.  Again,this doesn't help me to formulate a proper decision on what to use...

---

### Post by imwithid on 2012-04-11
Why not stick with Ubuntu 10.04? It's still supported until April 2013. This gives you another year of support to fall back on. I intend on holding off for as long as I can while testing various distributions to see what works best.

I have yet to try Lubuntu. Xubuntu seems to be the best choice from what I've been testing (although I don't like the icon panel at the bottom. It feels too 'Macky', although I suppose that it can be removed).

---

