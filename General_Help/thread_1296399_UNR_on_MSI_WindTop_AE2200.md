---
title: "UNR on MSI WindTop AE2200"
date: 2009-10-20
forum: General Help
---

### Post by siblog on 2009-10-20
I just recently purchased a MSI WindTop AE2200 and am curious if others have successfully gotten Ubuntu Netbook Remix (9.04/9.10) + touchscreen working on it? I have seen other forum posts on getting UNR installed on the MSI WindTop AE1900 but that model has completely different processor, graphics card and other hardware specs from this model.

I imagine I will give it a go either way just thought I would see if others have already done it

Specs - [http://us.msi.com/index.php?func=newsdesc&news_no=846]("http://us.msi.com/index.php?func=newsdesc&news_no=846")

thnx,

-Simon

---

### Post by siblog on 2009-10-23
bump

---

### Post by GREZZO16 on 2009-11-01
hi
i have the Ae1900 as my signature says, and i've installed UNR9.10 on it: only 2 devices hasn't been worked "out of the box".

You can find the solution here:
[http://forum-en.msi.com/index.php?topic=128477.0](http://forum-en.msi.com/index.php?topic=128477.0)

byeee

---

### Post by siblog on 2009-11-02
Thanks. I will have to give it a shot, I am just a little wary since the processor and other hardware are very different from the AE1900

Thanks

---

### Post by siblog on 2009-12-29
Update:
I ended up deciding to go with Linux Mint 8 64-bit which is Ubuntu 9.10 based. I used the instructions above (kinda) to get touchscreen running. Here is what I did - 

```

sudo aptitude update;
sudo aptitude upgrade -y;
sudo aptitude install xserver-xorg-input-evtouch -y;

```

From there I launched the evtouch touchscreen calibration tool. Once I calibrated, I restarted and the touchscreen worked perfectly.

As for the microphone this solution did not work for me and am trying other possibilities

---

