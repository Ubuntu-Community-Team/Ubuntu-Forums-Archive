---
title: "Help installing Divx Player"
date: 2010-04-21
forum: General Help
---

### Post by Sao Paulo on 2010-04-21
I'm on a website that streams divx programmes and so need the divx player from [here]("http://labs.divx.com/DivXLinuxCodec").

The problem is I'm new to Linux and can't install the ruddy thing so wondered if someone can talk me through it here in simple terms?

---

### Post by klemes on 2010-04-21
I do not think you need this in particular in Linux.
Just install kubuntu-restricted-extras and you are all set with every possible codec you need.
Also activate the medibuntu repository(I think but I am not sure if it is automatically activated once you install the above package) and install the w32codecs like this.

```
sudo apt-get install kubuntu-restricted-extras w32codecs libdvdcss2 vlc
```I think this should be enough.If you get an error telling you that some packet is not installed go to [www.medibuntu.org]("http://www.medibuntu.org") and follow the instruction on how to install the above repository.Also not that vlc streams network streams including divX I suppose so it could prove handy to you.

If by any chance you need only this particular decoder that you mentioned from the website tell us and we 'll think of something.

---

### Post by Sao Paulo on 2010-04-21
Thanks klemes but I get the message "Couldn't find package w32codeecs"

I did look at that website but it didn't help :(

---

### Post by 3rdalbum on 2010-04-21
> **Sao Paulo said:**
> Thanks klemes but I get the message "Couldn't find package w32codeecs"

I did look at that website but it didn't help :(

You need to use the "Repository HOWTO" link on the Medibuntu website before you can install the "w32codecs" or "w64codecs" packages. Also, the Medibuntu repository is down at the moment... hopefully will be back tomorrow.

The 'kubuntu-restricted-extras' package should be enough to get DivX and Xvid videos to play. Hit Alt-F2 and type this:

```
apt:kubuntu-restricted-extras
```

Also note that the person advising you earlier made a typo; it's w32codecs, not w32codeecs.

---

### Post by klemes on 2010-04-21
The above post answered your question.Ehm,,,sorry for the typo....:)

By the way if you have an older Ubuntu version the above command will not work on your system:

simply type at the console prompt:

sudo apt-get install kubuntu-restricted-extras vlc

like the above user said it is all you need for the moment.(also I added vlc because of it's newtwork streaming capabilities)

---

### Post by Sao Paulo on 2010-04-21
> **klemes said:**
> The above post answered your question.Ehm,,,sorry for the typo....:)

By the way if you have an older Ubuntu version the above command will not work on your system:

simply type at the console prompt:

sudo apt-get install kubuntu-restricted-extras vlc

like the above user said it is all you need for the moment.(also I added vlc because of it's newtwork streaming capabilities)

Tried that and although it installed I still can't get things to work on this site -

[http://veehd.com/](http://veehd.com/)

On Windows all I did was install the divx player

---

### Post by klemes on 2010-04-21
If all you want is to play streaming video from the above site try:

```
sudo apt-get remove totem-mozilla
```

and

```
sudo apt-get install mplayer mozilla-mplayer
```

and restart your browser after it completes.

I have no means to try it myself right now but mplayer mozilla plugin will play almost anything windows will play(except maybe some drm stuff restricted artificially to windows players)

---

### Post by Sao Paulo on 2010-04-21
Thats it working now,thanks for the help :)

---

