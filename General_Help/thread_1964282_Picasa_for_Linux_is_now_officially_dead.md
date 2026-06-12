---
title: "Picasa for Linux is now officially dead"
date: 2012-04-23
forum: General Help
---

### Post by Nick Payne on 2012-04-23
Second last bullet point here: [http://googleblog.blogspot.com.au/2012/04/spring-cleaning-in-spring.html]("http://googleblog.blogspot.com.au/2012/04/spring-cleaning-in-spring.html")

---

### Post by oldfred on 2012-04-23
I am running the Windows version with .wine in 12.04, so far without major issues. 

Not sure why anyone would want the Linux version as it is old and is just the old version running in .wine anyway.

From my history:

```

103  wget http://winezeug.googlecode.com/svn/trunk/winetricks
  104  sudo wget http://winezeug.googlecode.com/svn/trunk/winetricks
  105  sudo chmod 777 winetricks
  106  sudo apt-get install cabextract wine wine-gecko
  107  sudo apt-get update
  108  sudo apt-get upgrade
  109  history
  110  sudo apt-get install wine
  111  wine picasa39-setup.exe

```

---

### Post by techsupport on 2012-04-23
I'm running Linux Picasa 3.0 beta and I just installed it right now. Package is still available for download too.  Works terrific. Don't know how much better the windows version must be? What's the difference between Windows Picasa and Linux Picasa? Anyone have both running to tell us? I can't stand running Windows apps in Wine. Slow and choppy too.

You can get the Linux Version of Picasa 3.0 here:

```
wget http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb && sudo dpkg -i picasa_3.0-current_amd64.deb
```> **oldfred said:**
> I am running the Windows version with .wine in 12.04, so far without major issues. 

Not sure why anyone would want the Linux version as it is old and is just the old version running in .wine anyway.

From my history:

```

103  wget http://winezeug.googlecode.com/svn/trunk/winetricks
  104  sudo wget http://winezeug.googlecode.com/svn/trunk/winetricks
  105  sudo chmod 777 winetricks
  106  sudo apt-get install cabextract wine wine-gecko
  107  sudo apt-get update
  108  sudo apt-get upgrade
  109  history
  110  sudo apt-get install wine
  111  wine picasa39-setup.exe

```

---

### Post by Nick Payne on 2012-04-23
> **techsupport said:**
> What's the difference between Windows Picasa and Linux Picasa? Anyone have both running to tell us? I can't stand running Windows apps in Wine. Slow and choppy too.

You can get the Linux Version of Picasa 3.0 here:

```
wget http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb && sudo dpkg -i picasa_3.0-current_amd64.deb
```

There is no native Linux version of Picasa. What Google calls Picasa for Linux is the old Windows version running under Wine. That's what you get from the download link above.

---

### Post by cwwilson721 on 2012-04-23
> **oldfred said:**
> I am running the Windows version with .wine in 12.04, so far without major issues. 

Not sure why anyone would want the Linux version as it is old and is just the old version running in .wine anyway.

From my history:

```

103  [COLOR="Red"]wget http://winezeug.googlecode.com/svn/trunk/winetricks[/COLOR]
  104  [COLOR="red"]sudo wget http://winezeug.googlecode.com/svn/trunk/winetricks[/COLOR]
  105  [COLOR="red"]sudo chmod 777 winetricks[/COLOR]
  106  sudo apt-get install cabextract [COLOR="Red"]wine wine-gecko[/COLOR]
  107  sudo apt-get update
  108  sudo apt-get upgrade
  109  history
  110  sudo apt-get install wine
  111  wine picasa39-setup.exe

```
Just for future reference (and to save time/headaches), just use the command "winecfg', and it sets up your .wine folder with wine-gecko already setup for you. No additional "winetricks" help needed anymore. When installing wine, it also installs winetricks, too.

You can remove all parts in red from your setup script now (At least since wine version 1.3)

So new setup would be (assuming you have the wine1.3 PPA setup already, and picassa39-setup.exe in the proper place):
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine1.3 cabextract
winecfg
wine picassa39-setup.exe
```

Go to the [wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313"), and in the stickys, it has instructions for getting the PPA setup. Wine is now at 1.4+, but "wine1.3" installs the latest, no matter revision number, so far)

Lees typing is always better, for me at least. Less typeoze.

---

### Post by oldfred on 2012-04-23
@cwwilson721
Thanks for the update. I see my updates installed 1.4. Synaptic is showing winetricks, so I do not know which was used for my install. I will update my scripts.

---

### Post by cwwilson721 on 2012-04-24
I know the feeling...

I get "stuck" doing something one way, and then it becomes obsolete...lol

But, now that you mention it, I think you DO need to install winetricks separately...

I'll repost after I replace 11.10 w/12.04. I always do a "fresh" install, so I'll need to redo my wine. I'll let you know then.

---

### Post by Herman on 2012-04-24
> I'm running Linux Picasa 3.0 beta and I just installed it right now.  Package is still available for download too.  Works terrific. Don't know  how much better the windows version must be? What's the difference  between Windows Picasa and Linux Picasa? Anyone have both running to  tell us? I can't stand running Windows apps in Wine. Slow and choppy  too.Well if you have Picasa and Google Earth installed in Windows, you can use the geotagging tool in Picasa to insert your pictures into google earth and geotag them.
Geotagging photos is a useful way to record where on earth you took each photo. That can be important for some people, especially if the pictures are recording some kind of evidence or proof of something. For example the highest flood level recorded at a certain location might be recorded by taking pictures of the flood. If the picture is geotagged, it's possible to go back and locate the exact same spot the photo was taken at some time in the future. (Even if the place looks completely different by then). You may need to send that photographic information to a scientist who is studying flood heights and rainfall records in your area. Or maybe you just want to remember where you took those holiday snaps. When you're done you can save a folder full of geotagged pictures as a compressed .kmz file if you want, too, which can be emailed to a friend and opened in their google earth.

If you have a  GPS enabled camera so you can take photographs that are already geotagged, you can use the Windows version of Picasa to insert them in Google Earth to see where they were taken and possibly compress them into a .kmz, as already mentioned.

Unfortunately, the last time I looked at the Linux version of Picasa, it didn't have any capability for handling geotagged photographs that I could find at all. I was quite disappointed.

Then I got busy and wrote my own scripts and now I can process whole folders full of geotagged photos and open then in Google Earth in Ubuntu way quicker than I can do them one at a time in Windows, so I really don't care if we don't have Picasa, I don't need it for anything anyway.
I couldn't do without Google Earth though, Google Earth is great! :)

So at least that's the difference between the Windows version and Linux version as it affects me, there may be other features that other people would be looking for and I would be interested to read what features other people like.

---

