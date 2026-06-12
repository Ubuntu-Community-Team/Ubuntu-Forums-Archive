---
title: "Is there a way to resize the Firefox URL bar?"
date: 2009-10-16
forum: General Help
---

### Post by Rytron on 2009-10-16
Hi.
Is there a way to resize the Firefox URL bar? Is there an option in about:config?

Below are examples of how I have Firefox setup. The first picture is my ideal setup, the second picture is what I get when I restart Firefox. The third picture is what I use for now (it has too much dead space though).

---

### Post by Vaphell on 2009-10-16
workaround is to set fixed width to the bookmark part, that way it won't get squashed.

[http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar](http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar)

---

### Post by aysiu on 2009-10-16
Just drag the toolbar down to where the icons are, and that should shrink it down automatically.

---

### Post by Rytron on 2009-10-16
> **Vaphell said:**
> workaround is to set fixed width to the bookmark part, that way it won't get squashed.

[http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar](http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar)

Hi. I got the message 'Http/1.1 Service Unavailable' when I click on the above link!

---

### Post by Rytron on 2009-10-17
> **aysiu said:**
> Just drag the toolbar down to where the icons are, and that should shrink it down automatically.

Hi. I tried that. No luck. The URL bar is automatically resized when 
I restart Firefox.

:confused:

---

### Post by Rytron on 2009-10-18
> **Vaphell said:**
> workaround is to set fixed width to the bookmark part, that way it won't get squashed.

[http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar](http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar)

Thank you Vaphell.

One of the comments to that link had this line:
```
#bookmarksBarContent .bookmark-item {visibility: visible !important;}
```

I added that to ~/.mozilla/firefox/xxxxxxx.default/chrome/userChrome.css

---

### Post by Rytron on 2009-10-18
Another method I used was adding these lines to ~/.mozilla/firefox/yyyyyy.default/chrome/userChrome.css

```
/* Urlbar width */
#urlbar-container {
min-width: 470px !important;
max-width: 470px !important;
}


/* Make the Firefox Search box flex wider */
#search-container, #searchbar {
/*#width: 100px !important;*/
min-width: 200px !important;
max-width: 200px !important;
}
```

Below is my slimline Firefox setup.

:popcorn:

---

