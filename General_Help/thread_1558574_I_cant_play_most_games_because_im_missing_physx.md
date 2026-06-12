---
title: "I cant play most games because im missing physx"
date: 2010-08-22
forum: General Help
---

### Post by KEE on 2010-08-22
ok, need help with putting this together.[http://www.nvidia.co.uk/object/freebsd-x86-256.35-driver-uk.html]("http://www.nvidia.co.uk/object/freebsd-x86-256.35-driver-uk.html") i found a physx driver on nvidia site but how do I it? im kinda hoping this will solve my problem [IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-6.png[/IMG]

---

### Post by Frogs Hair on 2010-08-22
This software normally comes with your graphics card install disk  if supported. I have no idea weather it will work with wine.    [http://www.nvidia.com/object/physx-9.10.0513-driver.html](http://www.nvidia.com/object/physx-9.10.0513-driver.html)

---

### Post by Morrad on 2010-08-22
> **Frogs Hair said:**
> I have no idea weather it will work with wine.

The winetricks packages allows you to install physx.  In my (limitted, tried for one game) experience, it made the game a bit more unstable, but I was trying to run a more graphics intensive game on a very low end physx enabled card.

```
winetricks physx
```

---

