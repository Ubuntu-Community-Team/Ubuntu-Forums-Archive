---
title: "Belinea CRT 106055 Resolution sharp picture"
date: 2012-07-13
forum: General Help
---

### Post by i argor on 2012-07-13
Hello,

i have hooked up an older 19 inch Belinea 106055 onto my laptop... like this screen, it is big and has good color... but... :)

The screen can handle a resolution up to 1600. I would like to use 1280 resolution. The problem is that the letters look not sharp in higher resolution. i hope you know what i mean. i have tried different moire settings without success. Ubuntu recognizes the screen as an RogenTech 17 inch.

my question is how to adjust the monitor via Software so the picture gets more sharp and also is it okay that or does it affect the picture when ubuntu uses the RogenTech 17 inch driver, how can i change it

I currently use 1024 at 100 Hz which gives me the best picture, but i would prefer 1280 resolution because i use some applications where a bigger screen is better

Thank you for any answer

regards

):P

---

### Post by Kopkins on 2012-07-13
Have you tried using the system settings?

In system settings > Displays

you can adjust a few of the monitor settings. 

As for the the blurry or 'not sharp' letters, I'm assuming you mean text.

You can adjust the font hinting a couple of ways. I would recommend using ubuntu tweak, as it is a very useful tool. To install it,
```
sudo add-apt-repository ppa:tualatrix/ppa

sudo apt-get update

sudo apt-get install ubuntu-tweak

```

Once installed, open ubuntu tweak and navigate to the tweaks page. There will be four menu buttons along to top, click on tweaks. The first option here should be 'Fonts'. Click on 'Fonts' to open the tweaks for fonts. From here you can edit all of the system fonts as well as change the anti-aliasing and hinting. I would recommend fiddling around with the hinting and anti-aliasing until you find setting you are happy with. 

Best of luck,
Kopkins

---

### Post by i argor on 2012-07-13
thanks...

i have tried the ubuntu tweak, it is nice and might help. but in my case i think the crt monitor is just not good at higher resolutions :)

---

