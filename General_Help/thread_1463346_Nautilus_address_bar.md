---
title: "Nautilus address bar"
date: 2010-04-26
forum: General Help
---

### Post by KayakJim on 2010-04-26
In 8.10 and 9.04 while in Nautilus I used to have an address bar where I could type in the directory I wanted to go, similar to the address bar for URLs in a web browser.

I'm currently running 10.4 RC and am unable to find anything similar. All I now have are a series of clickable boxes with each directories' name.

Any idea how I can get the address box back?

---

### Post by Cygnia on 2010-04-26
Just press Ctrl-L and a text entry field appears, in place of the breadcrumb boxes.

---

### Post by KayakJim on 2010-04-26
> **Cygnia said:**
> Just press Ctrl-L and a text entry field appears, in place of the breadcrumb boxes.

Yes, that is exactly what I wanted.

How do I make that the default instead of having to CTRL-L every time I open Nautilus?

---

### Post by KayakJim on 2010-04-26
> **KayakJim said:**
> How do I make that the default instead of having to CTRL-L every time I open Nautilus?

Found the answer for anyone else that wants to know:
[https://help.ubuntu.com/community/RestoreNautilusLocationBar]("https://help.ubuntu.com/community/RestoreNautilusLocationBar")

---

### Post by Cygnia on 2010-04-26
You might be able to use the following link from the Ubuntu Help Pages, on the other hand it may be outdated for Lucid. Try at your own risk:

[https://help.ubuntu.com/community/RestoreNautilusLocationBar](https://help.ubuntu.com/community/RestoreNautilusLocationBar)

As for how I found it, I just instinctively associated file browser with web browser and that they might work the same, and ended up getting lucky.

---

### Post by Cygnia on 2010-04-26
Hey, no fair, you beat me to my own answer!  Good job.

---

### Post by keypox on 2010-05-24
Its great that control -L does it but, didnt it use be a double click in that region and it went from candy bar to address?  I like taht functionality the best.

---

### Post by keypox on 2010-05-24
Its great that control -L does it but, didnt it use be a double click in that region and it went from candy bar to address?  I like taht functionality the best.

---

### Post by Beanmonster on 2010-05-25
I agree, the button to toggle between text and buttons should have stayed....

Why reduce the functionality of a new release????

After using 10.04 for a few weeks I have to say that I am rather disappointed. 
Nvidia issues, Empathy issues, simple things like the titlebar buttons being moved to the top left etc.

[B]
[Idea #24931: Bring back "Show path" button in Nautilus]("http://brainstorm.ubuntu.com/idea/24931")    [/B]posted at brainstorm

---

### Post by Rowen91 on 2010-06-21
YESSS!!!! No more annoying buttons, :3 I love the text field because it's a hell of a lot faster to navigate by typing the directory if you know it.

---

### Post by no_angst on 2010-12-27
Agreed, please bring this back as the default.  Here's a one-liner to set it.

```
gconftool -t bool -s /apps/nautilus/preferences/always_use_location_entry true
```

---

### Post by kaiwi on 2011-11-18
> **no_angst said:**
> Agreed, please bring this back as the default.  Here's a one-liner to set it.

```
gconftool -t bool -s /apps/nautilus/preferences/always_use_location_entry true
```

Thank you for this one-liner! For me it worked.

Nautilus should make it easier to set such fundamental options.

---

