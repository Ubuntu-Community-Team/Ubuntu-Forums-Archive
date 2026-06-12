---
title: "Jamendo doesnt load in Rhythmbox"
date: 2010-03-09
forum: General Help
---

### Post by arnab_das on 2010-03-09
Jamendo fails to load its catalogue whenit is launched in Rhythmbox. Even if it loads the catalogue, its not possible to play anything. Magnatune though works perfectly.

Any workarounds/solutions?

---

### Post by 2Karl on 2010-03-12
I had a similar issue. The Jamendo catalogue loads, but any attempt to play anything is met with failure. However, it can be fixed as follows:

Edit the file /usr/lib/rhythmbox/plugins/jamendo/JamendoSaxHandler.py with your favourite text editor (you'll probably need to use sudo)

On line 29, change "ogg2" to "mp31" so that the line reads:

```

stream_url = "http://api.jamendo.com/get2/stream/track/redirect/?id=%s&streamencoding=mp31"
```

Save and exit.

Restart Rhythmbox and you should be rocking and rolling.

---

### Post by arnab_das on 2010-03-12
thanks.

mine was already selected as mp3 as i found out.

but today jamendo has suddenly started working! although i didnt even change a line of that script :)

---

### Post by 2Karl on 2010-03-13
I think the ogg / mp3 selector on the plugin itself was a little buggy, ie not always selecting the format you had thought you selected. Now that everything's hardcoded on mine it seems fine ;)

---

