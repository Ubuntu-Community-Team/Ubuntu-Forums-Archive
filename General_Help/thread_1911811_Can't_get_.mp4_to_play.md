---
title: "Can't get *.mp4 to play"
date: 2012-01-19
forum: General Help
---

### Post by JCM_Pico on 2012-01-19
Hello world !!!

I'm having some trouble to make my system read or encode .mp4 video files....

1 - I've some videos recorded in this format and I can't open them with Ubuntu movie player... I tried to open them with xine and it plays fine, except I've n sound...

2 - I've installed kdenlive to edit some videos... and I found that I can not render any project to H.264, xvid or mpeg4... Apparently there are some library's missing  :confused:

So I've came to the forum and searched for a workaround this problem... That's were I found --> [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
But it sank it to the swamp... (it didn't worked)....

Can anybody give me some advise on this... (using Ubuntu 10.04 :D)

---

### Post by kc1di on 2012-01-19
Install ubuntu-restricted-extras and ubuntu-restricted-addons

you can find them in synaptic 

or simply enter the following in a terminal it should then work.

```
sudo apt-get install ubuntu-restricted-extras ubuntu-restricted-addons
```

---

### Post by Dreamer Fithp Apprentice on 2012-01-19
If the above isn't enough to get all the functions you need google "medibuntu". It is a repository with codecs and such that are encumbered with licenses and so on.

---

### Post by JCM_Pico on 2012-01-20
> **kc1di said:**
> Install ubuntu-restricted-extras and ubuntu-restricted-addons

you can find them in synaptic 

or simply enter the following in a terminal it should then work.

```
sudo apt-get install ubuntu-restricted-extras ubuntu-restricted-addons
```


Ubuntu doesn't find ubuntu-restricted-addons

```
ubuntu-restricted-extras is already the newest version.
E: Couldn't find package ubuntu-restricted-addons

```


:(

---

### Post by JCM_Pico on 2012-01-20
> **Dreamer Fithp Apprentice said:**
> If the above isn't enough to get all the functions you need google "medibuntu". It is a repository with codecs and such that are encumbered with licenses and so on.

I'm considering this solution... but I just want to read and render *.mp4.... isn't installing medibuntu going to download too much unnecessary data to my system?

---

### Post by kc1di on 2012-01-20
Which Version of Ubuntu are you using?

Do you have synaptic install?

if not install it ```
sudo apt-get install synaptic
```
then refresh the repositories and search for ubuntu-restricted.

The restricted codecs work here and play .mp4 format fine Using Ubuntu 11:10 But it work with 10:04 and 10:10 also for me. 

I would also in stall VLC and give that a try. 

good Luck ,
Dave

---

### Post by pretty_whistle on 2012-01-20
I have Totem movie player and Gnome MPlayer both of which play my mp4's fine.

Probably easier to just switch to one or both of these.

---

### Post by JCM_Pico on 2012-01-21
> **kc1di said:**
> Which Version of Ubuntu are you using?

Do you have synaptic install?

if not install it ```
sudo apt-get install synaptic
```then refresh the repositories and search for ubuntu-restricted.

The restricted codecs work here and play .mp4 format fine Using Ubuntu 11:10 But it work with 10:04 and 10:10 also for me. 

I would also in stall VLC and give that a try. 

good Luck ,
Dave

Yes I have synaptic....
Xine plays the video but not the sound... VLC the same thing... its a codec problem not player problem....

I'm not being able to install the codecs.... does anybody can help with this?

---

### Post by holycow131415 on 2012-01-21
[LEFT]Install VLC player, it plays everything out of the box.
[/LEFT]

---

### Post by JCM_Pico on 2012-01-21
> **holycow131415 said:**
> [LEFT]Install VLC player, it plays everything out of the box.
[/LEFT]


This doesn't solve the render problem ...

---

### Post by JCM_Pico on 2012-01-22
Render problem solved after following the tutorial and then re-runing the KdenLive configuration wizard....

For the plaing the files... the only workaround that I found is not to use Movie Player.... I'm using Xine for this format (VLC will do =) )

---

### Post by sudodus on 2012-01-22
Try to do what is suggested in the following thread. It usually helps to get the multimedia programs work.
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=766683_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by kc1di on 2012-01-24
Glad you found the answer. 
:)

---

