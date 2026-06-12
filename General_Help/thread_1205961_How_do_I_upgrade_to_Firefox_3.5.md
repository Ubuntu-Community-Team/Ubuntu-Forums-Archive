---
title: "How do I upgrade to Firefox 3.5?"
date: 2009-07-06
forum: General Help
---

### Post by harecanada on 2009-07-06
Hi.
How do I upgrade to FF 3.5? I downloaded the firefox-3.5.tar.bz2 but now what? Can someone give me a hand? I'm not sure what to do next.
harecanada

---

### Post by michy99 on 2009-07-06
I just installed 3.5 using the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Go down to the section that says Installing Other Versions.

---

### Post by t0p on 2009-07-06
I think what you've downloaded is an archive containing a Firefox-3.5 binary.  What you need to do is extract it using Archive Manager - right-click on the archive, select **Extract here**.

A folder will be extracted - called **firefox** I think.  If you look in it, you'll see a number of files, one of which is a shell script called **firefox**.

What I would do is open a terminal.  Navigate to the firefox folder.  If you extracted the archive on your Desktop, you will change to the firefox folder with the command

```
cd ~/Desktop/firefox
```

Now run the shell script.  You do this with the command

```
./firefox
```

That should start Firefox-3.5 for you.

It will be more convenient in the future if you make a launcher to run the script, so you can start Firefox-3.5 without having to mess with the terminal.  You can do that by right-clicking on the top panel and selecting **Add New Item** then select to create a launcher.

**EDIT:** You may feel more comfortable installing Firefox-3.5 as a .deb, through the package manager.  To do that, read the instructions [here]("http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm").

---

### Post by lovinglinux on 2009-07-06
...and here we go again.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Shiretoko+PPA, Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT). I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

[35 and counting...](http://www.uluga.ubuntuforums.org/showthread.php?t=1200781)

---

### Post by aysiu on 2009-07-06
I agree with lovinglinux here.

If you want a no-frills one-paste-command to get the .tar.bz2 set up, [Psychocats](http://psychocats.net/ubuntu/firefox) is the way to go.

[UbuntuZilla](http://ubuntuzilla.wiki.sourceforge.net/) has some neat features, though, especially if you haven't already downloaded the .tar.bz2. It'll automatically fetch the latest version and verify the download. If one download mirror isn't available, it'll automatically fetch Firefox from another mirror. It can also be used to install the latest versions of Thunderbird or Seamonkey.

---

### Post by harecanada on 2009-07-07
Thanks Everybody.
I'll post how I do and what I use.
harecanada

---

### Post by Locutus_of_Borg on 2009-07-07
i recommend you compile the source code

---

### Post by Teabicky on 2009-07-07
I used ubutnuzilla. It was really easy, now I have firefox 3.5 to zip round the net at impressive speeds with.

---

### Post by nr0mx on 2009-07-07
I use Ubuntuzilla, and I've found it really great at this kind of stuff. I find the fact that you can manually specify the version you want to install quite useful.

---

### Post by lovinglinux on 2009-07-07
I have updated the "Installing Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) with a detailed explanation of each installation method provided, comparing the most important differences.

---

### Post by Krupski on 2009-07-07
> **harecanada said:**
> Hi.
How do I upgrade to FF 3.5? I downloaded the firefox-3.5.tar.bz2 but now what? Can someone give me a hand? I'm not sure what to do next.
harecanada

All I did was go into Synaptic Package Manager, search "Firefox", checked "3.5" and let 'er rip.

THEN... open a console window and type these lines (use 'sudo' if necessary):

```

cd /usr/bin
unlink firefox
ln -s firefox-3.5 firefox
exit

```

Now your old Firefox shortcut will bring up v3.5!

In fact, I'm using it right now!

---

### Post by harecanada on 2009-07-08
Thanks lovinglinux. I used your how to and it works great. I much appreciate it.
harecanada

---

### Post by lovinglinux on 2009-07-08
> **harecanada said:**
> Thanks lovinglinux. I used your how to and it works great. I much appreciate it.
harecanada

You are welcome.

---

