---
title: "Howto redirect sound output from user A to user B ?"
date: 2011-04-30
forum: General Help
---

### Post by WitchCraft on 2011-04-30
Hi question:


I'm running a browser (google-chrome) as a different user.

To achieve this, I do the following:

```

$ sudo xhost +

```


Then run the command you want as the other user:
```

$ sudo -i -u <username> /opt/google/chrome/chrome

```

Then when I'm done browsing, I do:
```

$ sudo xhost -

```


Now it works fine.
The only problem is I don't get sound.

First I thought it were permission, so I tried to add the user to the audio group: 
```

$ sudo adduser <user> audio
$ sudo adduser <user> pulse
$ sudo adduser <user> pulse-access

```


But that didn't work.
Then I read somewhere that two sound daemons cannot run simultaneously. It made sense to me.


So I tried:
```

pkill pulse

```

and restarted Chrome as different user.
Now I get sound !

But of course now there is no more sound as the user I currently am logged in with, unless I restart the pulseaudio-daemon, which would in turn crash the browser.


Now the question:
Instead of doing pkill pulse, is there any way to redirect the sound output (Flash Player) from <browser user> to <current gnome user>, so I don't have to pkill the sound daemon of the current user ?

---

### Post by WitchCraft on 2011-05-07
bump.

---

### Post by WitchCraft on 2011-05-09
bump.

---

### Post by WitchCraft on 2011-05-15
bump.

---

### Post by enimeizoo on 2011-05-15
Could you have one user to stream to the other via lo or something?
I just found some streaming tools, I didn't take time to test yet, but I will update this post.

[http://www.4front-tech.com/ossapps.html](http://www.4front-tech.com/ossapps.html)

Or it seems that vlc can do the trick :
[http://n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/](http://n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/)

---

