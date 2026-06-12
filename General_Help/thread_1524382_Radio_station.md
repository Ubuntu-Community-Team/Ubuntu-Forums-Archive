---
title: "Radio station"
date: 2010-07-05
forum: General Help
---

### Post by cuddy2977 on 2010-07-05
[FONT="Trebuchet MS"]Hi.

I’ve a relatively non-technical friend who I’ve done an install of Ubuntu 9.10 for.

She’s relatively happy with the arrangement, apart rom one thing.

There’s a particular internet radio station that she can’t access, Saint FM, and I’d like to try finding a relatively end-user way of doing it.

I’ve tried opening the stream ( [FONT="Courier New"]mms://saintfm.stpetershigh.essex.sch.uk:8134[/FONT] ) using the Internet Radio Station options in Rhythmbox, but with little success: basically Rhythmbox just crashes.

Is there a (relatively) easy way for a non-technical user to open this stream?

(I’d rather not install iTunes, via Wine, btw, as her machines hard-drive isn’t exactly big.)[/FONT]

---

### Post by Maximus20 on 2010-07-05
Well to answer your question(problem) just try to follow this tutorial :

If you intend to listen to mp3 or AAC streams, you'll need to enable the universe and/or multiverse repositories to get the proper codecs. Let's use gstreamer codecs as an example so you can listen to radio with Rhythmbox.

Using synaptic or apt-get, for mp3 download gstreamer0.8-mad
For aac decoding, download gstreamer0.8-faad

1) Click the streaming link with the format of your choice in your browser.

2) If a dialog box appears asking you if you want to choose an application or save the file to disk, I save it to disk! (usually some sort of playlist, .pls file what-have-you)

3) use an editor (gedit, nano, whatever) to look inside this file. You'll find the proper http address of the "channel" You might find several lines of channel url's there which should be self-explanatory as to which one you really want.

4) Now open up Rhythmbox, right-click on the radio icon, and add a new station using the address we found in step 3 by placing the url in the location box.

5) Click the play button and enjoy!

Orginal posted by stream303 :P.

---

### Post by ajgreeny on 2010-07-05
I have just tried this radio station to check it out and using this link
_[http://www.saintfm.org.uk/listenlive.html](http://www.saintfm.org.uk/listenlive.html)_
I went straight in with no problems using the plugin of my browser, Firefox, so that is an alternative way, though I could not get it to play in rhythmbox, nor could I get the stream you linked to play in RB either.

However, the steam you found will play in gnome-mplayer with no problem, though you may need to ensure that you have all the necessary codecs required by installing ubuntu-restricted-extras.

---

### Post by HermanAB on 2010-07-05
Howdy,

Do yourself a favour and install Streamtuner.

---

### Post by cuddy2977 on 2010-07-05
> **ajgreeny said:**
> I have just tried this radio station to check it out and using this link
_[http://www.saintfm.org.uk/listenlive.html](http://www.saintfm.org.uk/listenlive.html)_
I went straight in with no problems using the plugin of my browser, Firefox, so that is an alternative way, though I could not get it to play in rhythmbox, nor could I get the stream you linked to play in RB either.

However, the steam you found will play in gnome-mplayer with no problem, though you may need to ensure that you have all the necessary codecs required by installing ubuntu-restricted-extras.

Cheers, AJ: that sounds idea, if she can get it working: I don’t know if she’s tried that, as yet: I’m *fairly* sure the correct codecs are installed.

I’ve also been told the stream in question is using an older WMA format that still isn’t fully supported in Ubuntu, as yet …

---

