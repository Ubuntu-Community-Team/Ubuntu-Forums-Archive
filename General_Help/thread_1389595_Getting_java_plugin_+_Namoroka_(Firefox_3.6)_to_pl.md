---
title: "Getting java plugin + Namoroka (Firefox 3.6) to play"
date: 2010-01-24
forum: General Help
---

### Post by bwhite82 on 2010-01-24
Thus far I have had no luck. I have installed Namoroka from the ppa repo and got flash working nicely but java is another matter. I followed instructions to install the jre manually but no matter what I do it will not display in FF's "about:plugins".

I have to ask if Namoroka is using the default folder: /home/username/.mozilla/plugins/? Because that is where I created the symlink to the java plugin. Any help at all would be appreciated. And YES, I have tried the plugin from Synaptic to no avail.

Thanks!

EDIT: Solved my own problem. I had to remove the erroneous symbolic link and instead create a new inside of: ~/.mozilla/plugins/ to the file "libnpjp2.so".

---

### Post by kitikri on 2010-01-26
> **Soldierboy said:**
> EDIT: Solved my own problem. I had to remove the erroneous symbolic link and instead create a new inside of: ~/.mozilla/plugins/ to the file "libnpjp2.so".

I don't know where you found this piece of info, but it worked!
Thanks!:D

---

### Post by scouser73 on 2010-01-26
Bookmark this for future reference: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by bwhite82 on 2010-01-27
> **kitikri said:**
> I don't know where you found this piece of info, but it worked!
Thanks!:D

Glad to help! :D

---

### Post by meekiat on 2010-02-15
Thanks a lot

---

### Post by GeekGirl1 on 2010-02-26
> **scouser73 said:**
> Bookmark this for future reference: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)That helped me as well. Thank you.

---

### Post by sqren on 2010-03-05
Thank you very much! The symlink did the job!
For the less tech-savvy, this was what I wrote in terminal:

```
ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugins/libnpjp2.so
```You might have to edit the sourcepath (/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/), to you own settings.

---

### Post by kamatschka on 2010-04-16
Thnak you... this helped me getting Java working on Namoroka... Thanks again.. :guitar:

---

### Post by jonerich on 2010-04-27
> **scouser73 said:**
> bookmark this for future reference: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)



thanks mate worked like a charm:ks :ks :ks :ks :ks

---

