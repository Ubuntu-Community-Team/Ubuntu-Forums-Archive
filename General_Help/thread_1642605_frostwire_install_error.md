---
title: "frostwire install error"
date: 2010-12-10
forum: General Help
---

### Post by kooley on 2010-12-10
hey all, i just recently downloaded the new frostwire and when i tried to install it i got this error msg back saying " Error: dependency is not satisfiable default-jre-headless" i was just wondering what that means and how do i fix it?

all help greatly appreciated thanx

---

### Post by JOHNNYG713 on 2010-12-10
To get Frostwire to run right I have had to do this, **Go to synaptic and install the apps in the attachments Below,**

Then set java as default!

 ```
sudo update-java-alternatives -l
```Which should return something like this

    java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
    java-6-sun 63 /usr/lib/jvm/java-6-sun

Now openjdk is set as default and we want to set it to suns version with this


    ```
sudo update-java-alternatives -s java-6-sun
```

Then install Frostwire! You should be good to go !

---

### Post by kooley on 2010-12-11
thanks for the suggestion but when i try to install the packages your recommended my synaptic cant find them, its probably because i have an old version of kubuntu (8.04, my computer is old :( ) is there any way to maybe get an older version of frostwire?

---

### Post by JOHNNYG713 on 2010-12-11
Hmm, Not sure try this ! [http://ubuntuforums.org/showthread.php?t=843882 ]("http://ubuntuforums.org/showthread.php?t=843882")
 I am not sure if this version of FW is still available, as hardy posts are dated and not kept up to date !

---

### Post by kooley on 2010-12-12
it worked :) thank you very much for the help

---

