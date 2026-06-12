---
title: "Too loud when starting up."
date: 2011-01-09
forum: General Help
---

### Post by zami on 2011-01-09
In Sound Preferences,
I have volume muted (currently)
Alert volume: muted
Sound theme : none

But I am still hearing full volume bongos when I restart X, or restart the computer.

What's causing this?  What do I do?

Volume elsewhere seems to be fine.  No system sounds (as per settings) and the volume goes up/down just as it should.

-zami

Ubuntu 10.10

---

### Post by zami on 2011-01-11
This is still a problem for me, and I haven't had any luck Googling for answers.

I've noticed, it's a log-in issue only.  I can make it happen by switching users, or when restarting X.  When I start up the computer, I have it set to auto-login, so I don't hear the mega-loud bongos then.

In the "Login Screen Settings", I have "play login sound" UNchecked.

Thanks for any help or suggestions.

-zami

---

### Post by Jamezo97 on 2011-01-11
Hmmm, have you tried going to 
'System-Administration-Login Screen'
.Then press the unlock button, and type in your password, then uncheck the "Play Login Sound" check box. That should turn off the startup sound.
I don't know whether that will work, because I have ubuntu 10.04, but it should be roughly the same...

Image here:[HERE]("http://i54.tinypic.com/2ustqn5.png")

Mind you, thats only a temporary fix...
If you have Audacity and you know where the startup sound file is, then you could open it up in audacity and turn down the sound by going to 'Effect-Amplify' and push the slider to the left about 10-20 decibels...
Ill see if i can find where that sound file is...

I found it:
Go to '/usr/share/sounds/ubuntu/stereo' and look for the file 
desktop-login.ogg
Open that up with Audacity and go to 
Effect-Amplify
and then push the slider to the left about 10-20 decibels. If you can't press the OK button, check "Allow Clipping".
Then export the file as a .wav(File-Export), then use vlc or something to convert it to an .ogg and then replace the old file with the newer one... Just make sure to keep a backup... Don't want to make a mistake and loose the startup sound all together...
(
To convert something in VLC:
Start up VLC
Press 'CTRL+r' or just go to 'Media-Convert/Save...'
Click add and choose your new .wav file.
Click 'Convert / Save'
Choose your destination file
And choose the profile that you want to save it in (Audo - Vorbis (OGG))
Click start and wait for the playing slider bar to stop.
And there you go! One OGG file coming right up!
)
Oh wait... I just realized that when your exporting the .wav you can choose to export it as an ogg instead of a wav... Oh well!
:D
Hope that helps. And i hope i made sense, I sometimes don't...

---

### Post by zami on 2011-01-11
> **Jamezo97 said:**
> Hmmm, have you tried going to 
'System-Administration-Login Screen'
.Then press the unlock button, and type in your password, then uncheck the "Play Login Sound" check box. That should turn off the startup sound.
I don't know whether that will work, because I have ubuntu 10.04, but it should be roughly the same...

Image here:[HERE]("http://i54.tinypic.com/2ustqn5.png")

Mind you, thats only a temporary fix...
If you have Audacity and you know where the startup sound file is, then you could open it up in audacity and turn down the sound by going to 'Effect-Amplify' and push the slider to the left about 10-20 decibels...
Ill see if i can find where that sound file is...

Thank you for the suggestions.

Yes I have tried un-checking the "play login sound"  under the Login Screen controls.  No luck!  I even tried checking it, incase the label was reversed.  No luck!

I like your idea to just squelch the sound file itself.  Brilliant!!

-zami

---

### Post by zami on 2011-01-11
That did it.  And your instructions were perfect.

It was actually dialog-question.ogg.  And I slid the amplify slider waaaay down, because my volume is FULL BLAST when I log in.

Even when I have system sounds on, they are all at whatever volume I set, but log in is always full bore crazy loud.

Well anyhow, this has made booting bearable!

Thank you, thank you, thank you!

-zami

---

### Post by Jamezo97 on 2011-01-11
No problem, glad to help.

---

