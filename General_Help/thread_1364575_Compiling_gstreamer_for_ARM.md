---
title: "Compiling gstreamer for ARM"
date: 2009-12-26
forum: General Help
---

### Post by shariefbe on 2009-12-26
Hello,
  I am trying to compile gstreamer for my ARM board. but when i compile it i am getting the following error
```

checking for arm-linux-gnu-pkg-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GST... no
configure: error: you need gstreamer development packages installed !
Configuration of glib library  has failed

```

---

### Post by shariefbe on 2009-12-27
i didnt have that "pkg-config" in that folder. see i have only one file in /usr/local/lib directory.```


iqbal@iqbal-laptop:/usr/local/lib$ ls
python2.6
iqbal@iqbal-laptop:/usr/local/lib$
```

 No i didnt install any gst-plugin-base. i dont know what are all the files needed to compile the gstreamer for ARM board. and what are the commands used to compile. what are all things i have to export. so pleae help me. so tell me what are all the files needed to compile for arm. now i have 
1)ARM cross compiler
2)gst-fsl-plugin-1.6.0
3)fsl-mm-codeclib-1.6.0

   THis are the steps i followed o compile the gstreamer
       1)i exported cross compiler path.
       2)then i tried to compile this gst-fsl-plugin-1.6.0
               by that time only i got this error. so please help me what to do?what are the things i have to do now? and what are the files needed?please help me

---

