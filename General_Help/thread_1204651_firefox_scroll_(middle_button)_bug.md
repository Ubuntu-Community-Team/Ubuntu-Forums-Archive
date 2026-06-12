---
title: "firefox scroll (middle button) bug"
date: 2009-07-05
forum: General Help
---

### Post by opensrcFTW on 2009-07-05
I'm currently using Linux Mint (a derivative of ubuntu as I understand it?? hence why I posted here, though correct me if I am wrong).

I'm running FireFox 3.0.11

When I am on a page in FF, and I click the middle mouse button (the scroll button) to autoscroll up and down like what would happen in windows, instead it does something which I do not understand. Sometimes it closes tabs, and other times I am met with a dialogue box which says "The URL is not valid and cannot be loaded"

What is this and how do i fix it?

Regards

---

### Post by DeMus on 2009-07-05
> **opensrcFTW said:**
> I'm currently using Linux Mint (a derivative of ubuntu as I understand it?? hence why I posted here, though correct me if I am wrong).

I'm running FireFox 3.0.11

When I am on a page in FF, and I click the middle mouse button (the scroll button) to autoscroll up and down like what would happen in windows, instead it does something which I do not understand. Sometimes it closes tabs, and other times I am met with a dialogue box which says "The URL is not valid and cannot be loaded"

What is this and how do i fix it?

Regards


In Edit > Preferences, tab "Tab" you can set the way you want FF handle new pages. Should they be in the same Tab, a new TAB or even in a new Window.
I have set it to a new Tab. Look at the first picture.
On the last page I set the preferences like in the second picture.
Now when I click with the middle mouse button on a link, a new Tab is opened with the new page.
When i click with the middle mouse button next to a link a double sided arrow appears and I can drag the mouse and the page scrolls.

I understand this is not the case in your system? This is what it should be. Try these settings first please and see what happens.

---

### Post by Giant Speck on 2009-07-05
> **opensrcFTW said:**
> Sometimes it closes tabs, and other times I am met with a dialogue box which says "The URL is not valid and cannot be loaded"

Are you clicking in the actual webpage itself when you are trying to scroll?  Because in Firefox, middle-clicking on a tab closes it and middle-clicking on a link opens it in a new tab.

---

### Post by DeMus on 2009-07-05
> **opensrcFTW said:**
> I'm currently using Linux Mint (a derivative of ubuntu as I understand it?? hence why I posted here, though correct me if I am wrong).

I'm running FireFox 3.0.11

When I am on a page in FF, and I click the middle mouse button (the scroll button) to autoscroll up and down like what would happen in windows, instead it does something which I do not understand. Sometimes it closes tabs, and other times I am met with a dialogue box which says "The URL is not valid and cannot be loaded"

What is this and how do i fix it?

Regards

One more things where you can look:
Open a new window or Tab and as Url type About:config
When doing this for the first time you get a warning. Read it and accept it.
Now you get a page with all settings, on top of them is a filter (empty white field)
Type middle and now only those items with the word middle in it show up.
look at my attached picture and change the settings as I did.
You can do that by double clicking a line, the value changes when you do that.

---

### Post by opensrcFTW on 2009-07-05
> **DeMus said:**
> One more things where you can look:
Open a new window or Tab and as Url type About:config
When doing this for the first time you get a warning. Read it and accept it.
Now you get a page with all settings, on top of them is a filter (empty white field)
Type middle and now only those items with the word middle in it show up.
look at my attached picture and change the settings as I did.
You can do that by double clicking a line, the value changes when you do that.

Ahhh thank you, I did not have autoscroll enabled.

Question though, why is it that autoscroll is not enabled by default in linux and it is in windows? Just a simple mistake or accident? Or is there a specific purpose?

Thanks again!!

Regards

---

### Post by CatKiller on 2009-07-05
> **opensrcFTW said:**
> why is it that autoscroll is not enabled by default in linux and it is in windows? Just a simple mistake or accident? Or is there a specific purpose?

I don't know for sure, but the default behaviour of the middle-mouse button under Linux is to paste the contents of the text buffer. It's possible that this setting isn't enabled by default under Linux to prevent any problems with this function.

---

### Post by opensrcFTW on 2009-07-06
> **CatKiller said:**
> I don't know for sure, but the default behaviour of the middle-mouse button under Linux is to paste the contents of the text buffer. It's possible that this setting isn't enabled by default under Linux to prevent any problems with this function.


I thought about that too, but then I really got to thinking about it and I'm still not sure about that because I cannot foresee any conflicts arising from that (but I'm not a programmer lol so I would not know)

---

### Post by cristianrosa on 2009-10-28
I had a really anoying problem with this middle-click paste/load url functionality, because I am using a Synaptic touchpad and allows you to scroll using two fingers. If you scroll in small amounts, the system interpretets it as a middle-click instead, and pastes whatever is in the buffer (usually an old URL).
[This blog post]("http://gaarai.com/2009/09/09/fix-the-url-is-not-valid-and-cannot-be-loaded-in-firefox-on-ubuntu/") speaks about that.

---

