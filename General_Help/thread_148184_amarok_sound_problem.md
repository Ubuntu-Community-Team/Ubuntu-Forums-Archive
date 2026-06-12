---
title: "amarok sound problem"
date: 2006-03-21
forum: General Help
---

### Post by ozkan on 2006-03-21
i  installed amarok but i have a problem when it plays a song the sound is not pure i hear  creaking noises with the music . I think that there is a problem with my sound card but Rythmbox music player plays same songs without problem
any  help ?

---

### Post by Gallows on 2006-03-21
Ozkan

Open Amarok, select Settings / Configure Amarok / Engine.  Check to see what engine you have configured Amarok to use.  As I understand it there are multiple engines you can use and you *may* not have the engine correctly installed or configured.

Use Synaptic to see if you have either the aRts or the gstreamer sound engines installed.  If you are missing one, or are able to update it, install it and use Settings / Configure Amarok / Engine to configure Amrok to use the new engine.

Have a look at the [Amarok Wiki site]("http://amarok.kde.org/amarokwiki/index.php/Audio_Engine_Comparison") for a nice article on engine comparison and [here]("http://amarok.kde.org/amarokwiki/index.php/FAQ") for the FAQ.

Hope this helps...

---

### Post by ozkan on 2006-03-21
yeah  thank you i uppdated my gstreamer but i think the problem was at outputplugin : it was ossssink by default but i changed it to alsasink and it's better now thank you ...

---

