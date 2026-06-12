---
title: "Ubuntu 11.10 unusual panel?"
date: 2011-10-16
forum: General Help
---

### Post by Derekisamazing on 2011-10-16
I've upgraded to 11.10 recently and haven't really found issues other than this:

[[IMG]http://img38.imageshack.us/img38/5093/ubuntu1110.png[/IMG]]("http://imageshack.us/photo/my-images/38/ubuntu1110.png/")

I don't believe my panel is supposed to appear like that; however that is how it came when I upgraded. How would I change this to something nicer?

Thanks.

---

### Post by ezramorris on 2011-10-16
> **Derekisamazing said:**
> I don't believe my panel is supposed to appear like that; however that is how it came when I upgraded. How would I change this to something nicer?

Click on the Dash home button, and launch Appearance. Make sure "Ambiance" is selected from the theme selection.

Hope this helps,
Ezra.

---

### Post by Derekisamazing on 2011-10-16
> **ezramorris said:**
> Click on the Dash home button, and launch Appearance. Make sure "Ambiance" is selected from the theme selection.

Hope this helps,
Ezra.

I appreciate the reply, Ezra.

When I launch my Appearance settings and check the drop-down box next to theme, two themes are displayed, "HighContrast" and "HighContrastInverse". 

[[IMG]http://img6.imageshack.us/img6/2690/themeju.png[/IMG]]("http://imageshack.us/photo/my-images/6/themeju.png/")

Perhaps I need to download the Ambiance theme?

---

### Post by Leaf on 2011-10-16
You can further customize the theme's appearance with the gnome-tweak-tool.  Change your window borders and such to you liking!
```

sudo apt-get install gnome-tweak-tool

```

---

### Post by ezramorris on 2011-10-16
> **Derekisamazing said:**
> Perhaps I need to download the Ambiance theme?

This is included in the light-themes package, of which ubuntu-desktop is dependent upon.

To make sure everything is installed as it should be, start Terminal, and type:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Then check in appearance settings to see if it appears. You may have to log out and in again for it to appear.

Ezra.

---

### Post by Derekisamazing on 2011-10-16
> **Leaf said:**
> You can further customize the theme's appearance with the gnome-tweak-tool.  Change your window borders and such to you liking!
```

sudo apt-get install gnome-tweak-tool

```

This was very useful, thanks.



> **ezramorris said:**
> This is included in the light-themes package, of which ubuntu-desktop is dependent upon.

To make sure everything is installed as it should be, start Terminal, and type:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```Then check in appearance  settings to see if it appears. You may have to log out and in again for  it to appear.

Ezra.

And this worked, thank you so much!

---

