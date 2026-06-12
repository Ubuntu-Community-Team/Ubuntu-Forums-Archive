---
title: "pidgin &quot;paste as plain text&quot; set to default"
date: 2010-09-09
forum: General Help
---

### Post by ligaa9mm on 2010-09-09
Can anyone tell me where the file is that allows me to change CTRL+V in Pidgin from "paste" to "paste as plain text"? According to a changelog, it should be possible somewhere. I've seen about five different files referenced on various forums, but haven't been able to locate any of them on my computer.

Another thread mentioned appending the following bit of code to the **gtkrc** file:
```
bind "<ctrl>v" { "paste" ("text") }
```

I found the file in */user/share/themes/Default/gtk-2.0-key/*.When I open this file, it's empty. I added the code there, but it didn't work. The only other locations I found that file were in the other theme folders, but I use the default.

I'm running Ubuntu Netbook Remix v9.10, and the latest build of Pidgin (2.7.3).

Thanks for the help!

---

### Post by ligaa9mm on 2010-09-14
Never mind, I figured it out. It involved mixing and matching all of the different tutorials out there to find a combination of this-file-and-that-directory. Anyway, here we go...

1. Go to ***/usr/share/themes/Default/gtk-2.0-key/*** (replace Default with whatever theme it is that you use).
2. Open the **gtkrc** file in Gedit or whatever text editor you prefer (you may need to chmod or something to get permission to do so).
3. Add this code below the comments:

```
binding "my-bindings"
{
    bind "<ctrl>v" { "paste" ("text") }
}
widget "*pidgin_conv_entry" binding "my-bindings"
```

4. ???
5. Profit!

Took me forever and a day to figure out. Hope this helps others.

---

