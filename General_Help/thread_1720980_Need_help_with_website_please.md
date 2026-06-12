---
title: "Need help with website please"
date: 2011-04-03
forum: General Help
---

### Post by Nick-S on 2011-04-03
Greetings friends
I need some help with my css and html page again.  Basically now it looks better but I have an  issue with images and links. I have images as links and when I click on the top left side of the page, the area is clickable, but its not suppose to be. I have attached some images as well as my page for more information. If you open my page and right click with your mouse and select all, you will see what I mean. Or if you click and hold an image will do the same. 
I validated my page and it seems better. 
I would strongly appreciate your help. 
Nick-S

ps: Am I posting in the right area?

---

### Post by blueridgedog on 2011-04-03
I would start with adding the end > to your body tags.  You have <body and </body.

---

### Post by Nick-S on 2011-04-03
Thank you blueridgedog > has been added to the body tags. However I still have the problem with linked images as explained above.
Help is strongly appreciated.

---

### Post by blueridgedog on 2011-04-04
When you hold you mouse over the area that links, what is the URL given in the browser (you can see it at the bottom)?

I can't reproduce it, but I don't have a server running at the moment.

---

### Post by mendhak on 2011-04-04
I think the problem is the CSS you're using. For example look at the images:

.img img {
    bottom: -150px;
    height: 85px;
    margin: 10px;
    padding: 20px;
    position: relative;
    right: -390px;
    width: 85px;
}

This is probably because you've got all your links in a single <div> but want it to go across.

So instead, you could use more DIVs inside the DIV.img to place those links.  Have a main container div (the DIV.img) and then you could float the images left within the DIV so that they stack and flow over to the next line.

---

### Post by Nick-S on 2011-04-04
> **mendhak said:**
> I think the problem is the CSS you're using. For example look at the images:

.img img {
    bottom: -150px;
    height: 85px;
    margin: 10px;
    padding: 20px;
    position: relative;
    right: -390px;
    width: 85px;
}

This is probably because you've got all your links in a single <div> but want it to go across.

So instead, you could use more DIVs inside the DIV.img to place those links.  Have a main container div (the DIV.img) and then you could float the images left within the DIV so that they stack and flow over to the next line.

Can you show me an example? I am confused, sorry.

---

### Post by Nick-S on 2011-04-04
Anyone?:(

---

### Post by Nick-S on 2011-04-05
Can someone help me please? :(

---

### Post by blueridgedog on 2011-04-05
What is the link you get when you mouse over the areas in question?

---

### Post by Nick-S on 2011-04-05
> **blueridgedog said:**
> What is the link you get when you mouse over the areas in question?

I get diabian.html, reactos.html, arch-linux.html and more. 

Basically The links should be where the images are, but they seem to be scattered.
The images are still working perfectly, but as I said the links are scattered on the left side of  the page (I have attached another image showing where the links are scattered)
About the image: black dots indicate clickable area and the grey dots indicate clickable when the pink list is removed. I am using Firefox 4, Google Chrome and Opera on Windows xp, 7 and Ubuntu 10.10 however ubuntu does not seem to render the page correctly. 

edit: I will correct the "ReactOS is not linux" as soon as this problem is fixed.

---

### Post by Nick-S on 2011-04-06
Can someone help me please? :sad:

---

### Post by Nick-S on 2011-04-07
Can someone please help me ?

---

### Post by Nick-S on 2011-04-08
bump

---

