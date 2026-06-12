---
title: "What to do with a .bin?"
date: 2006-03-22
forum: General Help
---

### Post by vindicta on 2006-03-22
I've downloaded Planeshift and I have no idea how to install it.  It is a .bin.:confused:

---

### Post by vindicta on 2006-03-22
i figured it.

---

### Post by Shampyon on 2006-03-22
[QUOTE=vindicta]i figured it.[/QUOTE]
 So what was it? Was it the disc-image type bin or the Linux executable type?
And how to you get it running? It'll be handy for if (or more likely, when) I run into one.

---

### Post by lothar_m on 2006-03-22
[QUOTE=vindicta]i figured it.[/QUOTE]
did you know that you could share your discoveries with other users??

thats the objective of these forums... sharing knowledge between users.

---

### Post by aysiu on 2006-03-22
[QUOTE=lothar_m]did you know that you could share your discoveries with other users??

thats the objective of these forums... sharing knowledge between users.[/QUOTE] Especially since one of the ways I do (and other users should) find things is by searching the forums. A search for *planeshift .bin* on these forums would pop only "I figured it out."

Please do share what you did to get it to work.

---

### Post by bionnaki on 2006-03-22
.bin is an image file, right? I guess just burn to disk with k3b

---

### Post by Shampyon on 2006-03-23
I did a search on FileXT. Apparently .bin is used for a lot of different filetypes, including Avast Antivirus, image files, and Linux self-extracting binary executables.

I found a match for the latter on Sun's Java site.

Apparently you have to set permissions to run the executable:
**[FONT="Courier New"]chmod +x filename.bin[/FONT]**
Then simply enter [FONT="Courier New"]**./filename.bin**[/FONT]

Side note, probably doesn't apply to all .bin files - the howto (here: [FONT="Courier New"]**[http://java.sun.com/j2se/1.4.2/install-linux.html](http://java.sun.com/j2se/1.4.2/install-linux.html)**[/FONT]) also mentions that their particular binary installs system preferences in that executable's installation directory. Something to do sharing preferences with other Java Runtimes on your network. If you only want your options to be used on your local machine, you use [FONT="Courier New"]**./filename --localinstall**[/FONT]
This saves the preferences in the[FONT="Courier New"]** /etc**[/FONT] directory.

---

### Post by rattking on 2006-03-23
there are a few tools to help figureout what an unknown file is
the cli program file tries to determine file type
sometimes it reports -data- so not always so helpfull 
file filename.bin

and when in a real pinch (and i mean real pinch because this is a pain)
strings filename |less
and look for any text that looks familiar

---

### Post by yager on 2006-03-25
[QUOTE=vindicta]i figured it.[/QUOTE]

I figured it out too...........


You guys crack me up.  It sure would have been nice if vindicta had revealed the ancient secret of what he did.  Perhaps we will never know his way.  This is what I did to make it work.  It is not clean, but it should take the edge off for a hardcore MMORPG junkie.

I downloaded the .bin from planeshift at:

[http://www.filecloud.com/files/file.php?file_id=3040](http://www.filecloud.com/files/file.php?file_id=3040)

Next, I opened up the terminal and typed:

```
chmod +x /[COLOR="Blue"]download directory name[/COLOR]/PlaneShift_CBV0.3.013.i686.bin
```

Next, things got interesting as I am pretty new to this Linux thing.

I had to then execute this file by entering.

```
sudo /[COLOR="Blue"]download directory name[/COLOR]/PlaneShift_CBV0.3.013.i686.bin
```

The install will start and ask you your preferences.  I chose to have it add the game to the Gnome menus and left the file permissions as installed.  Again I am very new to Linux so I stuck with as many of the default choices as possible.

Once installed, I had an issue with being able to launch Planeshift but I got the whole rights things worked out finally.  Go to System/Administration/Users and Groups and choose the Groups tab.  Make sure that the Show all groups and users check box is marked and find the games group.  Add your login to this group along with anyone else on your system that may want to play Planeshift.

Log out and then log back in to pick up your new rights.  You will find that Planeshift was added to your Applications/Games menu and you should now be able to launch the game.  I suggest that you check the Planeshift Setup just to make sure all of your preferences are as you want them.  The default is to launch in a window.

BTW, there is a known bug that I came across in the zoneinfo.xml file.  Go to this forum thread for all the details and the file to fix the error.

[http://planeshift.oodlz.com/wbboard/thread.php?threadid=22468&boardid=41&styleid=3&sid=cd070da2417e7e0a014ca9dc92803d1b](http://planeshift.oodlz.com/wbboard/thread.php?threadid=22468&boardid=41&styleid=3&sid=cd070da2417e7e0a014ca9dc92803d1b)

I hope this helps some diehard MMORPG fans.

---

### Post by Jedeye on 2006-04-12
[QUOTE=yager]I figured it out too...........


You guys crack me up.  It sure would have been nice if vindicta had revealed the ancient secret of what he did.  Perhaps we will never know his way.  This is what I did to make it work.  It is not clean, but it should take the edge off for a hardcore MMORPG junkie.

I downloaded the .bin from planeshift at:

[http://www.filecloud.com/files/file.php?file_id=3040](http://www.filecloud.com/files/file.php?file_id=3040)

Next, I opened up the terminal and typed:

```
chmod +x /[COLOR="Blue"]download directory name[/COLOR]/PlaneShift_CBV0.3.013.i686.bin
```

Next, things got interesting as I am pretty new to this Linux thing.

I had to then execute this file by entering.

```
sudo /[COLOR="Blue"]download directory name[/COLOR]/PlaneShift_CBV0.3.013.i686.bin
```

The install will start and ask you your preferences.  I chose to have it add the game to the Gnome menus and left the file permissions as installed.  Again I am very new to Linux so I stuck with as many of the default choices as possible.

Once installed, I had an issue with being able to launch Planeshift but I got the whole rights things worked out finally.  Go to System/Administration/Users and Groups and choose the Groups tab.  Make sure that the Show all groups and users check box is marked and find the games group.  Add your login to this group along with anyone else on your system that may want to play Planeshift.

Log out and then log back in to pick up your new rights.  You will find that Planeshift was added to your Applications/Games menu and you should now be able to launch the game.  I suggest that you check the Planeshift Setup just to make sure all of your preferences are as you want them.  The default is to launch in a window.

BTW, there is a known bug that I came across in the zoneinfo.xml file.  Go to this forum thread for all the details and the file to fix the error.

[http://planeshift.oodlz.com/wbboard/thread.php?threadid=22468&boardid=41&styleid=3&sid=cd070da2417e7e0a014ca9dc92803d1b](http://planeshift.oodlz.com/wbboard/thread.php?threadid=22468&boardid=41&styleid=3&sid=cd070da2417e7e0a014ca9dc92803d1b)

I hope this helps some diehard MMORPG fans.[/QUOTE]
That helped me out a lot, thanks!

---

### Post by lucky2 on 2006-04-24
The forum has moved, I hope this is at least similar to the post you referenced. Im still downloading the client. Never played an MMORPG myself, Looking fowrard to it.

[http://hydlaa.com/smf/index.php?PHPSESSID=c7bc2759b89c6f66920557d48bcb4f07&topic=20291.0](http://hydlaa.com/smf/index.php?PHPSESSID=c7bc2759b89c6f66920557d48bcb4f07&topic=20291.0)

Cheers.

---

