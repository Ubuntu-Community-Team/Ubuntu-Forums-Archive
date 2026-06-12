---
title: "update manager grrrrr"
date: 2012-02-06
forum: General Help
---

### Post by jockyburns on 2012-02-06
Hoping someone can help . Every day, the update manager keeps popping up telling me that there are updates available. The updates it's telling me I need to download are .
Chromium Browser. 
Codecs for Chromium Browser
Codecs for Mozzilla Browser etc. 
I have Chrome set as my default browser and don't particularly want to load Chromium, nor any updates for Mozzilla. 
Up to now I just untick these updates. 
Is there a way to stop these updates appearing daily?

Cheers

---

### Post by WthIteh on 2012-02-06
If you change state of a package to "hold", you will not be prompted for updating it anymore.

You can see state of a package using:
```
dpkg --get-selections | grep packagename
```and change state of a package to 'hold' by
```
echo "packagename hold" | sudo dpkg --set-selections
```

---

### Post by jockyburns on 2012-02-07
Thanks for taking the time to reply, but, terminal commands mean nothing to me. I'll just keep on unticking these items for now. ;)

---

### Post by raja.genupula on 2012-02-07
[http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

---

### Post by jockyburns on 2012-02-08
Thanks for the link Raja. Genupula. all sorted . :D:D

---

