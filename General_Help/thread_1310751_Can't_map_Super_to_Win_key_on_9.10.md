---
title: "Can't map Super to Win key on 9.10"
date: 2009-11-02
forum: General Help
---

### Post by jpmaglutac on 2009-11-02
So I just did a fresh install of Karmic on my laptop (Aspire One) after using Jaunty for a while. I used to be able to use the Super key (win key) as a single shortcut to show the desktop. After installing Karmic, it seems the win key is defaulted as Mod4 key, meaning I have to use it together with another key, and not as a single shortcut key. 

I tried opening the layout options in Keyboard preferences, and it seems that the "Super is mapped to the Win-keys" option isn't even available as one of the choices. So how do I map the windows key to be detected as Super_L, instead of Mod4?

---

### Post by Aearenda on 2009-11-02
There are a couple of ways to fix this - see [this page]("http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html") for one solution.

---

### Post by jpmaglutac on 2009-11-02
That solution doesn't seem to be working for me =/ Thanks for the help though; any others?

---

### Post by wilee-nilee on 2009-11-02
If your using Ubuntu Tweak I think you can assign keys in it.

---

### Post by Aearenda on 2009-11-02
> **jpmaglutac said:**
> That solution doesn't seem to be working for me =/ Thanks for the help though; any others?

I just tried it on my netbook and it worked - you didn't accidentally stick a 'sudo' on the front did you (it mustn't have it)?

My Alt/Win key behaviour is set to 'default' in Keyboard layouts.

---

### Post by jpmaglutac on 2009-11-02
> **Aearenda said:**
> I just tried it on my netbook and it worked - you didn't accidentally stick a 'sudo' on the front did you (it mustn't have it)?

My Alt/Win key behaviour is set to 'default' in Keyboard layouts.

Naw I didn't :P

Well, technically it does work, but it doesn't do what I want xD When I press it, the application menu pops out, but I kinda want to use it to hide all windows and show the desktop

---

### Post by hanexar on 2009-11-02
Hi there, I found this fix:

- alt-f2 : gconf-editor 
- apps -> metacity -> global_keybinding and look for Show_Desktop
- right click and edit, change value to "Super_L" without the quote.
- Enjoy your Super L key doing what it does best!

---

### Post by Aearenda on 2009-11-02
> **jpmaglutac said:**
> Well, technically it does work, but it doesn't do what I want xD When I press it, the application menu pops out, but I kinda want to use it to hide all windows and show the desktop
Ah! Sorry, I misunderstood your original post. Hanexar has the right answer for you!

---

### Post by jpmaglutac on 2009-11-02
Oh thanks :D It worked :)

---

