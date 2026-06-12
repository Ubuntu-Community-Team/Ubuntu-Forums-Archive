---
title: "Blocking access to website on public computer"
date: 2006-03-02
forum: General Help
---

### Post by 90Brougham350 on 2006-03-02
Is there any way I can type a few lines of code and block access to a website? I share a public computer with 22 other people, and we've all decided that myspace and facebook simply have to be blocked, because  they are being abused. Thanks for any help!

Brian

---

### Post by 5-HT on 2006-03-02
Hi Brian,

What about placing entries for those sites in /etc/hosts pointing to the localhost?

Just append something like:

```
 127.0.0.1 <site_you_want_to_block_goes_here> 
```

So for example, this should direct any querries of [www.ubuntuforums.org](www.ubuntuforums.org) to point to the computer itself and prevent anyone from viewing the site:

```
 127.0.0.1 www.ubuntuforums.org 
```

If you have a browser open while doing this, it may need a restart before reflecting the changes.

Be careful not to mess with anything already in the file though, it's best to back it up before making any changes.

Hope this helps

---

