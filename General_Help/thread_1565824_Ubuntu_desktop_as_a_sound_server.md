---
title: "Ubuntu desktop as a sound server"
date: 2010-09-01
forum: General Help
---

### Post by jkeane on 2010-09-01
I'm a longtime Ubuntu user, but just recently started participating in the forums. I have an ubuntu system (running the standard desktop 10.04) that I mainly use for playing music (using mpd), and watching hulu that is sitting in my living room.

What I would like is for the system to have a soundserver (pulse preferably just to stay mainstream within ubuntu) running at all times so that mpd can be played regardless of what user is logged in. 

There are a few "solutions" to this that I've found so far, all of them far from ideal (hence the scare quotes):

1. (my current setup) Have mpd connect directly to ALSA.
Pros: works (nearly) all the time.
Cons: if the system has to play a sound it will often stop mpd, play the sound, and I have to manually start mpd playing again.

2. Pulse as a systemwide daemon. (cf [http://wiki.archlinux.org/index.php/PulseAudio#System-wide_daemon]("http://wiki.archlinux.org/index.php/PulseAudio#System-wide_daemon"))
Pros: proper sound mixing.
Cons: breaks parts of Pulse. horribly insecure.

3. Create a generic user that mpd plays as and use the pulse mpd connection in mpd
Pros: proper sound mixing. fairly secure.
Cons: stops playing if I log in as anyone else. The generic user has to have access to mpd files, not the worst thing in the world but I would rather not have that. I have to ensure that this user is logged in if I want to play music.

Possible other solutions that I haven't investigated:
1. Some sort of virtual gnome session that I have pulse tied to.

2. Another sound server, although I would prefer to avoid this if possible so that my system setup is as easily configurable and replicable as possible (I tend to reconfigure this system often depending on my needs, so I would rather not have to rip apart ubuntu's sound whenever I reinstall or upgrade), but if something worked perfectly I would not rule it out.

Take home questions:
What's the best way to accomplish this? Is there a better way than my current imperfect cludge? What do other people use?

---

### Post by bobcollard on 2010-09-02
Here is a suggestion.  This system based on Ubuntu is for Media and it might serve as your basis to do what you are asking.
[http://www.elementmypc.com/main/index.php](http://www.elementmypc.com/main/index.php)

---

