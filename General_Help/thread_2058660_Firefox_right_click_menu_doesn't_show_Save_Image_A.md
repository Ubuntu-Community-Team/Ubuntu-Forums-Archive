---
title: "Firefox right click menu doesn't show Save Image As."
date: 2012-09-16
forum: General Help
---

### Post by MrWestwood on 2012-09-16
I've only just noticed this as I don't use it often. When I right click on an image in Firefox, as if to save the image, the option isn't there. As an example, with previous versions. I could do a Google image search and simply right click on any thumbnail and select Save Image as or View Image. These options are now no longer there.

Any ideas?

---

### Post by cwsnyder on 2012-09-16
It is more likely that the particular image you are viewing is set up to block that function in browsers than that the functionality has been removed from your Firefox.  I certainly have run into those image problems, and Firefox is working fine for me on unblocked images.  Save Image As . . also doesn't work if the image is a Flash video image, which may _look_ as if it is a still image.

---

### Post by MrWestwood on 2012-09-16
> **cwsnyder said:**
> It is more likely that the particular image you are viewing is set up to block that function in browsers than that the functionality has been removed from your Firefox.  I certainly have run into those image problems, and Firefox is working fine for me on unblocked images.  Save Image As . . also doesn't work if the image is a Flash video image, which may _look_ as if it is a still image.

I thought that at first but it does it with every image. I have tested it on other machines with the same site and I get the option, just not on my build. I also get some strange right click copy/paste issues.  If I highlight text and right click, it just unhighlights the text and then there's no option obviously. Also I get a similar thing with the spell checker. Firefox will highlight the text as having a spelling error but when I right click, there's no option to correct the word.

---

### Post by vasa1 on 2012-09-16
> **MrWestwood said:**
> I've only just noticed this as I don't use it often. When I right click on an image in Firefox, as if to save the image, the option isn't there. As an example, with previous versions. **I could do a Google image search** and simply right click on any thumbnail and select Save Image as or View Image. These options are now no longer there.

Any ideas?
Could you put up a screen grab of the right-context menu?
And is this issue only when you view Google Image search results?

---

### Post by vasa1 on 2012-09-16
This is what I see using Firefox 16. Can you try safe mode? Perhaps an extension is to blame?

---

### Post by MrWestwood on 2012-09-16
Sorry for the quality. I can't do a screen grab with right click menu open.

[[IMG]http://i.imgur.com/CpTvi.jpg[/IMG]](http://imgur.com/CpTvi)

[[IMG]http://i.imgur.com/BDVLW.jpg[/IMG]](http://imgur.com/BDVLW)

---

### Post by MrWestwood on 2012-09-16
> **vasa1 said:**
> This is what I see using Firefox 16. Can you try safe mode? Perhaps an extension is to blame?

I have found it. It was an addon called [multilink ]("https://addons.mozilla.org/en-US/firefox/addon/multi-links/"). I feel like such a tool. Two recent problems I've had with 12.04 have been related to software I've downloaded. 

Thanks for the ideas guys. I really need to pay more attention lately.

---

### Post by vasa1 on 2012-09-16
> **MrWestwood said:**
> ... I can't do a screen grab with right click menu open.

Yes, you can :) without installing additional software.

Instead of trying with plain print screen, you try this.
Let's say you have your browser open and you want to take a snap-shot of the menu you get on right-click. Obviously, that menu disappears as soon as you press print screen.
While having your browser open, also open a terminal (Ctrl+Alt+T), and, assuming you have a regular install, you should have a program called **gnome-screenshot**.
Type **gnome-screenshot -i** at the prompt. You'll get a box that let's you select a **delay**. For the first time, set a delay of 5 or more seconds. Once you get familiar with things you can reduce it.
Then, click **take screenshot**.
Now, click back on your browser window. Right-click wherever you need to in order to display the context menu **and wait**.
When the delay is complete, the screenshot will be taken without intervention by you. You'll get a window that lets you set a name and destination. Done.


This is assuming you are using regular Ubuntu. If your using a community distro such as Kubuntu or Lubuntu or Xubuntu, the name of the program will be different.

---

### Post by MrWestwood on 2012-09-16
Thanks for the tip.

---

