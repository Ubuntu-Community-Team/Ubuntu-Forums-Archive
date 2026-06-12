---
title: "Problems with Flash"
date: 2012-02-11
forum: General Help
---

### Post by F104G on 2012-02-11
Ubuntu 11.10
64 bit
Firefox 10.0

Hello people!  Can anybody figure this out?
If I try to play something in BBCiPlayer I get a message saying "You need to install Flash to play this video" but when I look in the software centre it tells me it's already installed.  I tried removing it and re-installing but no joy. 
Another symptom: in YouTube videos appear in a small window in the top-left corner of the normal window - no sound in Youtube either.

:confused:

---

### Post by raja.genupula on 2012-02-11
install Flash Aid to firefox and try again .may be that gonna solve the issue .

---

### Post by F104G on 2012-02-12
> **raja.genupula said:**
> install Flash Aid to firefox and try again .may be that gonna solve the issue .

Well... I tried that but was unsuccessful, getting this message:
"The add-on could not be downloaded because of a connection failure on addons.mozilla.org"

It feels like I'm missing something obvious but I'm stumped.
Hmmm...

---

### Post by Gremlinzzz on 2012-02-12
maybe update flash
get the one you need
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
then extract it rename the folder to  plugins
then go to mozilla folder and replace the plugins folder
with the one you renamed:popcorn:

guess getting lazy,don't replace the plugins folder there maybe plugins in it.just open the flash folder and get file named libflashplayer.so and put that plugin in the mozilla plugins folder.but if there is no plugins folder create one and put libflashplayer.so in it

---

### Post by F104G on 2012-02-13
> **Gremlinzzz said:**
> just open the flash folder and get file named libflashplayer.so and put that plugin in the mozilla plugins folder.but if there is no plugins folder create one and put libflashplayer.so in it

Tried that: permission denied :confused:
And yes: I'm the only user of this machine, so I can't log out and then back in at a higher level.  Or can i?

---

### Post by flipper T on 2012-02-13
open a terminal and type

¨gksudo nautilus¨

enter your password when prompted.

you now have all the authority you need to move the file.

oh, ps...when using sudo / gksudo, linux will assume you know what you are doing...so be sure that you do

---

### Post by F104G on 2012-02-13
> **flipper T said:**
> open a terminal and type

¨gksudo nautilus¨

enter your password when prompted.

you now have all the authority you need to move the file.

Thanks.
Tried it - copied across the file - restarted the computer...

Still no joy.  BBCiPlayer still tells me I need Flash Player.
As an aside: on some other websites (those with music files that play automatically) I get the bar at the top of the screen saying "install missing plugins" appear.  If I click the button I get a window open telling me that Gnash is needed, but if I click continue it then says It's already installed.   Gah ](*,)

---

### Post by pqwoerituytrueiwoq on 2012-02-13
maybe it uses shockwave not flash in which case you have 3 options
1) use wine + windows firefox + shockwave
2) virtual box + windows + windows firefox+ shockwave
3) wine and complain to the site owner about it telling them you use flash or better yet html5

you can get the latest version of flash aid here:
[https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads)
direct link to file below
[https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.3-fx-linux.xpi](https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.3-fx-linux.xpi)

make sure the plugin is enabled in your browser

edit:
looks like the site does use flash (BBCiPlayer)

---

### Post by flipper T on 2012-02-13
the last post that i recall flash-aid not resolving, was down to the use of a very old version of firefox.

[COLOR=Yellow]is your firefox up to date ?[/COLOR] [COLOR=Black]...ignore, just re read your post[/COLOR]

same problem in chromium ?....but still try this

ps bbc iplayer uses flash...watching it now

---

### Post by F104G on 2012-02-13
> **flipper T said:**
> the last post that i recall flash-aid not resolving, was down to the use of a very old version of firefox.

[COLOR=Yellow]is your firefox up to date ?[/COLOR] [COLOR=Black]...ignore, just re read your post[/COLOR]

same problem in chromium ?....but still try this

ps bbc iplayer uses flash...watching it now

Yep: same thing in Google Chrome.
BTW - it's not that Flash Aid didn't fix it - I was simply unable to download Flash Aid.  I simply get the rather cryptic message "There was an error downloading Flash Aid"
Just tried it again and it's the same, but I have no problem downloading anything else from the Add Ons Manager.
Strange huh?

---

### Post by flipper T on 2012-02-13
the author of flash aid is a member of thos forum..¨loving linux¨, i seem to recall.

perhaps he can help

i´m out of ideas as flash aid working fine for me.

good luck

---

### Post by HiImTye on 2012-02-13
in firefox, go to edit>preferences then choose the 'applications' tab. once there, scroll down until you find 'Shockwave Flash file' and make sure that 'Use Shockwave Flash' is selected. if it is, go to youtube and see if you can play a video there

if flash is installed, it might be a firefox extension blocking flash from loading, such as NoScript, AdBlockPlus or Ghostery

---

### Post by pqwoerituytrueiwoq on 2012-02-13
> **F104G said:**
> Yep: same thing in Google Chrome.
BTW - it's not that Flash Aid didn't fix it - I was simply unable to download Flash Aid.  I simply get the rather cryptic message "**There was an error downloading Flash Aid**"
Just tried it again and it's the same, but I have no problem downloading anything else from the Add Ons Manager.
Strange huh?which i why i linked to the copy on github in post 8

---

### Post by F104G on 2012-02-14
> **pqwoerituytrueiwoq said:**
> which i why i linked to the copy on github in post 8

Yes - sorry.  I obviously wasn't paying attention. :redface:

---

### Post by F104G on 2012-02-14
> **HiImTye said:**
> in firefox, go to edit>preferences then choose the 'applications' tab. once there, scroll down until you find 'Shockwave Flash file'

Hmmm... it's not there.  The alphabetical list goes straight from *RAR Archive* to *Video Podcast*.  There is, though, an entry further up for *Flash Video*.  This is marked as *Use VLC Multimedia plug-in*

---

### Post by HiImTye on 2012-02-14
that is something separate.
it appears that the flash player is either not installed or not installed correctly. you could verify this by typing about:plugins and finding that there is no entry for 'Shockwave Flash'

I would suggest removing and reinstalling flash player

---

### Post by F104G on 2012-02-14
> **HiImTye said:**
> I would suggest removing and reinstalling flash player

Yep: done that quite a few times now.  Nothing seems to work.  'Tis strange...

---

### Post by Gremlinzzz on 2012-02-14
> **F104G said:**
> Tried that: permission denied :confused:
And yes: I'm the only user of this machine, so I can't log out and then back in at a higher level.  Or can i?

you shouldn't need permission.its the Mozilla folder in hidden files.inside folder there might be or not a plugins folder.thats where you put libflashplayer.so /if plugins folder exist put file in if it doesn't create folder inside of mozilla folder and name it plugins:popcorn:


getting to Mozilla folder click your home folder and on top where you will see view click it and choose show hidden files scroll to mozilla:popcorn:

---

### Post by F104G on 2012-02-15
> **Gremlinzzz said:**
> getting to Mozilla folder click your home folder and on top where you will see view click it and choose show hidden files scroll to mozilla:popcorn:

Now I AM confused: there is no Mozilla folder in Home.  There is one called .mozilla - is that what you mean?  What I do have isthese 7 folders:

usr/lib/mozilla
usr/lib/mozilla-firefox
usr/lib/python2.6/dist-packages/orca/scripts/apps/mozilla
usr/lib/python2.7/dist-packages/orca/scripts/apps/mozilla
usr/share/ca-certificates/mozilla
usr/share/pyshared/orca/scripts/apps/mozilla
usr/share/vlc/mozilla

---

### Post by Gremlinzzz on 2012-02-15
> **F104G said:**
> Now I AM confused: there is no Mozilla folder in Home.  There is one called .mozilla - is that what you mean?  What I do have isthese 7 folders:

usr/lib/mozilla
usr/lib/mozilla-firefox
usr/lib/python2.6/dist-packages/orca/scripts/apps/mozilla
usr/lib/python2.7/dist-packages/orca/scripts/apps/mozilla
usr/share/ca-certificates/mozilla
usr/share/pyshared/orca/scripts/apps/mozilla
usr/share/vlc/mozilla

There is one called .mozilla - is that what you mean? yeah thats the one do you have a plugins folder inside? if not create a folder and name it plugins then put libflashplayer.so in the plugins folder. thats the way you update flashplayer,

---

### Post by pqwoerituytrueiwoq on 2012-02-15
lets make this easy
open terminal and run:
[FONT=Courier New]nautilus /home/$USER/.mozilla[/FONT]

---

### Post by F104G on 2012-02-19
> **pqwoerituytrueiwoq said:**
> lets make this easy
open terminal and run:
[FONT=Courier New]nautilus /home/$USER/.mozilla[/FONT]

OK
the folder contains 1 file (firefox.last-version), and 2 folders: extensions and firefox

---

### Post by F104G on 2012-02-19
> **Gremlinzzz said:**
> create a folder and name it plugins then put libflashplayer.so in the plugins folder. thats the way you update flashplayer,

Alrightie!  Done that and dropped libflashplayer.so into it.
I will report back in a mo'

---

### Post by F104G on 2012-02-19
A big THANKYOU to all of you for your help and suggestions.
Everything's working again now 8-)

---

