---
title: "Chromium Enable Plugins Trouble"
date: 2009-08-24
forum: General Help
---

### Post by Soapy.Illusions on 2009-08-24
I just installed the latest version of Chromium, and it works fine, except that plugins are not enabled so flash doesn't work.

So I made a new item in my menu which is 

chromium-browser --enable-plugins

Although when I set that to my default browser it constantly says it is not the default one because it is setting the default one to be simply

chromium-browser

Now I don't mind constantly ignoring those messages, but when I open a link it opens with the default browser

chromium-browser

and flash doesn't work

Any ideas to make the plugins always enable on the default version of chromium

---

### Post by DeMus on 2009-08-24
> **Soapy.Illusions said:**
> I just installed the latest version of Chromium, and it works fine, except that plugins are not enabled so flash doesn't work.

So I made a new item in my menu which is 

chromium-browser --enable-plugins

Although when I set that to my default browser it constantly says it is not the default one because it is setting the default one to be simply

chromium-browser

Now I don't mind constantly ignoring those messages, but when I open a link it opens with the default browser

chromium-browser

and flash doesn't work

Any ideas to make the plugins always enable on the default version of chromium

Since chromium is still in experimental phase plug-ins (like flash) don't work yet.
Be patient, it will come.

---

### Post by P4man on 2009-08-24
Yep. here is how:

```
gksudo gedit /etc/chromium-browser/default
```

change it like this:
```

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--enable-plugins"
```

---

### Post by DeMus on 2009-08-24
> **P4man said:**
> Yep. here is how:

```
gksudo gedit /etc/chromium-browser/default
```

change it like this:
```

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--enable-plugins"
```

I stand corrected. It actually works. Wow.

---

