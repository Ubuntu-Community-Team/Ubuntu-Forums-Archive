---
title: "Veetle HD for Chromium"
date: 2012-09-08
forum: General Help
---

### Post by PremiumG on 2012-09-08
I am a Linux noob (OH GOD, WHAT DO I DO IN TERMINAL!?)...

Anyway, I am running the latest version of Lubuntu 64-bit, and I cannot watch HD streaming videos from Veetle. Sure, SD works just fine, but I want to watch in HD. 

What do I have to do to make this possible? Remember, im a noob.

---

### Post by PremiumG on 2012-09-08
btw, the installation instructions that their website offers do not work. Just says it cant open the file.

---

### Post by marinara on 2012-09-09
works fine in firefox here

---

### Post by PremiumG on 2012-09-09
What about for Chromium? Firefox seems to use more resources than Chromium, and somehow is much slower considering that.

---

### Post by tartalo on 2012-09-09
> **PremiumG said:**
> Firefox seems to use more resources than Chromium, and somehow is much slower considering that.

Did you actually measure times?
[http://www.unixmen.com/chrome-vs-firefox-for-ubuntu/](http://www.unixmen.com/chrome-vs-firefox-for-ubuntu/)

---

### Post by PremiumG on 2012-09-09
Doesnt matter, I am minimalist and pro-vanilla...

Anyway, let's stay on track... **HOW DO I GET VEETLE HD TO WORK IN CHROMIUM ON THE LATEST LUBUNTU stable 64-BIT?**

---

### Post by cariboo on 2012-09-09
Make sure you are in the directory the you downloaded the file to, if you are using Chromium, it's probably the Download directory. Open a terminal and type the following commands:

```
cd Downloads
```

Now make sure veetle is in the directory:

```
ls -la *veetle*
```

once you have made sure the file is in the directory, type the following:

```
./sh veetle-0.9.17-linux-install.sh
```

---

### Post by PremiumG on 2012-09-09
> **PremiumG said:**
> btw, the installation instructions that their website offers do not work. Just says it cant open the file.

As previously stated... the directions that you mentioned are not working. Sorry for the confusion.

---

### Post by cariboo on 2012-09-09
Where did you download the file to? As you have to be in the same directory, or add the path to the correct directory in order to run the script. In my commands note the ***./*** this needs to be added to the command, if you are in the same directory as where the script is located.

---

### Post by PremiumG on 2012-09-10
I downloaded the file to many places in my efforts to run it properly. I have, many times, installed the script through terminal, but still... when I go to Veetle, in Chromium, it does not allow the HD version to play. It insists that I install the plugin, as if I had never done so in the first place.

---

### Post by PremiumG on 2012-09-20
Bumpola

---

