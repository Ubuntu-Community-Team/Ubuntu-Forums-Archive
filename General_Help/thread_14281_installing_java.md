---
title: "installing java"
date: 2005-02-06
forum: General Help
---

### Post by audiored on 2005-02-06
I've searched through the forums to learn how to install java.

this is the procedure i followed:

sudo chmod a+x jre-1_5_0_01-linux-i586.bin
./jre-1_5_0_01-linux-i586.bin
sudo mv jre-1.5.0_01/usr/local/
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /user/local/jre1.5.0_01/plugin/i386/ns7-gcc29/libjavaplugin_oji.so libjavaplugin_oji.so libjavaplugin_oji.so

and i've installed the shortcut plugin from both ns7-gcc29 and ns7 folders and i've installed it in /usr/lib/mozilla/plugins as well
nothing seems to work. i still can't get java to work in firefox.

what am i doing wrong?

thanks,
jason

---

### Post by Kimimaro on 2005-02-06
Though I am new to Ubuntu i've came across this very same problem. Well... I had no idea what to do, thus I followed the instructions located here : [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)
... Still don't know how it works though  :mrgreen:  
If I were You... before trying anything from the link above, I'd repeal all the changes which You have done... I'm a newbie however, so my post just might be wrong... doing my best though :)


Best of luck

---

### Post by Perfect Storm on 2005-02-06
Take a look here: [http://ubuntuguide.org/index.html#jre](http://ubuntuguide.org/index.html#jre)




.:=The AI Dude=:.

---

### Post by audiored on 2005-02-06
[QUOTE=Artificial Intelligence]Take a look here: [http://ubuntuguide.org/index.html#jre](http://ubuntuguide.org/index.html#jre)




.:=The AI Dude=:.[/QUOTE]


thank you.. followed those directions and it worked.  =)  i'll have to include ubuntuguide.org in my future searches.

---

