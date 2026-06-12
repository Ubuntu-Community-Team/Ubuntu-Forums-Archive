---
title: "Is CAPTCHA available at all in CLI?"
date: 2009-10-22
forum: General Help
---

### Post by wesg on 2009-10-22
I'm working on browsing the internet on my server so that I can set it up as a downloading machine with little interaction. THe problem is that most websites now use the CAPTCHA image. 

Is it possible at all to use a browser to view images on the CLI? I have lynx and links2 but of course both only use text.

---

### Post by sisco311 on 2009-10-22
Just [change the bootup and console resolution]("http://ubuntuforums.org/showthread.php?t=258484") (framebuffer) and you should be able to run links2 in graphics mode:
```
links2 -g *URL*
```

[thread=882596]HOWTO: Ubuntu CLI versions & Framebuffer Programs[/thread]

---

