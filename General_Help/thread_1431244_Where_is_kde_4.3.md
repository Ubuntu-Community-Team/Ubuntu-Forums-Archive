---
title: "Where is kde 4.3"
date: 2010-03-16
forum: General Help
---

### Post by gawadelnil2002 on 2010-03-16
I don' know what to say or how to say , I like jaunty more than karmic and I installed it (jaunty)  today as base system from boot only cd.
 
and i wanted to install kde 4.3 from kubuntu backports but there is no jaunty packages in kubuntu backports for any kind of kde  software
And I looked at the supressed packages I found that jaunty packages all have been supressed.
so what ?
I just i tried to act inetlligent and take the karmic repository form kubuntu backpors and replace the word karmic by jaunty .
but it didn't work when i typed  sudo apt-get install kubuntu-desktop it just started to download kde 4.2.x from jaunty updates repository.
 
 I searched kubuntu news I dont see any thing says that kubuntu team stopped the kde 4.3 repository for jaunty
 
something else is confusing I still can download the supressed packges for kde 4.3 form kubuntu packports and it ends with the word jaunty so its there but supressed
 
is there some commans, orders or trick let me force apt-get to download packages from there after supressing it
 
and really I need to know what I have to do.

---

### Post by gawadelnil2002 on 2010-03-18
I think I asked vert silly question so People dosn't want to replay :)

---

### Post by wojox on 2010-03-18
You did this:

```

sudo sh -c "echo 'deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main' >> /etc/apt/sources.list"

```

```

sudo sh -c "echo 'deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main' >> /etc/apt/sources.list"

```

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A

```

```

sudo aptitude update && sudo aptitude dist-upgrade

```

---

