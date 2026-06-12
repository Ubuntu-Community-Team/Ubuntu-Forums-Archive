---
title: "How do I create a transparent animation using GIMP?"
date: 2009-09-24
forum: General Help
---

### Post by Bible-Man on 2009-09-24
I've been searching the web for a while, and haven't been able to come up with anything much. Whenever I create an animation with a transparent background in GIMP, the previous layers are still in the background.

I've read that to fix this, you need to either change each layer's attributes to (replace), or when saving, choose the "one frame per layer" option, and click "use disposal entered above for all frames".

But what this does, is delete the previous layers, as seen here: [IMG]http://img41.imageshack.us/img41/7783/linklightning.gif[/IMG]

A little help, please?

Oh, and I apologize if the prefix is incorrect. I'm not really sure which one I was supposed to choose. 

Thanks.

Edit: Do I need to do something with the Layer Mask? It seems as though that might be the answer, but I haven't accomplished anything with it.

---

### Post by Bible-Man on 2009-09-25
*bump*

---

### Post by arizonalarry2 on 2009-09-26
> **Bible-Man said:**
> I've been searching the web for a while, and haven't been able to come up with anything much. Whenever I create an animation with a transparent background in GIMP, the previous layers are still in the background.

I've read that to fix this, you need to either change each layer's attributes to (replace), or when saving, choose the "one frame per layer" option, and click "use disposal entered above for all frames".

But what this does, is delete the previous layers, as seen here: [IMG]http://img41.imageshack.us/img41/7783/linklightning.gif[/IMG]

A little help, please?

Oh, and I apologize if the prefix is incorrect. I'm not really sure which one I was supposed to choose. 


Thanks.

Edit: Do I need to do something with the Layer Mask? It seems as though that might be the answer, but I haven't accomplished anything with it.


Try just adding "replace" into the layer attributes and skip the other things, that's all I ever had to do.

You can probably find more help at the Gimp Forum - [http://www.gimptalk.com/forum/](http://www.gimptalk.com/forum/)

---

### Post by akakingess on 2009-09-26
Or even some help from the Multimedia group within this ubuntu forum.

---

### Post by Bible-Man on 2009-09-28
OK, thanks. I'll ask on those forums. Yeah, whenever I add "replace", it deletes part of the past image.

Thanks again.

---

### Post by StuartN on 2009-09-28
> **Bible-Man said:**
> whenever I add "replace", it deletes part of the past image.

It looks to me like some parts of your animation are traditional replacement frames and other parts are additions. The easiest thing is replacement and every layer is a complete new image. If you want to do more finely crafted animations with multiple modes then there is a good tutorial at [http://www.imagemagick.org/Usage/anim_basics/](http://www.imagemagick.org/Usage/anim_basics/) for Imagemagick, which uses the same terminology as Gimp uses.

---

