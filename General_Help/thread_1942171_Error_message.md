---
title: "Error message"
date: 2012-03-17
forum: General Help
---

### Post by cowboy7305 on 2012-03-17
can any one help with this error ubuntu 10.04

---

### Post by Bucky Ball on 2012-03-17
What are you attempting to do? Upgrade to 10.04 LTS or upgrade 10.04 to a newer release?

I'm presuming you are doing a release upgrade throught the Update Manager?

---

### Post by cowboy7305 on 2012-03-17
Just doing  and every day ubdate

---

### Post by jerrrys on 2012-03-17
what happens with

sudo apt-get update

---

### Post by Bucky Ball on 2012-03-17
Well, while trying to do you everyday update a package is attempting to get upgraded, thus your error message. This message is generally connected with a release upgrade, though, so are you absolutely positive you aren't inadvertently attempting one??? 

Try jerrrys' suggestion:

```
sudo apt-get update
```... and post the output it gives when it throws an error back here. You should find some instruction when it crashes in a terminal which will help more than the GUI message; that doesn't give a lot of info. (Pleae use ```
 tags for clarity.)

If it makes the update (which from what you say it won't) then attempt:

[code]sudo apt-get upgrade
```... which updates apps and packages, NOT the release to a newer one ... post the output of any error messages back here. ;)

You might also want to have a trawl through here:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A0oGkmPNSWVPZXYAwLU36At.?ei=UTF-8&fr=altavista&p=an+unresolvable+problem+occurred+while+calculating+the+upgrade&SpellState=&fr2=sp-qrw-corr-top](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A0oGkmPNSWVPZXYAwLU36At.?ei=UTF-8&fr=altavista&p=an+unresolvable+problem+occurred+while+calculating+the+upgrade&SpellState=&fr2=sp-qrw-corr-top)

---

### Post by raja.genupula on 2012-03-18
Hi Jerry and Bucky Ball

@OP i saw something as held pkg's or something similar .
well do this along with above two posts .
```
sudo apt-get install -f
```

---

