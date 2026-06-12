---
title: "XMMS installation problems, newbie need help"
date: 2005-02-19
forum: General Help
---

### Post by napalm_death on 2005-02-19
Hello there. Im having problem installing XMMS from ubuntu repository so i resort in downloading the installer from the net.

so here's the situation:
i went to this site: [http://www.xmms.org/download.php](http://www.xmms.org/download.php)

these are the requirements: (do ubuntu have this by default?)
# ALSA output: ALSA 0.9.0 or better.
# Esound output: esound 0.2.8 or better.
# Mikmod input: libmikmod 3.1.10
# Ogg Vorbis input: libvorbis
# OpenGL Visual plugin: Mesa 3.0 or better.

and downloaded the debian installer  here: [http://packages.debian.org/unstable/sound/xmms.html](http://packages.debian.org/unstable/sound/xmms.html)

then installed it using and there are some error messages that I dont have yet.

can I use the .rpm installer of the xmms here at ubuntu?

does installing in ubuntu much more tedious than installing in windows environment?

how do i effectively install programs in ubuntu? many thanks

---

### Post by Perfect Storm on 2005-02-19
You can check your Synaptic package Management if those files are installed. 

Try post which error you get while installing the .deb files

You could try the .rpm file but it's no guarentee that it work:

```

sudo alien <filename>.rpm
sudo dpkg -i <filename>.deb

```

Also what's wrong with your repository?

---

### Post by napalm_death on 2005-02-19
[QUOTE=Artificial Intelligence]You can check your Synaptic package Management if those files are installed. 

Try post which error you get while installing the .deb files

You could try the .rpm file but it's no guarentee that it work:

```

sudo alien <filename>.rpm
sudo dpkg -i <filename>.deb

```

Also what's wrong with your repository?[/QUOTE]
 thanks for the reply. do i need to connect to the internet before installing from the repository?
 
i followed the instructions here [http://ubuntuguide.org/](http://ubuntuguide.org/) but still i cant install using apt-get from the repository. do i have to reinstall ubuntu? thanks again.

---

### Post by kassetra on 2005-02-19
napalm: yes, the repositories are all online, so if your ubuntu computer is not connected online when you are trying to retrieve and install applications/files, you will not be able to get them.
 
 Here is some information on installing xmms in ubuntu:
 [Unofficial Ubuntu Starter Guide]("http://ubuntuguide.org/#xmms")

---

### Post by napalm_death on 2005-02-19
[QUOTE=kassetra]napalm: yes, the repositories are all online, so if your ubuntu computer is not connected online when you are trying to retrieve and install applications/files, you will not be able to get them.
 
 Here is some information on installing xmms in ubuntu:
 [Unofficial Ubuntu Starter Guide]("http://ubuntuguide.org/#xmms")[/QUOTE]
 thanks. i hope ubuntu will be friendly to me. :) thanks

---

### Post by kassetra on 2005-02-19
That's how I installed xmms, and it worked just fine.  :)
 
 However, if you want a media player that looks and acts like xmms but is updated to work better with your ubuntu system, I suggest looking at [beep-media-player]("http://www.gnomefiles.org/app.php?soft_id=122").

---

