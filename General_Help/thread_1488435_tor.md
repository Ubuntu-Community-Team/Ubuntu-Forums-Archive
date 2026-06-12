---
title: "tor"
date: 2010-05-20
forum: General Help
---

### Post by resonance77 on 2010-05-20
Background -
I installed Suse last night and liked it a lot. It would not let me boot to windows7 on a different partition. After messing with it all day and totally losing that partition, I decided to re format the hard drive and re install 7. I then installed the latest version of ubuntu to give that a whirl, instead of suse. I had no problem getting it to dual boot. I use this computer for work. I need it to work with magic jack and microsoft streets and trips, which I have found no way of making work in linux, hence the need for windows 7. I also need to edit pdfs, which was default in Suse by the way, so if anyone knows how to hook that up, it would be greatly appreciated. I also need to use Tor on occasion. I can not figure that one out. That is the main reason for this post. I need it and i can not get it to work. I really don't like the su sudo thing with the terminal. I spent the whole day trying to figure out suse and this is just making things much more difficult. I am only a couple of hours into ubuntu but I am running into more road blocks than I did all day with suse. How do I get Tor to work? I need details. I am like a mentally handicapped person trying to learn Chinese with this.

---

### Post by ryan858 on 2010-05-20
Well first off, you can use Wine to run your windows apps. It's kind of hit and miss about what apps it will work with... some will work perfectly and others won't work at all. But that kind of comes with the territory of trying to run windows programs in linux. The best solution would be to find an alternative version of the program you need, which is very easy to do with Ubuntu in particular. There are literally thousands of programs for linux OS's (and usually windows too) that are open source and free. Ubuntu makes it incredibly easy to get ahold of a very large amount of them. You just go to Applications on the top taskbar, and at the bottom of the Applications menu, click Ubuntu Software Center. You'll find thousands of apps that have been approved (and sometimes even improved) by the Ubuntu software team (I can't think of the actual name off the top of my head). You can also use the command **sudo apt-get install *<program>*** to install something from the terminal. You can find the terminal in *Applications > Accessories.*

You should read over the Ubuntu guides available in Ubuntu itself and on the website. They will help get you going fairly quickly.

Now, obviously there are programs that are windows only, such as  magicjack  most likely, but that's what wine is for. 

As for tor, you should read the guides on the tor website for help getting it working in linux. It's actually fairly easy to do once you know what to do.

Follow this guide, it should walk you though it all the way. [http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

To sum it up, basically you just add the source to /etc/apt/sources.lst (this is so you can download and update tor with one simple command **"sudo apt-get upgrade tor"**) and download & install it, then some simple configuration to get it setup to your liking.

Btw, you can use **sudo apt-get upgrade** to upgrade ALL software installed on your Ubuntu at once (excluding of course anything that isn't in the repositories).

Also, about the sudo thing... Read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically, sudo is a security measure, it's a big part of what makes Linux so safe and secure. If you need Tor, then you're obviously looking for security, so really, it's a very minor inconvenience to put up with the constant password prompts and having to type sudo all the time, for the greater purpose of being as secure as possible.

The move to Linux has a steep learning curve, it's almost comparable to the first time you ever got on a computer, because it's so different than what you're probably used to (I'd assume Windows), but once you get past that it's a breeze. (It won't take very long) And IMO, even easier to use than Windows.

Don't get me wrong though, I'm not trying to tell you that linux (or ubuntu) is better than windows or anything, that's up to you to decide. It's a personal preference kinda thing... I kinda feel like I'm stepping over some kind of boundary here, so I apologize in advance if I have... But anyway, just give it a good shot. I think you'll like it a lot.

---

### Post by resonance77 on 2010-05-21
No tor as of yet. I've tried this and about 8 other things. The closest I have gotten is using wine I get it to sort of start, but not connect. I don't know how to configure the firefox settings to make it work. I've found programs to do everything else I need to do. I'm sure I downloaded tor somewhere. I am utterly lost on this one.

---

### Post by resonance77 on 2010-05-21
I have been following these directions [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en) and I have finally got tor installed and running. Then got polipo  and uninstalled privoxy and used the polipo configuration for tor in the link on that page. Then I restarted polipo. I installed the firefox torbutton add-on and enabled it. 

Now If I toggle tor to enabled, it doesn't work.[COLOR=Black] I get an error page that says,
"The proxy server is refusing connections"

I checked Firefox connection settings and it is set for use system proxy settings.

I went to torbutton preferences, proxy settings. It's set for "Use the recommended proxy settings for my version of Firefox". Under that, the "use polipo box" is checked. I clicked on Test Settings. The results were this message:
"Tor proxy test: Local HTTP Proxy is unreachable. Is Polipo running properly?"

[/COLOR][COLOR=Black]Why is Local HTTP Proxy unreachable?[/COLOR]
[COLOR=Black]How do I figure out if Polipo is running properly?

[/COLOR][COLOR=Black]](*,) [/COLOR]
[COLOR=Black]
[/COLOR]

---

### Post by resonance77 on 2010-05-21
Duh, All I had to do was restart my computer and it is now working fine. 

I don't know how to switch the title of the thread to solved. If a mod could help me out with that, that would be great.

---

