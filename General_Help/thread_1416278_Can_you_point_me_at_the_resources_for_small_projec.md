---
title: "Can you point me at the resources for small project?"
date: 2010-02-25
forum: General Help
---

### Post by weavermount on 2010-02-25
Hello. I've been using ubuntu for 3 days now, and am really loving it. I though of a small project that I would like to do, but don't really know where to start

What I want to do have a key command that pops up a small window under my courser. In this window I have buttons for each of my workspaces and few apps. If you use blender you know the feel I'm going for. 

I'm looking to get under the hood a little, but am not sure where to start. Specifically
-How do I give an application awareness of workspaces, and the ability to switch the active one?
-How get at the data behind the applications menu, and then launch an application?
-What would be a good choice of code base?

If you can actually answer questions, great! Really I'm hoping for links to resources. I'm so new to this I don't even know where to start teaching myself

Thanks all!

---

### Post by smmalmansoori on 2010-02-25
> How do I give an application awareness of workspaces, and the ability to switch the active one?
There is an applet for a dock called AWN that switch between workspaces, you can inspect the source code to know how its done. Source is [here]("https://launchpad.net/awn-extras/+download")

> How get at the data behind the applications menu, and then launch an application?
Right click on Applications
Click Edit Menus
Choose the menu you want from the left
Choose the item on the right
Click properties, the command to call that application is found there

> What would be a good choice of code base?
Anything you're comfortable with would do.

---

### Post by weavermount on 2010-02-26
The AWN tip had exactly what I needed; thanks!

I just have figure out how to replicate the applications menu.

---

