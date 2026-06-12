---
title: "3 questions"
date: 2010-04-15
forum: General Help
---

### Post by entikryst on 2010-04-15
Three problems that have been driving me crazy after I reinstalled ubuntu yesterday.  It's important I mention that I use fluxbox.

1) Gkrellm start in the upper left.  I would like it to start in the upper right. 

2) The volume is always muted on start up.  I've googled and can find a solution that works.  Here is an expample of what I've tried with no success [http://forums.linuxmint.com/viewtopic.php?f=142&t=43463](http://forums.linuxmint.com/viewtopic.php?f=142&t=43463)

3)I want to go back to using the old yellow notification alerts (someone logs into messanger or song change in rhythmbox for example)  I want to get rid of the black ones that appear in the upper right.

---

### Post by lidex on 2010-04-15
#2
[http://ubuntuforums.org/showthread.php?t=1286998]("http://ubuntuforums.org/showthread.php?t=1286998")

---

### Post by Don1500 on 2010-04-15
What version of Ubuntu?

---

### Post by ibuclaw on 2010-04-15
#3 - remove notify-osd, install notification-daemon.

---

### Post by entikryst on 2010-04-15
> **lidex said:**
> #2
[http://ubuntuforums.org/showthread.php?t=1286998]("http://ubuntuforums.org/showthread.php?t=1286998")
Unfortunately none of the advice in the suggested thread worked to resolve question #2 
I resolved question #1  by placing gkrellm in the slit and changing the slit placement to the top right and the layer to normal.

I had hoped I could take care of  Question #2 by adding the GKrellM volume plugin. The plugin only helped by remembering the last volume level but it remains muted on start up.

Thanks for the responses for question #3.  I solved the problem by following the advice here 

[http://tuxtraining.com/2009/10/26/get-the-old-notification-system-back-in-ubuntu-9-04-and-9-10](http://tuxtraining.com/2009/10/26/get-the-old-notification-system-back-in-ubuntu-9-04-and-9-10)

Was that wise should I have used install notification-daemon instead?

---

### Post by entikryst on 2010-04-17
Bump for help with question #2.

---

### Post by lidex on 2010-04-18
Revisiting #2 - have a look here:
[http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state]("http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state")

---

### Post by entikryst on 2010-04-29
Question #2 has been fixed in Lucid. :)

---

