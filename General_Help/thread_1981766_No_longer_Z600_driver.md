---
title: "No longer Z600 driver?"
date: 2012-05-17
forum: General Help
---

### Post by Q-collective on 2012-05-17
I've grown used to manually installing support for my Lexmark Z600. I've always followed some tutorial and usually installed it in less than 10 minutes.

Now however, Lexmark seems to have pulled their drivers from the website. What the hell?

Doesanyone still have the Z600 drivers or have an alternate location, so I can still use my printer?

Lexmark, what a worthless company.

---

### Post by Q-collective on 2012-05-17
Ok, after a little more searching, I've found [this driver](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.2.deb) to be helpful.

Just install it via the terminal command:
```
sudo dpkg -i lexmark.z600-0.2.deb
```

Then plug in your printer and it'll be automatically configured for you.
This was tested for Kubuntu 12.04

Hope it helps :)

---

### Post by Geezanansa on 2012-05-29
Following this guide
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)
and using the lexmark driver CJLZ 600 LE -CUPS-1.0-1.TAR.gz from here [http://support.lexmark.com/index?page=answers&startover=y&locale=en&userlocale=EN_US&question=CJLZ600LE#1](http://support.lexmark.com/index?page=answers&startover=y&locale=en&userlocale=EN_US&question=CJLZ600LE#1)
May give you answer to question.
Have used this method of getting old lemark x1270 working on older flavours but not got this working in 12.04 yet as backend end not mounting/error so driver installed but printer can not speak to pc allthough it is being detected.
What flavour you on Q-collective?



[]("http://ubuntuforums.org/showthread.php?t=49714")

---

