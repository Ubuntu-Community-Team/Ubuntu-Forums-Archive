---
title: "How to install gnome themes on 11.10"
date: 2011-10-22
forum: General Help
---

### Post by _0R10N on 2011-10-22
Hi everybody, I installed 11.10 yesterday and I can't find where I can install new themes for gnome. Appearance window is completely new and there's no option to do that. I installed gnone-tweak-tools, but it doesn't have an option for installing themes, neither.

Any help? 

Kind regards!

---

### Post by CatKiller on 2011-10-22
At the moment, you don't. GTK 3 theming is still in a state of flux. The old themes are for GTK 2. It'll arrive after a while.

---

### Post by ShodanjoDM on 2011-10-22
If you're talking about gnome-shell, you can read here: [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Especially this part: 

Easily change GNOME Shell themes

```
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-user-theme
```

Extract and put your downloaded themes in ~/.themes folder in your home directory. If it doesn't exist, create one.

Hope that helps.

---

### Post by _0R10N on 2011-10-22
@ShodanjoDM thanks! I' using Unity, actually. I've googled a little and I found that themes for Unity have to be uncompressed under /usr/share/themes/. After doing so the themes should be available on gnome-tweak-tools, but it's not; so I'm wondering whether it's a problem of this theme I'm trying to install, or it's a Unitiy issue. I guess I'll give it another try to this approach with a different theme and see what happens.

I'll post later on this.

Thanks again!

Regards!

---

### Post by _0R10N on 2011-10-22
By the way, the theme is Moomex and I successfully installed it on 11.04 (without Unity)

---

### Post by 3rdalbum on 2011-10-22
> **_0R10N said:**
> @ShodanjoDM thanks! I' using Unity, actually. I've googled a little and I found that themes for Unity have to be uncompressed under /usr/share/themes/. After doing so the themes should be available on gnome-tweak-tools, but it's not

Ubuntu 11.04 uses Gnome 2 with GTK 2. Ubuntu 11.10 uses Gnome 3 with GTK 3. The themes from GTK 2 and GTK 3 are not interchangable, that's why Gnome Tweak Tool doesn't recognise the GTK 2 theme.

As an earlier poster said, there should be more themes available soon, but GTK 3 and Gnome 3 are still young yet. There *are* a few GTK 3 themes available - maybe search specifically for GTK 3 themes?

---

### Post by _0R10N on 2011-10-22
@3rdalbum excellent, many thanks!

---

### Post by magicjuice on 2011-10-22
Hi everyone.New on ubuntu and im tryind understand how it works.I tried to copy/paste my new desktop themes on the usr/share/theme file and i cant.I dont have the permition to do.
 What am i doing wrong ?

---

### Post by _0R10N on 2011-10-22
Hi @magicjuice!! you're doing nothing wrong. Regular users shouldn't have access to that folder (write / execute). So, if you're trying to write into that directory, you have to execute the cp command with sudo

```
sudo cp my_theme_folder /usr/share/themes/
```

Regards!

---

### Post by magicjuice on 2011-10-23
> **_0R10N said:**
> Hi @magicjuice!! you're doing nothing wrong. Regular users shouldn't have access to that folder (write / execute). So, if you're trying to write into that directory, you have to execute the cp command with sudo

```
sudo cp my_theme_folder /usr/share/themes/
```

Regards!

Thnx....Done.!!!:guitar:

---

### Post by _0R10N on 2011-10-23
Well, copying the theme folder into the directory previously mentioned did work. I first thought it didn't because everything still looked pretty much the same, but when I opened a window that wasn't maximized, I saw the window border corresponding to the theme I selected.

I guess that what I'm looking for is Unity Themes, since what I want to change is the whole look of my gnome session. On this, gtk2 themes doesn't seem to come in handy.

Regards!

---

