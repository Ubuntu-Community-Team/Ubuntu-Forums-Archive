---
title: "[sound] Suddenly stopped working"
date: 2010-09-03
forum: General Help
---

### Post by micha8l on 2010-09-03
Hello, I'm very new to Ubuntu and I'm using the latest stable version. Yesterday I had my sound working, but today my sound has stopped working.

I've taken the following steps without success:

System -> Administrator -> Hardware Devices (finds nothing)
```

sudo apt update
sudo apt-get update

```

When I run the following command in shell:

```

alsamixer

```
It says the command isn't found.

When I run this command:
```

alsaconf

```

It says it couldn't detect a sound card.

Any help at all would be appreciated!

Regards

---

### Post by micha8l on 2010-09-03
Still haven't solved this, but I've found that my hardware is plugged in right: 

And I found some statistics on my systems sound:
[http://www.alsa-project.org/db/?f=af661bff5408d7e522b2816d733c65db3dc2c156](http://www.alsa-project.org/db/?f=af661bff5408d7e522b2816d733c65db3dc2c156)

Please help :)

---

### Post by micha8l on 2010-09-03
I don't know exactly what I did for my sound to stopped working, but I noticed that before my sound 'went' I was having some trouble with sound on flash videos.

Anyway, I got it working again by following this tutorial, apparently some program had over-written sound preferences without my knowledge.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

To revert to default sound preferences I used the following command:

```

 sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2.

```

Hope this can help somebody else,

Kind Regards
Mike

---

### Post by dodo3773 on 2010-09-03
Thank you very much. I had this exact problem today when I got home.

---

