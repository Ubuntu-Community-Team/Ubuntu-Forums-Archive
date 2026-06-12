---
title: "My bass has just disapeared on ubuntu"
date: 2009-09-16
forum: General Help
---

### Post by Psyphre on 2009-09-16
Hi,

Ive just realised my bass has dissapeared in ubuntu. I have no idea why. For a while I've felt something was lacking with my sound, at first i thought it was my speakers breaking, but i just played music on my ps3 through the same speakers and it sounds perfect, with a nice deep bass.

When i checked ubuntu again, it was devoid of any deep bass. 2 months ago i know both my pc and my ps3 had the same level of bass as i used both through the same speakers, so something since has changed (an update maybe??).

I've messed around with alsamixer but the bass slider does nothing.

Any suggestions?
Thanks.

---

### Post by gettinoriginal on 2009-09-16
You might try [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+sound+9.04&sa=Search&cof=FORID:9#941")

---

### Post by Psyphre on 2009-09-16
> **gettinoriginal said:**
> You might try [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+sound+9.04&sa=Search&cof=FORID:9#941")

Thanks for the reply, but i think you misunderstood me. Sound works fine, its just the bass whcih doesnt. You link takes me to solutions for those without any sound.

---

### Post by gettinoriginal on 2009-09-16
I did a search under googlubuntu "bass slider does not work in 9.04" and got varying solutions, most by sound card.  You might want to try that.

---

### Post by Psyphre on 2009-09-16
> **gettinoriginal said:**
> I did a search under googlubuntu "bass slider does not work in 9.04" and got varying solutions, most by sound card.  You might want to try that.

Thanks for the prompt replies. I dont know if I'm being stupid but i searched for "bass slider does not work in 9.04" in your link and still didnt get anything :confused: . At the top of the list was this thread lol.

---

### Post by whitethorn on 2009-09-16
Are you using pulse audio and do you have a seperate base?  Then you probably need to uncomment a setting in /etc/pulse.

```
sudo vim /etc/pulse/daemon.conf
```

What you're looking for is a line with
>  ; disable-lfe-remixing = yes

and change it to

> disable-lfd-remixing = no   reboot and enjoy bass.

---

### Post by Psyphre on 2009-09-16
> **whitethorn said:**
> Are you using pulse audio and do you have a seperate base?  Then you probably need to uncomment a setting in /etc/pulse.

```
sudo vim /etc/pulse/daemon.conf
```

What you're looking for is a line with


and change it to

  reboot and enjoy bass.

actually I'm not. I'm using Alsa. I've been wondering if me disabling pulse caused the issue, but i did that months ago and I'm sure I would have noticed this earlier if that were the case.

What do you mean by seperate bass?

---

### Post by whitethorn on 2009-09-17
I have a surround sound system with a seperate bass box.  Pulse was disabling sound being sent to it (stereo sound) unless it was 6 channel sound.  Hmmm in that case I don't know what could be wrong.

---

### Post by Psyphre on 2009-09-17
ye its pretty wierd, i dont get whats going on either.

---

