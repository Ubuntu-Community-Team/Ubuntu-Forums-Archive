---
title: "How to disable Google Chrome Popup blocker on Ubuntu"
date: 2010-02-02
forum: General Help
---

### Post by LinuxTAd on 2010-02-02
Hello,

 I am interested in disabling the popup blocker in Google Chrome on Linux as you can do in windows, but am unable to locate the correct way to do so.

**For Windows the line to use in the shortcut is:**
```
"C:\Documents and Settings\Ali\Local Settings\Application Data\Google\Chrome\Application\chrome.exe" -disable-popup-blocking
```

[B]For Ubuntu I have tried the following, but it doe snot seem to work:
[/B]

```
/opt/google/chrome/google-chrome %U -disable-popup-blocking
```


I would appreciate any help in locating the correct line to use to prevent the popup blocker form loading in Chrome for Linux :)

Best regards,
LinuxTAd

---

### Post by giarca on 2010-02-02
I think it's a typo. After the command you pass the option with a single indent at first. Commonly must have double indent like --disable-popup-blocking.

---

### Post by LinuxTAd on 2010-02-07
Giarca, 

 Thank you for your reply, I appreciate it greatly!  :p

Best regards,
LinuxTAd

---

