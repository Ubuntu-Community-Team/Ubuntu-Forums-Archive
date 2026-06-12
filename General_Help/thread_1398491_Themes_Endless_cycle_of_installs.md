---
title: "Themes: Endless cycle of installs"
date: 2010-02-04
forum: General Help
---

### Post by eraevous on 2010-02-04
Okay, I've been trying to install new themes for Ubuntu on my laptop and another person's laptop. When I go to try and install these new themes, I inevitably get some sort of "you're missing blahblahblah" messages. The problem comes when I track down whatever I'm missing and try to install *that*. I get another error telling me I'm missing something else! This keeps happening no matter how many hoops I jump through. Are there packages that I can simply apt-get, or is this seriously "turtles all the way down"? I'm okay with following the instructions to make this or ./configure that, but the other person will NOT be happy doing those sorts of things. She's a windows user who does not have time to learn all sorts of new stuff just to have the same functionality that she can get on her windows 7 partition. Any help would be wonderful!

---

### Post by junapp on 2010-02-04
where are you getting your themes? I thought you should be able to drag them onto the theme window and all was installed for you.

---

### Post by VCoolio on 2010-02-04
Unless you're missing the engine for these themes, don't worry about it. If you'r e missing the engine, try 'apt-get install gtk2-engines-missingenginehere'. If it complains about icons or others stuff just check if it looks ok; most of the time these are just tips from the theme author to complement the theme with stuff that looks good with it. If you want to get rid of the error anyway, edit the themes index.theme file and delete the lines containing the hints.

---

