---
title: "Good calculator programs?"
date: 2011-12-24
forum: General Help
---

### Post by linuxuser12345 on 2011-12-24
Are there any good, simple calculator programs that mimic one that would be used in an office where everything is recorded to calculator tape or paper, but instead save it to a file?

---

### Post by kurt18947 on 2011-12-24
I've wondered the same thing so I'll be watching this thread.  I suspect the availability of good no-cost spreadsheet programs limits the appeal of developing such calculator apps.  Here's one that might be interesting:
[http://www.mariottini.net/roberto/superbcalc/](http://www.mariottini.net/roberto/superbcalc/)

---

### Post by Lars Noodén on 2011-12-24
speedcrunch has the ability to save output to a file

Alternately if you are using one of the text based calculators like bc, you could use [tee](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tee.1.html) to save the output.
```

bc | tee /home/linuxuser12345/output.txt

```

---

### Post by utnubuuser on 2012-03-14
Qalculate will save to file as well, and it features graphical fraction output...[http://sazeit.com/articles/qalculate-put-a-better-calculator-on-your-desktop]("http://sazeit.com/articles/qalculate-put-a-better-calculator-on-your-desktop")

---

### Post by troymius on 2012-03-14
linuxuser12345... I am not sure about doing this because it will look like dirty marketing but I have a little website with a calculator called [calculatorpi.com]("http://calculatorpi.com"). It does show earlier calculations for reuse. A sequence of calculations can be printed or saved as a bookmark. I made it first for myself because I needed such feature and thought that making it a website is actually more convenient because I don't have to install it on every machine I work with.

Later I made it a "business". It is really just for fun. It's not making any money, quite the opposite :-) I just feel really happy when I see a handful of people using it every day. 

If the forum administrator deletes this posting, that's ok. I am not trying to sell anything, just help.

Let me know if/how it works for you. Thanks.

---

### Post by Habitual on 2012-03-14
```
sudo apt-get install speedcrunch
```

has a tape...

---

