---
title: "Can't change default applications"
date: 2011-10-18
forum: General Help
---

### Post by mcmullen on 2011-10-18
Hi, I'm trying to change my default music player to guayadeque but on system info I cant select any other option other then the already selected VLC.

Thanks

---

### Post by mc4man on 2011-10-18
Im going to assume your on 11.10, it's probably the way guayadeque is installing itself that's keeping it out of the list.

There's very little to be gained, mainly if you want it to show up in the Dash's "Listen to Music" icon.

It that's what you want pretty simple - 

For starters go ahead & switch to vlc in system info > Default Applications > Music, then I know the file & line will be present.

After that in a terminal
 ```
gedit  ~/.local/share/applications/mimeapps.list
```
In the [Default Applications] sections you'll see this line

audio/x-vorbis+ogg=vlc.desktop

replace vlc.desktop with guayadeque.desktop so the line will look like this - 

audio/x-vorbis+ogg=guayadeque.desktop

Then save & close gedit & do a **restart,** (not a log out/in
you'll then have guayadequ in dash - screen
For ref. screen 2 shows the list in gedit

---

### Post by Meelad on 2011-10-18
[]("http://www.ubuntuforums.org/search.php?searchid=83557697")[U][http://ubuntuforums.org/showthread.php?t=1863257](http://ubuntuforums.org/showthread.php?t=1863257)

[/U] Problem #3.

---

### Post by mc4man on 2011-10-18
> **Meelad said:**
> []("http://www.ubuntuforums.org/search.php?searchid=83557697")[U][http://ubuntuforums.org/showthread.php?t=1863257](http://ubuntuforums.org/showthread.php?t=1863257)

[/U] Problem #3.
again i'm going to say that I think that is a very poor idea, though if people want to do so then fine, just my opinion..

---

### Post by Meelad on 2011-10-19
> **mc4man said:**
> again **i'm going to say that I think that is a very poor idea**, though if people want to do so then fine, just my opinion..

Do you mean the idea to change the default app, or the way I suggested to do it??

---

