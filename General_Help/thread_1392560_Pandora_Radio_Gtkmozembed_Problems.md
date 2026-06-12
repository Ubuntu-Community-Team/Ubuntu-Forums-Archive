---
title: "Pandora Radio Gtkmozembed Problems"
date: 2010-01-28
forum: General Help
---

### Post by Cunnilingus on 2010-01-28
When I try to add the Pandora Radio applet to my dock in AWN I get this error message:
The following Python modules could not be found: gtkmozembed.
Pandora works just fine in Firefox. The applet is the only thing that is giving me trouble..

Just wondering, do you need a certain amount of posts to have an avatar?

---

### Post by Cunnilingus on 2010-01-28
I got it working, all I did was run this command in terminal:
```
sudo apt-get install python-gtkmozembed
```
Problem solved.

---

