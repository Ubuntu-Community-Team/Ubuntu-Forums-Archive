---
title: "computer bogs down after firefox is left open for a few hours"
date: 2009-07-31
forum: General Help
---

### Post by elgthg on 2009-07-31
First of all I am brand new to this forum, and I have never participated in any forums. So please be patient with me.

I installed Ubuntu on an old Dell Optiplex GX260 about 3 years ago. It is not my primary computer so I consider myself to be a green user I have it set up in my home office where I work from using a company-supplied laptop. I don't like to do anything personal on the company laptop, so that is why I wanted to have a home computer that I use to check personal email and browse the internet.

Ubuntu has just run great for all of these years until recently. I have never installed anything on it other than the regular update patches. I think I have the most current version of Ubuntu. When I click on "System - About Ubuntu" it opens a page that says, "Thank you for your interest in Ubuntu 8.04
                - the Hardy Heron - released in April 2008."
                

Anyway, recently it has developed some strange symptoms. It used to be that I could just leave it running for days and never encounter any problems. But recently I have noticed that if I open firefox and leave it open for a couple of hours the computer acts like something is totally consuming all of the cpu resources. I can't even move the mouse without the pointer freezing in place and then jumping. I try to quit firefox by clicking on the X in the top right, and that does not always work. Sometimes I have to open a terminal window and find the firefox process using ps -ef then do a kill -9. Then when I reboot the computer, the video won't load unless I power it off, power it back on, and then boot to a recover mode and run the utility that repairs x video. 

I will really appreciate it if someone can give me some advice. Maybe I just need to do a fresh install from the ground up?  Thanks in advance.

---

### Post by Vaphell on 2009-07-31
8.04 is not the latest version - ubuntu is released every 6 months so there were 8.10 and 9.04 after 8.04 (big number is the year, small number - month)

ff problems are related with flash, inefficient javascript engine and with page history taking up resources.
Flash quality in linux is adobe fault, not much to be done here.
Javascript engine is much better in FF3.5, you can try installing it
You can make FF lighter by reducing depth of tab history stack - enter about: config in URL bar and set browser.sessionhistory.max_total_viewers to 0
Also installing Adblock to cut amount of ads shown on screen makes pages less heavy. Flash animations and tons of unnecessary javascripts add to the CPU load.

---

### Post by lovinglinux on 2009-07-31
[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

