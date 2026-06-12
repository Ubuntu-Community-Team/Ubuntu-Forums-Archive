---
title: "Java applets in Chrome/Firefox"
date: 2010-05-06
forum: General Help
---

### Post by YAN3 on 2010-05-06
Hi everyone.

I recently upgraded to Ubuntu 10.04 and I am a complete Ubuntu (Linux) noob. Can anyone please help me figure out why java apps don't seem to be working in any of my 2 browsers? I'm pretty sure I have openjdk-6-jre icedtea6-plugin installed and that I have a 64-bit version of Ubuntu.

I need to analyze this game [http://www.alientiles.com/](http://www.alientiles.com/) for one of my courses (believe it or not!), but I can't see the game itself! In Firefox, I just get a grey box where the game should be, and in Chrome, I see nothing at all. Please help :(

Thanks a lot.
Nick

---

### Post by QIII on 2010-05-06
It could be that your game does not play well with OpenJDK, and I believe Chrome does not play with OpenJDK at all.  I uninstalled it, but I don't think you need to go that far ... unless you want to.

See my post here:

[http://ubuntuforums.org/showthread.php?t=1474157](http://ubuntuforums.org/showthread.php?t=1474157)

---

### Post by YAN3 on 2010-05-06
Thanks a lot. But could you please tell me exactly what to do? Like I said, noob :)

Thanks
Nick

---

### Post by QIII on 2010-05-06
Open the terminal by going to Applications | Accessories | Terminal.

Type

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
``` and press enter.

You will be prompted for your password.  That is the same password you use to log in.  As you type it, you will not see any characters appear.  That is normal.  Press Enter.

You will watch a few lines of text scroll by, and you will eventually be left back at the prompt.  Type "exit".

Now go to System | Administration | Synaptic Package Manager

Search for "sun-java6" (no quotes)

Select sun-java6-fonts, sun-java6-bin, sun-java6-jre and  sun-java6-plugin.  If you are interested in programming in Java, also select sun-java6-jdk.

Click Apply.

When they are finished installing, go back to the terminal and type

```
sudo update-java-alternatives -s java-6-sun
```When you are returned to the prompt, type "exit" again.


PS:  Is that somewhat more complicated than installing it in Windows?  Perhaps.  But you have to remember that Linux distributions don't take it on themselves to decide exactly what you should/should not/want/do not want  to do or have active.  You are in control, not the OS.  In this case, you are taking control of your own destiny and bending your "user experience" to your will, instead of being fed what someone else has decided will be your "user experience."

Linux is not Windows, which is sometimes the hardest hurdle for new users to get over.  Once that is firmly set in your mind, what follows will make more sense and you will enjoy the adventure and freedom to make your "user experience" yours and yours alone.  Linux distributions are highly customizable.  But there is a danger to that.  Like I said:  Linux does not presume to know what you want.  If you tell it to make this change or that, it will do so.  Sometimes to your detriment.  

So, please:  Before launching into the dark alone, take a moment to come to the forums and ask questions first.  The only stupid question is the one asked too late.

Happy Ubuntuing!  We are here to help.  Don't let the "I hate Noobs!" jerks get you down.  Ignore them.

---

### Post by OldGoat58 on 2010-05-06
> **YAN3 said:**
> Thanks a lot. But could you please tell me exactly what to do? Like I said, noob :)

Thanks
Nick

Nick,

I was able to follow your link to the game and play it with my machine, but I'm running 32 bit Ubuntu 10.04 LTS, Lucid Lynx.  I don't know if it will help you but here is what I did so that the JAVA applets would work so that I could play games at POGO.com.

I first went to System, Administration, Synaptic Package Manager, and searched for iced.  I removed the icedtea6-plugin.  I closed Synaptic.  I then went to Applications, Ubuntu Software Center, and searched for sun.  I installed the Sun JAVA 6 Plugin.  I then searched for java and made sure the Open JDK JAVA 6 Runtime and Open JDK 6 Webstart were installed.  I rebooted, and it worked.

I'm sure if I'm wrong someone on the Ubuntu forums will find out and correct me.  I wish you well my friend.  I too am an Ubuntu newbie as I only started in November with Ubuntu 9.10 Karmic Koala.

Mike
Fairless Hills, PA

](*,)

---

### Post by YAN3 on 2010-05-06
Dear QIII and Mike,

thank you so much! It works :D I tried what QIII said first, and it works fine now, although in the last step I got: 
update-alternatives: error: no alternatives for java-rmi.cgi.

In any case, the game works in both browsers now, and I can even open and view pdf files in Chrome now, something which previously I could only do in Firefox for some reason.

Thanks a lot for the support. Vista crashed a couple of days ago and I am trying to get myself to dive into the world of Ubuntu. So your help today was really encouraging. You guys and this forum rock! Expect more questions soon :p

Regards,
Nick

---

### Post by dBuster on 2010-05-08
The trick worked to remove icedtea and use the sun plugin, which I could have sworn was not available two days ago.  Any how..

Anyone have issues with sites such as pogo only working with firefox?  I get the game loading screen with chrome however after some time the window closes and no game...

---

### Post by YAN3 on 2010-05-20
Hi guys. Help again!
I had to format my laptop and reinstall Ubuntu, and I'm having the same problem with Java again (although this time I'm using a 32-bit version).

I tried following QIII's advice again, but I can't even find sun-java6 in the Synaptic Package Manager..

I tried Mike's way, but the Sun JAVA 6 Plugin was not available for installation, only for 'more information'. I also tried to install the Ubuntu restricted extras thing from the software center but that didn't make that game function..

What should I do? Thanks a lot in advance.
Nick

---

### Post by QIII on 2010-05-20
Did you add the Lucid partner repository?

Java has been deprecated in the "standard" repositories.  If you don't have the partner repository, you won't find Java in Synaptic.

---

### Post by YAN3 on 2010-05-20
You mean using:
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"?
Yeah I did. What else can I try?

---

### Post by QIII on 2010-05-20
Go to System | Administration | Software Sources

I'm not at my machine right now, but I think the tab you want to click says something like "Other Software".  Make sure the partner repo is checked.

That should get the packages in Synaptic.

Alternatively, you could install from the terminal (provided the partner repo is available):

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```If that works, then after all the agreeing with the license bit and such and the packages install

```
sudo update-java-alternatives --set java-6-sun
```

---

### Post by YAN3 on 2010-05-20
Using sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts

I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin

What does this mean?

---

### Post by YAN3 on 2010-05-20
> **QIII said:**
> Go to System | Administration | Software Sources

I'm not at my machine right now, but I think the tab you want to click says something like "Other Software".  Make sure the partner repo is checked.

That should get the packages in Synaptic.

```
sudo update-java-alternatives --set java-6-sun
```

Ok that worked :D
Thanks a lot man :) I really need some way of understanding what's going on here and what I just did :P I still don't quite understand :)

---

### Post by Hastor on 2010-05-20
Hey man, I'm pretty much in the same boat as you in the moment as much as understanding exactly what type of environment I'm working in. The best bet, I would say, for figuring out what's around would be the Ubuntu guide at [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
It's free and, to my knowledge, applicable to Lucid Lynx. I'm not recommending trying to cram through it all, but having something on your desktop as a reference tool would probably be a huge help. Also, just skimming through really helps improve your "ubuntu literacy" or understanding of what you're working with. 
Good luck, man!  :KS

---

### Post by suresnjain on 2010-05-21
I was having problem with icedtea plugin.It was dead slow in Firefox and did not work in the chromium.I did whatever is suggested here.Removed Icedtea via synaptic.Installed Sun Java Plug in via Synaptic.Also did check that both  Java runtime are there already.Hey,presto.It worked like a charm.Thanks brother,thanks forum.

---

### Post by cazazo on 2010-05-22
I've done the exact same thing for Lucid 10.04LTS and did work perfectly! The only thing I did removed the Iced using the Software Center as well. Glad it's working!

---

### Post by YAN3 on 2010-05-23
Thanks a lot Hastor! I appreciate it :)

---

### Post by lamino144 on 2011-10-08
Wow! Thanks a lot, this works like charm. What can I say... just amazing!

---

