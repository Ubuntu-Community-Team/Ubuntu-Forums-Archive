---
title: "Java not recognizing keyboard"
date: 2011-02-09
forum: General Help
---

### Post by Dubslow on 2011-02-09
Anytime I try to do anything with Java, the mouse works fine but the keyboard does not seem to interface with Java. I first tried this with minecraft, but then tested it with an in browser applet and got the same results.

I first tried dl'ing Java off the Sun website and following their install instructions, but that didn't work. Then I tried "apt-get install sun-java-jre6" which still didn't fix Java. Then I tried Iced Tea via the Software Manager. Then, in my best attempt to fix it, I deleted the installed files from the Sun DL, which was in /usr/local. Then I purged sun-java-jre6 with apt-get and remained with Iced Tea, which leaves me where I am now. Anybody know what to do?

---

### Post by lykeion on 2011-02-10
I think you need to explain what you mean with "the keyboard does not seem to interface with Java". 

You can try this asteroids game written in Java: [http://cloningtheclassics.com/asteroids/play-asteroids/](http://cloningtheclassics.com/asteroids/play-asteroids/)
Can you move the spaceship around with your arrow keys?

---

### Post by Dubslow on 2011-02-10
Sorry, I meant that Java is not interacting with my keyboard, as in pressing any keys does not produce any sort of result at all. I tried your game, and it tells me to install Java, where as with this game, [http://www.jgames.com/cgi-bin/crostics.cgi?i=laura1|Laura's+First+Puzzle&f=](http://www.jgames.com/cgi-bin/crostics.cgi?i=laura1|Laura's+First+Puzzle&f=)
the game loads fine except that the keyboard doesn't work. Like I said, Minecraft opens and runs fine, except that I can't move from my spawn block except by digging down. 

As an extra detail, in my linked game, when I try and type it wound up in the URL instead of the game. (I made sure I was clicking in the right place because a friend with Ubuntu is using that game just fine, keyboard and all.)

Edit: I just had the same friend try the asteroid game, and it wouldn't load for her either, even though everything else in Java works fine for her.

---

### Post by lykeion on 2011-02-10
I tried the crossword game and I can't enter anything with keyboard either. I don't think it's a Java issue though, but rather something wrong with the game itself, or maybe I just don't understand how it works. I think you'll get more help on this particular game by contacting the game site.

The asteroids game is an applet (I didn't write it) but when it says you need to install Java it seems you don't have the Java browser plugin installed. Can you try this: Enter "about:plugins" (without quotes) in the address field of Firefox (I assume you use this browser). You should see an entry like this "Java(TM) Plug-in 1.6.0_22" if you have the Sun Java browser plugin installed. If you have IcedTea Java browser plugin you should see something similar, I think the current version is 1.6.0_b18. If you don't see anything like that you have no browser plugin installed.

If you have the IcedTea plugin installed and have problems with Java games, I recommend you to uninstall it and install Sun Java plugin. In Ubuntu the way to install is not by manually downloading stuff from the web (like in Windows), instead you use a package manager like Synaptic.

1. Start Synaptic (System > Administration > Synaptic Package Manager)
2. Start by updating the repositories by clicking the big Reload button at top.
3. Enter icedtea in search field. If icedtea6-plugin is installed it's marked green. Right-click it and select "Mark for removal". Then click Apply at top.
4. Enable the Partner repositories (it's where Sun Java is). Select Settings > Repositories > Other Software tab and make sure the line with "http://archive.canonical.com/ubuntu maverick partner" is ticked. And click Reload afterwards again.
5. Enter "sun-java6" in search field and right-click the package sun-java6-plugin > "Mark for installation"
6. Quit Synaptic and restart Firefox

Now you should be able to play the Asteroids game and other Java games. Hopefully someone else can help you with your crosswords game.

---

### Post by Dubslow on 2011-02-10
The crosswords game was just a test, and it did work on my friend's computer. I am using Chrome, but tried about:plugins anyways and the first result was 
"IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.5 (6b20-1.9.5-0ubuntu1))
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.5 (6b20-1.9.5-0ubuntu1)) executes Java applets."

Like I said, I have tried the Sun Java package with apt-get and dl'ed and installed the .bin file from their website, neither of which worked. I will however uninstall Iced Tea and try apt-get again. (I don't use Synaptic, I use the default Software Center from Ubuntu.)

---

### Post by lykeion on 2011-02-10
Crosswords game works for me too, but you must enter the right characters. You'll get no input when entering wrong ones.

You said you tried installing sun-java6-jre, this is not the same as sun-java6-plugin. Using Synaptic or USC is pretty much the same (even though you can't manage repositories in USC). Uninstall icedtea6-plugin and install sun-java6-plugin. Restart browser.

---

### Post by Dubslow on 2011-02-10
Hmm...
I removed everything that came up in USC when I searched iced or java, then 
apt-get install sun-java6-jre
apt-get install sun-java6-plugin (as per your suggestion)
I've restarted Chrome, which no longer shows Iced Tea but 
"Java(TM) Plug-in 1.6.0_22
The next generation Java plug-in for Mozilla browsers."

And I tried both games, neither worked. The asteroid game still refused to load at all.
Actually, just tried the crossword, and after some finagling I was able to type letters, but Asteroids still won't work and Minecraft still only partially works. I'm going to try rebooting.
Edit: No dice. I should note that in Minecraft, pressing a key temporarily lags my vision, and I can get the escape menu by pressing escape, and then alt-tabbing out and back, at which point the menu appears, so there is some sort of keyboard-java interaction.

---

### Post by lykeion on 2011-02-10
Okay, I tested some sites/applets with Chromium + Sun Java plugin:
[Java.com test]("http://www.java.com/en/download/testjava.jsp") - works
[Minecraft]("http://www.minecraft.net/play.jsp?server=224a2ae72c2ca755afd38de5a30178bf") - works
[JGames Acrostic game]("http://www.jgames.com/cgi-bin/crostics.cgi?i=laura1|Laura's+First+Puzzle&f=") - works
[Asteroids game applet]("http://cloningtheclassics.com/asteroids/play-asteroids/") - does NOT work

I can't reproduce your problem, although it's strange that the Asteroids game doesn't work (it works fine in Firefox). Maybe some other Chromium-using poster can help you further. The only thing I can do is to direct you to: [http://code.google.com/p/chromium/issues/list](http://code.google.com/p/chromium/issues/list)

---

### Post by Dubslow on 2011-02-10
Java says it's working,
Minecraft still has the same issues, 
Acrostic works if I hit the clear all entries button first
     I had something similar in Mathematica where the keys didn't work until         I went into the menus
Asteroids doesn't work at all. 

Thanks for trying, I'm getting a better idea of what does and doesn't work. 
Anybody else got any ideas?

---

### Post by Dubslow on 2011-02-28
Ah. My friend figured out the problem with a little help from Google.
It's a fairly well known bug with the iBus daemon that disables keyboard inputs with Java.

[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/481656](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/481656)
[http://ubuntuforums.org/showthread.php?t=1613677](http://ubuntuforums.org/showthread.php?t=1613677)

---

