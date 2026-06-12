---
title: "disable form auto-filling in Firefox (3.5)"
date: 2009-12-04
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-12-04
It's pretty weird but I can't locate this config. I definitely remember that windows firefox had this option in a very easy to find place. But where was it hidden to in linux firefox?

---

### Post by wojox on 2009-12-04
Type:

```
about:config
```

In address bar and search for:

```
browser.urlbar.maxRichResults
```

And set it to 0

---

### Post by Eugene_Bondarenko on 2009-12-04
Thanks, I already tried this and it seems to affect wrong place. It affects URL dropdown and I like that. What I hate are forms. So for example when you sign in somewhere and want to enter login in the login form, a dropdown appears and offers you logins you used before (including the ones where I made typo). I know that incorrect ones can be deleted, etc, but I simply hate this feature and want to remove it. :)

---

### Post by winotree on 2009-12-04
Is this what you're looking for in **about:config**?  ```
signon.autofillForms;true
```
Changing it to false would meet your needs?

EDIT - clarified comment...

---

### Post by Eugene_Bondarenko on 2009-12-04
For some reason it didn't work. However it gave me an idea to look for the configs that have "form" in name. The config that did the trick is
```

browser.formfill.enable=false;

```

---

