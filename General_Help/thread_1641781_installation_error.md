---
title: "installation error"
date: 2010-12-09
forum: General Help
---

### Post by ExOH on 2010-12-09
I have upgraded to ubuntu 10.10 from 10.4 and once i did so i tried to re-install some of the games and programs i had from the software centre, but as i did so my computer froze in the middle of an install, i keep getting the messege "There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry." and i am unsure how to fix it or what to do now

---

### Post by sikander3786 on 2010-12-09
Welcome to the forums :-)

Go to Applications > Accessories > Terminal and post the output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

