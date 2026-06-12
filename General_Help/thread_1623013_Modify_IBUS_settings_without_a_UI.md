---
title: "Modify IBUS settings without a UI"
date: 2010-11-16
forum: General Help
---

### Post by awp2513_ on 2010-11-16
Hi,

I have a system running Ubuntu 10.4 Netbook Remix in kiosk mode. Users have access to a single custom application, and in it they may choose to change its language from English to one of several others, including Chinese, Japanese, and Korean. 

I'm using IBUS as the IME, and I am able to provide several input methods for each of these three languages. However, I would like to be able to only provide the appropriate language support. If the user selects Chinese as his language, I would like to only provide Chinese input methods, and not the Korean or Japanese ones. What's more, I do not want a Chinese user to have to cycle through Japanese and Korean options just to get to his.

Because the system is in kiosk mode, I need to change the IBUS settings behind the scenes somehow, but I've been unable to find a settings file that I can modify manually, without going through the UI (which is not really an option in this case).

Does IBUS have a settings file I can manipulate or replace? I've looked all over, and even done diffs on directories after changing a setting to see if there were any differences. I haven't found any.

One alternative I can think of would be to have a separate user for each language (English, Chinese, Japanese, and Korean). Realistically, users will only change the language of the system once, so restarting is not horrible. When the user changes the language, I would configure the system to auto-login to the appropriate account and restart the system. While this might work, it's not very clean.

Thanks in advance,

awp2513_

---

### Post by awp2513_ on 2010-11-18
I found the answer. IBUS stores its settings in the registry. run gconf-editor and navigate to desktop/ibus/general. From here, the "preload_engines" key can be modified to contain the values you want.

---

