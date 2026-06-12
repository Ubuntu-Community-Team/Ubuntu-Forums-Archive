---
title: "Diagnose a webpage on firefox"
date: 2010-06-04
forum: General Help
---

### Post by AgentZ86 on 2010-06-04
Hi

For some reason this page started coming up mostly blank

The site is [www.forexpeacearmy.com](www.forexpeacearmy.com)

Many of the tabs do not work, and produce blank pages, making the page non-functional for Firefox and Ubuntu 9.10 64 bit.

IE:
[http://www.forexpeacearmy.com/forex_news_calendar](http://www.forexpeacearmy.com/forex_news_calendar)


Most images are missing and text is missing too.

I can navigate on some of the tabs and get to the forums, but other then that the page is almost useless.

I'm on 9.10 Karmic 64 bit, with Firefox 3.59 all updates are up to date.

It seemed to work fine on install, but over time I noticed it degraded, and then now not responsive.

It's just this page too, as far as I know all other pages are working perfectly.

I tried to install the latest flash 10 from the / ubuntu software center with no effect.

Konqueror opens and works this page just fine with no problem.

It appears it's just Firefox related ?

Please advise

---

### Post by wojox on 2010-06-04
Do you have Java installed in Firefox? 

```
about:plugins
```

---

### Post by StuartN on 2010-06-04
> **AgentZ86 said:**
> For some reason this page started coming up mostly blank

It displays for me - did you try View -> Page Source to see what kind of content the page has, and Tools -> Error Console to see any errors? For serious debugging, install the Firebug plugin.

You might also need User Agent Switching for some commercial sites, to pretend to be Internet Exploder.

---

### Post by SoFl W on 2010-06-04
It didn't pass a [validation test]("http://validator.w3.org/check?uri=http%3A%2F%2Fwww.forexpeacearmy.com%2F&charset=%28detect+automatically%29&doctype=Inline&group=0") (very few websites do) site has a lot of errors.

---

### Post by AgentZ86 on 2010-06-04
> **StuartN said:**
> It displays for me - did you try View -> Page Source to see what kind of content the page has, and Tools -> Error Console to see any errors? For serious debugging, install the Firebug plugin.

You might also need User Agent Switching for some commercial sites, to pretend to be Internet Exploder.

Do all the tabs and site locations work for you ?

I can see the main page and some links in those tabs, but when I click on the tabs and locations most produce empty site pages with only some limited forexpeacearmy graphics.

I don't know why ?

I have latest Java, extras, flash etc. And also I'm not having any problems with any other sites either. Just this one.

Very strange

---

### Post by AgentZ86 on 2010-06-04
> **wojox said:**
> Do you have Java installed in Firefox? 

```
about:plugins
```

Yep all plugins installed and working perfectly to my knowledge, all other sites are working well as far as I know.

I have not experienced any problems on the web except this topic.

Not sure really how to diagnose it or make it work on firefox even with the mentioned site errors.

---

### Post by wojox on 2010-06-04
That's weird. Both links work perfect for me as well. You don't have any add-ons that would mess that up do you?

---

