---
title: "Bad key or directory name"
date: 2010-10-19
forum: General Help
---

### Post by krige on 2010-10-19
When I ran:

```
gconftool-2 -s '/apps/metacity/general/&#65279;button_layout' --type string ":minimize,maximize,close"
```

I got the following error message:

```
Error setting value: Bad key or directory name: "/apps/metacity/general/&#65279;button_layout": '\357' is not an ASCII character and thus isn't allowed in key names
```

By typing the message here in the forum I noticed there was a character between the '/' and the 'b'characters, which in the terminal was not visible! I deleted both I typed them again and that fixed it. Weird...

---

