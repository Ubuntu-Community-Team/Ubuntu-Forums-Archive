---
title: "how to install tbird without apt-get"
date: 2006-03-10
forum: General Help
---

### Post by jeisma on 2006-03-10
hello!

(while looking and hoping for a solution to my apt-get problem, i downloaded tbird 1.5.)

when running ./thunderbird, i get this:

./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

what does this mean? how can i run tbird?


thank you!

---

### Post by dmizer on 2006-03-10
just use this wiki: [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28install%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28install%29)

and replace where it says firefox with thunderbird.

unfortunately, it appears that you'll need to install the libstdc++.so.5 before you can work thunderbird.  not too sure how to tell you to get that installed without apt-get.

---

### Post by Sutekh on 2006-03-10
Did you download thunderbird from mozilla's website?

Installing thunderbird will be a  little more involved this way (not using apt-get)

apt-get is so nice becuse it handles dependant packages for you.

Without apt-get you will have to resolve these yourself and as they appear.

So libstdc++  fortunately is on the installation CD,  meaning you can install it with apt-get/Synaptic.  But I'm not sure it's the right version.

---

### Post by aysiu on 2006-03-10
There's a page dedicated to Thunderbird:
[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

---

