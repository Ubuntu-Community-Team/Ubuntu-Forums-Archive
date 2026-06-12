---
title: "Open Chromium maximized via command-line"
date: 2011-05-02
forum: General Help
---

### Post by OldTimeyJunk on 2011-05-02
How can I open the Chromium web browser (chromium-browser) maximized via the command line. The geometry variable doesn't work!

---

### Post by tredegar on 2011-05-02
There doesn't seem to be a command line option to do this.

But chromium-browser store its last preferences in **~/.config/chromium/Default/preferences**

So you could open c-b, maximise it, close it.
Then 
```
cp ~/.config/chromium/Default/preferences ~/.config/chromium/Default/preferences-maximised
```

Then to open it full-screen from the terminal:
```
cp ~/.config/chromium/Default/preferences-maximised ~/.config/chromium/Default/preferences
chromium-browser
```

If you think this is too much of a hack, you could try using **sed** to edit **preferences** and then start c-b

---

