---
title: "Delete forever the Login Drum sounds?"
date: 2012-01-17
forum: General Help
---

### Post by PDA1 on 2012-01-17
I want to delete forever the Login "jungle drum" sound file.  

That's what I want to do.  No, I don't want to do anything other than that.  I'm sick of hearing that racket when I boot up.  The login screen check box, unchecked, has no effect.


But I have no idea where the file is or what it's name is.

Do you know?

---

### Post by bluexrider on 2012-01-17
under 'startup applications' un-tick the gnome logon sounds and under the 'logon screen settings' un-tick the 'Play logon sound'

---

### Post by cbanakis on 2012-01-17
hmm...

if you manage to delete it as sudo, updates will probably put it back from time to time.

I would suggest replacing it with a blank sound clip.

That way, Ubuntu sees the file, plays it at login, and will never know the difference.

You would have to replace the file from terminal as root.

Not sure where the file is located though.

---

### Post by MG&amp;TL on 2012-01-17
I wouldn't recommend deleting it-if for instance, in pseudo code, your login manager's code looks like this:

```

blah...
playloginsound(loginsound.ogg)
blah...

```

the program would freeze.

Instead, make a silent one-second recording, or a piece of music more to your taste, then move it as described [here]("http://linux-software-news-tutorials.blogspot.com/2011/12/change-startup-sound-in-ubuntu.html"). 

I find it a little odd that unchecking the box does not work in startup applications; would you mind filing a bug?

---

### Post by ubudog on 2012-01-17
I believe the sound is at /usr/share/sounds/ubuntu/stereo/desktop-login.ogg

What you can do, as suggested before, is make a blank sound clip.  To accomplish this, open Sound Recorder, click record, then immediately click the stop button.  Save the file as an ogg onto your Desktop.  Open a terminal, and do this:
```
sudo cp /usr/share/sounds/ubuntu/stereo/desktop-login.ogg ~/desktoploginbak.ogg; sudo cp Desktop/savedfile.ogg /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```
Note: Replace 'savedfile.ogg' with the file you saved on the desktop. 

Hope that helps,
- ubudog

---

### Post by PDA1 on 2012-01-17
Ugh.

Figured it out.

The file's name was something like "loginsound.ogg" was located in something like...

/usr/share/sounds/blah....blah....blah

I deleted the file and the problem is GONE FOREVER!!!!!!

---

### Post by ubudog on 2012-01-17
:D Glad you figured it out.

---

### Post by jonobr on 2012-01-17
Looking forward to your next thread
> 
"I deleted the drums, and I miss them. How do I get them back"
;)

---

### Post by KdotJ on 2012-01-17
> **jonobr said:**
> Looking forward to your next thread

;)

Lol the OP seems to hate it a large amount... which I agree with Haha

---

