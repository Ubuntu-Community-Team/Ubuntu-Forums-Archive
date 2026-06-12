---
title: "Why Doesn't Nautilus Remember My Preferred Applications?"
date: 2010-05-19
forum: General Help
---

### Post by Skywa&#8224;cher on 2010-05-19
Hi all,

Something that's been bothering me for a while is the fact that Nautilus never seems to remember my preferred applications. For example, it is insistent on opening .EXE files with the Archive Manager, and not Wine. This is despite the fact that I have manually selected Wine from the "Open With" dialog box *and* ticked "Remember this application". Why is Nautilus ignoring me?!

---

### Post by snkiz on 2010-05-19
Linux usually doesn't care about file extensions, it reads a few bits to determine the mime type. As a matter of fact it will warn you if a file has the wrong extension. (You can test this by changing a png to txt then trying to open it.) Is your exe one of those zip installers? That being said if you manually set it then nautilus should listen.

---

### Post by Skywa&#8224;cher on 2010-05-25
Ah, I figured it out. Jeez, Nautilus doesn't half make it confusing to choose default apps. Seems you have to right-click on any file of the type you want to set the default app for, click Properties and then choose an app from the Open With tab. Doing it "the Windows way" (i.e. right-click > Open With > Other Application... > select an app and tick Remember This Application) has absolutely no effect whatsoever. Humph.

---

### Post by snkiz on 2010-05-25
> **Skywa†cher said:**
> Ah, I figured it out. Jeez, Nautilus doesn't half make it confusing to choose default apps. Seems you have to right-click on any file of the type you want to set the default app for, click Properties and then choose an app from the Open With tab. Doing it "the Windows way" (i.e. right-click > Open With > Other Application... > select an app and tick Remember This Application) has absolutely no effect whatsoever. Humph.

Sounds like a bug to me, you can file it here: [https://bugs.launchpad.net/ubuntu/+source/nautilus]("https://bugs.launchpad.net/ubuntu/+source/nautilus")
Glad you got it worked out :D

---

