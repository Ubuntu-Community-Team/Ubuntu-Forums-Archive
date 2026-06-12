---
title: "Java installation problems"
date: 2009-11-19
forum: General Help
---

### Post by Baasha on 2009-11-19
I am using Ubuntu 64 bit 9.10 with the 64 bit version of Firefox.  I have successfully followed the instructions given here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

until I get to step 14 (on the right side of page) where the command is:

ln -s /opt/java/64/jre1.6.0_17/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

and then I get the following error:

ln: accessing `/home/bob/.mozilla/plugins/': Not a directory

Does anyone know what the problem is?  I notice that in the 64 bit version of FF "plugins" is not a seperate folder but is a file in the ~/.mozilla directory, if that makes a difference.  I tried leaving the final "/" off the link command but that didn't work either?  Suggestions?

---

### Post by mechro on 2009-11-19
Did you do - **mkdir ~/.mozilla/plugins** - in step 11?

---

### Post by scouser73 on 2009-11-19
> Did you do - mkdir ~/.mozilla/plugins - in step 11?

+1 for **mkdir ~/.mozilla/plugins**

---

### Post by Baasha on 2009-11-19
Yes, I did the mkdir command and it told me it already existed.  In the meantime, I discovered there is another plugins folder: ~/.mozilla/firefox/plugins

I am not sure I understand why there is a shared plugin library file in /.mozilla and then another folder in /.mozilla/firefox.  I changed the command to put the link in /.mozilla/firefox and it didn't complain.  Then I went to the Java site given in the directions to check what version I had (to confirm the installation) but that site said I needed a java plugin before I could check to see if I had a java plugin.  I didn't acccept their offer to install because I wasn't sure I wasn't going to get a 32 bit plugin.  If I check in firefox with about:plugins java is not listed.

---

### Post by mechro on 2009-11-19
If you put "plugins" in /.mozilla/firefox then I guess this...

```
ln -s /opt/java/64/jre1.6.0_17/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

should be this...

```
ln -s /opt/java/64/jre1.6.0_17/lib/amd64/libnpjp2.so ~/.mozilla/firefox/plugins/
```

---

