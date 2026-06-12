---
title: "movie players"
date: 2010-07-10
forum: General Help
---

### Post by choochoousmc on 2010-07-10
Ubuntu 10.04lts   default player is totem movie player.
However, it does not provide a way to remove recently played media listings.

In the Ubuntu available software menu, which one(s) would you all recommend as a 
replacement that does allow removal of the recently played list.

---

### Post by flick on 2010-07-10
Totem will let you delete playlists in its sidebar. Click on/highlight what you want to get rid of, then click the big minus sign button in the lower right hand corner.

---

### Post by choochoousmc on 2010-07-10
playlists yes.
But not the recently played list.     two different subjects.
You play a movie and close the application.
Next time you open the application and select media, the last movie or movies is listed.
I want to be able to clear this list.

But thanks for responding

---

### Post by flick on 2010-07-10
Places > Recent Documents > Clear Recent Documents

---

### Post by Johnny B on 2010-07-10
you can disable the recently used documents with this:
```
rm ~/.recently-used.xbel && mkdir ~/.recently-used.xbel
```

---

### Post by choochoousmc on 2010-07-17
while back I posted a question on clearing the recently played list in totem.
Couple people responded and offered help.
But they either didn't understand or were in error.
I was not talking about playlists
I was talking about recently played items.

Here is the answer.
If you want to delete the recently played list in totem.
In Ubuntu  select PLACES > recent documents> clear.
apparently the writers of TOTEM elected to clear the list this way, rather than incorporate their own menu option in the player itself.

---

### Post by yetiman64 on 2010-07-17
> **choochoousmc said:**
> while back I posted a question on clearing the recently played list in totem.
Couple people responded and offered help.
But they either didn't understand or were in error.
I was not talking about playlists
I was talking about recently played items.

Here is the answer.
If you want to delete the recently played list in totem.
In Ubuntu  select PLACES > recent documents> clear.
apparently the writers of TOTEM elected to clear the list this way, rather than incorporate their own menu option in the player itself.

I think this is the thread (note post number #4 there)
Edit: <link removed as thread now merged - post #4 above now thread is merged>

I'll ask the mods to merge these 2 threads, cheers.

---

