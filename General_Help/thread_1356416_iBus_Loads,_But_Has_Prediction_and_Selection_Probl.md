---
title: "iBus Loads, But Has Prediction and Selection Problems"
date: 2009-12-16
forum: General Help
---

### Post by Andante on 2009-12-16
Hi everyone,

I have two issues with iBus.

First is that though it loads up with Chinese, there is no character prediction. If I type a multi-character phrase, it starts the selection process after each character, not the phrase. This makes it incredibly slow and tedious to type real sentences, to the point of unusable. (In Japanese the spacebar will not select Kanji--I can only type Hiragana. Proper Japanese support is not crucial, though, just something I thought might be related.)

Second, after selecting iBus from the Language Settings under administratio and restarting, I no longer see any iBus dialog on my system. If I hit ctrl+space (my hotkey) I can begin typing Chinese, but there's no visual notification that iBus is running and no way to change languages.

I can live with this, though--I can't live without typing Chinese.

I greatly appreciate any help I can get with this! I need to use Chinese frequently and ever since Karmic I've had to run Windows (can't get SCIM working anymore either--I'd be pleased if the solution were to get SCIM working, or some other program), which has its own set of problems.

Thanks!

---

### Post by Andante on 2009-12-16
Bump? I would love to fix this, or just get SCIM working again, since I need Chinese most everyday.

Thanks!

---

### Post by Irihapeti on 2009-12-16
It sounds to me as though you are using the pinyin method that comes as default with iBus, which is part of the m17n suite. It's a rather basic method with no prediction.

If that is the case, you need to install ibus-pinyin, which behaves much like scim-pinyin.

If you want to go back to using Scim, then it can be installed via synaptic. Also install scim-bridge-client-gtk plus scim-pinyin at the same time - I'm assuming that this is the method you were using.

To select scim as your input method, go to System -> Administration -> Language Support and select scim-bridge as keyboard input method system. You'll then need to log out and in again.

You can leave iBus installed. Only one input method is active at any one time.

---

