---
title: "how do i run 2 seperate versions of firefox?"
date: 2010-03-03
forum: General Help
---

### Post by eival on 2010-03-03
i have the pre-insalled system managed version 3.18 but im trying to isntall/run a newer version but they open as 3.18.

ive tried installing Firefox 2 thru synaptic and the newest 3.6 from firefox.com both open as 3.18

is there some config file i have to change or something?

im using 8.04

---

### Post by Enigmapond on 2010-03-03
My suggestion and someone may have a better one but this worked for me. Go and delete everything firefox in synaptic except any plugins or such. Then search the root directory and delete all evidence and other instances there. look in /bin, /opt, /ect and /usr for strays. Then install the 3.6 again. This 'should' work as it did for me....good luck.

---

### Post by eival on 2010-03-04
i dont want to delete the original version, i want to have 2 different versions installed and running side by side at the same time.

i know i was able to do it back when 3.5 was in beta mode but dont remember what i did.

---

### Post by Vaphell on 2010-03-04
in terminal write firefox and press tab twice, it will show you all legit commands starting with firefox (autocompletion feature)
probably they will be called firefox-2.0, firefox-3.0, firefox-3.6 or whatever.

create a launcher with a proper path, it will run your 'other' firefox version

---

### Post by eival on 2010-03-04
i wound up just installing the windows version thru WINE

thanks for your help tho

---

