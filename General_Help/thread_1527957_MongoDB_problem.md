---
title: "MongoDB problem?"
date: 2010-07-10
forum: General Help
---

### Post by Ncage1974 on 2010-07-10
Guys first let me say i'm definitely a novice when it comes to linux. I'have dabbled with a lot o different distros but i'm not a guru by any means. That being said.l I just installed ubuntu for using Ruby on Rails/MongoDB/& VIM. Well install of everything went smoothly, at least so far, except for MongoDB.  Installed it through the ubuntu software cent and it seems to install just fine but when i go to the terminal to use it and just type "mongod" i get the following error:
mongod: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory.

It took me a while to find a solution but i finally found one after googling here:
[http://www.crashcourse.ca/content/getting-started-mongodb-under-ubuntu](http://www.crashcourse.ca/content/getting-started-mongodb-under-ubuntu)


First thing is i'm suprised that MongoDB is not working from the default packages. I thought those were tested pretty thoroughly. Most of the people who i found were having the problem had the problem back in 9.1 which seems like its been a problem for awhile. 

Second, in the solution i found above can anyone explain to me what exactly what i did? I absolutely hate not knowing what i'm doing and i don't :). Is anything i did going to make things more difficult for me in the future: less secure, harder to upgrade, ect...? I already noticed the version of MongoDB is a pre-production version which i'm ok with just as long as i don't run into anything major of course id prefer to go with the production version of course but what can you do when you can't get the production version to work.

thanks in advance,
Ncage

P.S. This is Ubuntu x64 10.04

---

### Post by kristina-dev on 2010-07-11
MongoDB uses libmozjs.so for its javascript engine, and the package that comes in is a mess (xulrunner). The best way of installing the MongoDB package on Ubuntu is to follow these instructions: [http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages](http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages).

---

### Post by Ncage1974 on 2010-07-13
> **kristina-dev said:**
> MongoDB uses libmozjs.so for its javascript engine, and the package that comes in is a mess (xulrunner). The best way of installing the MongoDB package on Ubuntu is to follow these instructions: [http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages](http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages).

Kristina thank you so much for the help. There wasn't a lot of info available. I guess i will just remove current MongoDB & use the instructions from the link you posted. Trying to see what all the hype is about the NoSQL movement ;).

---

