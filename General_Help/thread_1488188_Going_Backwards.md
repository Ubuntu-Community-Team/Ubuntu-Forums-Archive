---
title: "Going Backwards"
date: 2010-05-19
forum: General Help
---

### Post by Hastor on 2010-05-19
I recently attempted to fanagle a means to get java on my Ubuntu OS through an outdated means. Through my attempts I seem to have bust up my OS to the point that plugins are unable to run. Though I know there is probably some cure to this, I would really just like to purge my system and reinstall Ubuntu. How would I go about doing this. Thank you.

---

### Post by Darkness Des on 2010-05-19
Boot up from the LiveCD once more and then tell it to format the partitions where Ubuntu is installed. Unless you did a Wubi install, in that case just uninstall Ubuntu from Windows.

---

### Post by QIII on 2010-05-19
Before you reinstall, what version of Ubuntu are you running?

What methods have you tried to install Java?

---

### Post by Lord.Quackstar on 2010-05-19
Backup files, boot up live cd, format or create linux partition, install, move back, install apps, done.

---

### Post by Hastor on 2010-05-19
To start off, I have the most recent version of Ubuntu which I would assume is 10.04 aka Karmic Koala.
Well, this is what went down. I was attempting to get Java on Ubuntu and, not knowing about the auto plugin thing, I googled it and followed the directions on this site [http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html)
Everything seemed to go fine until I got to a point where my terminal turned blue and what looked like a huge license agreement appeared on it. I attempted to interact with the terminal, but outside of moving up and down the document I could do nothing. I exited out of the terminal and was unable to find any automatic affects. I also attempted to run the last command and it was unidentifiable in the terminal. Thinking it might be a "behind the scenes" operation, I went to last.fm, the site I thought I needed Java to use, and attempted to use the auto-lugin source that popped up at the top of my screen to install Adobe. The operation was unable to work because it said something along the lines that I had apt-get running. To remedy this I tried to restart my computer and, when attempting the plugin a second time, I got the message that there was an interruption and that I needed to run sudo dpkg --configure-a to fix the problem, but when I attempted it the terminal said it couldn't execute. I'm certain I could fix it, but I worry that in attempting to follow the directions of the site I might have made changes I neither wanted not understood. That is why I just want to purge and begin anew. Thanks.

---

### Post by QIII on 2010-05-19
Well...

The first thing that comes to mind is that you were trying to install from a Dapper repo, and Dapper is no longer supported.

Also, you were trying to install Java 5 instead of Java 6.

Can you go to Synaptic and search for Java and scroll down to see if you can find any Java 5 entries and uninstall them.

Second -- Sun Java 6, Update 20 is the most recent version, and it is in the Lucid partner repository.  You can activate the repo (we'll talk about that later if you can get what you have uninstalled) and install Java from there.

Don't go off first thing and reinstall when you run into problems.

---

### Post by 98cwitr on 2010-05-19
this is how you install java CORRECTLY

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

btw 10.04 is Lucid Lynx...not Karmic Koala

---

### Post by Hastor on 2010-05-19
Thanks for the info cwitr.

Qlll, would there happen to be any site which could keep me up to date on Ubuntu's stats outside of this forum? I mean, I've found this forum to be a wonderful place, but it seems a bit cumbersome and wasteful to come crawling back to here whenever I hit the wall, and I really could use a bit of a brush up on the ins and outs of this operating system. Thanks.

---

### Post by 3rdalbum on 2010-05-19
You don't need to reinstall.

When you got the license agreement in the terminal, pressing Tab would have highlighted the I Agree button. It's not immediately obvious that you have to do this, though, so I tell people to install Java through Synaptic (which gives you the GUI version of the license agreement).

So you've interrupted the package manager. The command you need to type is:

```
sudo dpkg --configure -a
```

There's a space between the E in 'configure', and the hyphen before the A. If in doubt, copy and paste that into the terminal.

Then you can use the Tab key as I've described, etc.

Once installed you should remove the Dapper (Ubuntu 6.06) repository from your system. It's not likely to cause too many problems because all its packages will be overridden by the latest versions in the regular repositories, but still. When you went to install Java, it would have installed the latest version anyway, not the one in the old Dapper repository.

Don't follow old HOWTOs on Linux. You can get stuff seriously messed up that way. You're lucky, it looks like no actual harm was done.

---

### Post by QIII on 2010-05-20
> **Hastor said:**
> Thanks for the info cwitr.

Qlll, would there happen to be any site which could keep me up to date on Ubuntu's stats outside of this forum? I mean, I've found this forum to be a wonderful place, but it seems a bit cumbersome and wasteful to come crawling back to here whenever I hit the wall, and I really could use a bit of a brush up on the ins and outs of this operating system. Thanks.

Not sure exactly what you mean by that, Hastor.  This is the coffee shop where we all hang out to shoot the breeze and hide from our wives and kids.  (Dang.  I messed up something fierce on that one!  Our kids grew up and left and we started taking in fosters.  What were we thinking?)

I'm not aware if there is an RSS feed or something exactly what you are looking for, but you might see if there is something at [www.ubuntu.com](www.ubuntu.com).

I wouldn't think of it as "crawling back here".  Come hang out with us and read some posts that have nothing at all to do with a problem you are having.  You will learn an awful lot just by lurking.

And don't feel like your questions are stupid.  The only stupid question is the one not asked.  Most of us don't bite newcomers -- and you can just ignore the odd jerk or two who does.

---

### Post by Hastor on 2010-05-20
Thanks, man.
I'll do my job to fight the good fight. See you on the forums. :P

---

