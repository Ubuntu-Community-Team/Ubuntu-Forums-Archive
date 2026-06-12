---
title: "Create password field in Glade?"
date: 2009-11-29
forum: General Help
---

### Post by stinkinrich88 on 2009-11-29
Hello,

How can I get a text field to mask the input characters like a password field in Glade?

Thanks,

Rich

---

### Post by conehead77 on 2009-11-29
1. Open property editor (View -> Show property editor)
2. Make a "Text Entry" field
3. Select the Text Entry field
4. On the Widget tab there is an option "Text Visible": select No
5. Type some text in the text field to verify

---

### Post by stinkinrich88 on 2009-11-29
Ahh! Thanks, conehead77!

Though, I think we must be using different programs / versions. I'm using Glade 3.6.7 and I didn't have the "show property editor" button on my view menu. But the property editor was already docked in the main window. My "text visible" field on the widget tab was called "visible" and it was on the general tab. 

Do you think I'm using a rubbish version on Glade?

Thanks again!

---

### Post by conehead77 on 2009-11-29
I just checked and it's 2.12... So i guess you are better off with your version :D

But thanks for the hint, i think i will upgrade (although i don't make many GUIs) ;)

---

