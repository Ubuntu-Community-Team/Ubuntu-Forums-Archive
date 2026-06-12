---
title: "play sound on computer over ssh"
date: 2009-08-01
forum: General Help
---

### Post by topgun_tapan on 2009-08-01
I have music on my computer at my room. When I go to my lab I would like to listen to the music I have on my computer or watch videos over the network. When I ssh -XY , I can watch the videos but can't hear the audio (using mplayer). I tried using mplayer and xmms2 for audio, but still couldn't get the audio. Can anyone help me out with this ?

---

### Post by jocampo on 2009-08-01
> **topgun_tapan said:**
> I have music on my computer at my room. When I go to my lab I would like to listen to the music I have on my computer or watch videos over the network. When I ssh -XY , I can watch the videos but can't hear the audio (using mplayer). I tried using mplayer and xmms2 for audio, but still couldn't get the audio. Can anyone help me out with this ?

SSH does X11 forwarding, but doesn't handle sound at all but I think there are workarounds; you can try mplplayer, for instance.

```
sudo aptitude install mplayer
```

then

```
ssh user@yourhomepc "cat file" | mplayer -
```

This is a useful link, take a look: [http://www.go2linux.org/mplayer-command-line-music-video-player]("http://www.go2linux.org/mplayer-command-line-music-video-player") but I would not use ssh for playing music. I mean, it was not intended for such activity but for running console and commands remotely.

---

### Post by hyperAura on 2009-08-01
i didnt know that only the video is being transferred without audio.. the truth is that ive never tried it.. i will definitely try it..

---

