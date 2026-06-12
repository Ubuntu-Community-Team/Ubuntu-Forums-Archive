---
title: "Using Spotify URL:s"
date: 2009-09-08
forum: General Help
---

### Post by DJRadium on 2009-09-08
Hi all, sorry if my topic is a bit strange, but i don't know how to explain it in any other way. In windows, all you had to do was to click on a URL that linked to a spotify-song and that was it. But now when im using ubuntu, it doesn't work. I tried to follow this guide: [http://www.spotify.com/en/help/faq/w..._from_browsers]("http://www.spotify.com/en/help/faq/wine/#Opening_spotify_URIs_from_browsers") but i just don't get it. It explains how to do in "Epiphany" but, as i see it, not in Firefox. Since i'm very nooby at linux i don't want to mess around to much. Anyone got an idea what i should do?

---

### Post by callumacrae on 2009-09-08
Not sure what you're trying to do.

That guide means you can click on adverts, is that what you were trying to do?

---

### Post by themusicalduck on 2009-09-08
Which part of the guide don't you understand? It says you do the same thing for either epiphany or firefox.

---

### Post by ckonestroh on 2009-09-08
Ok, 

lets make this simple...

First lets do a bit of geek talk...

1. You want to run spotify well the best way to do so is in windows...

2. Emulator ----- duplicates a different system...

In this case we want to emulate windows...

They have a program called wine which allows you to run windows programs inside linux....

Wine can be a bit difficult.... Well your in luck there is a program called PlayonLinux...

PlayonLinux uses wine but already preinstalls programs that only run good in windows.... Examples Windows media player, AutoCad, Games like Call of duty, World of warcraft.... Windows Office 2003 and 2007...



Your luck has gone up .... They even have Spotify running in PlayonLinux...


Since your new words to luck up in your spare time...

Emulator       Wine for Linux



The link to PlayonLinux is here [Playonlinux]("http://www.playonlinux.com/")


Good luck,


have fun


later....


chris....

PS... To see an example of this PlayonLinux in action watch this Youtube video... Click [here]("http://www.youtube.com/watch?v=SKXp49-9L3c")

---

### Post by DJRadium on 2009-09-08
The titles says "Opening spotify URIs from browsers", which mean you can open URL:s like [http://open.spotify.com/track/2IAcYOEnZWTn3yR6LDslRY](http://open.spotify.com/track/2IAcYOEnZWTn3yR6LDslRY) directly from firefox to spotify. This do not work in ubuntu because "Firefox donät know how this address should be opened, befause the protocol isn't associated with any program. The guide tells you how to do this, but i don't understand it.

---

### Post by ckonestroh on 2009-09-08
Look your new to linux.... I understand quit reading these posts from people... If you want to learn a lot about desktop setup go to Youtube.com

search for this user:   [SIZE="3"][COLOR="Navy"]gotbletu[/COLOR][/SIZE]

he has a lot of great videos on general questions for desktop setup....


later...

---

### Post by themusicalduck on 2009-09-08
DJRadium

Since you posted that link I tried it myself to see if I can get the same result, but it doesn't work for me anyway.

If you still want to try it, then this is what the tutorial is saying to do in a slightly easier way.

Go to your home folder under Places. Right click on some space and click Create Document > Empty File. Name it browser2spotify

Open the file and copy this into it.

```
#!/bin/sh
exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$@"
```

Save the file. Back in the file browser, rename the file to .browser2spotify (the dot in front will make it hidden.)

Now go to Applications > Accessories > Terminal. Type this command into it and hit enter:

```
chmod 755 ~/.browser2spotify
```

Now open firefox and type ```
about:config
``` into the address bar.

Click through the warning and right click on the list of entries. Select New > Boolean and set it as it says in the guide.

Do the same again, but select New > String and name it as it says in the guide.

When you click on a link, it should ask to open the link with .browser2spotify, sadly this is as far as I got because it doesn't seem to want to load, but hopefully it'll work better for you.

---

### Post by Blakeseven on 2009-09-13
I am also a complete newbie in linux, have followed the suggestions made by the musical duck, and seem to have a similar end point - it asks me to choose an application to run it, but then seems to do nothing when I select .browser2spotify

the text edit window of .browser2spotify has what you typed in it (I cut and pasted) but now is in different colours. (I suspect this is not significant, but just identifying the functional parts, similar to formulae in an openoffice spreadsheet)

The cut and paste has "C:\Program Files\spotify\spotify.exec" within it, which I take to be the path to spotify app, but I am such a newbie I am not sure how to check that this is the correct path on my computer.

---

### Post by GH68 on 2009-09-14
I followed a tutorial found here: [http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/]("http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/"). Check the comments after the tutorial, since it seems not to work straight away for everyone. I had some problems myself due to mistyping and the fact that the error messages I got didn't seem relevant at all.

Good luck!

---

### Post by DivineOmega on 2009-09-21
I wrote a tutorial on this subject which may be of use:

[How to get Spotify links to work in Linux]("http://jordanhall.co.uk/ubuntu-linux/how-to-get-getting-spotify-links-to-work-in-linux/")

---

### Post by nukleuzN on 2010-02-04
> **GH68 said:**
> I followed a tutorial found here: [http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/]("http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/"). Check the comments after the tutorial, since it seems not to work straight away for everyone. I had some problems myself due to mistyping and the fact that the error messages I got didn't seem relevant at all.

Good luck!

Adding: *network.protocol-handler.expose.spotify* in about:config with value *false* did the trick if u'r using FF v3.5.x. You also need to make the spotify.sh-file as described in the quoted blog entry.

After adding this line, u will be prompted to choose application to open spotify links (of course this will first happen when you click on one spotify-link). Then browse the spotify.sh-file and check the box "Allways use for spotify-links" (or something similar).

---

### Post by lunalui on 2010-09-28
> **GH68 said:**
> I followed a tutorial found here: [http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/](http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/). Check the comments after the tutorial, since it seems not to work straight away for everyone. I had some problems myself due to mistyping and the fact that the error messages I got didn't seem relevant at all.

Good luck!

Hi, I've followed this tutorial, too but all I managed to get is that firefox now launches spotify when clicking on the links, but spotify does not open them. Any ideas how to fix this? thanks in advance

---

